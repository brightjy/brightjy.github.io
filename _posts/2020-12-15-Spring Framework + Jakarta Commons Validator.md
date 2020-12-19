---
layout: post
title: "Spring Framework + Jakarta Commons Validator"
date: '2020-12-15 15:00:00'
author: BBarkji
categories: java
tags: spring
cover:  "/assets/instacode.png"
---


# Spring Framework + Jakarta Commons Validator

여기서는 Jakarta Commons Validator를 Spring Framwork와 연동하여 사용하는 방법에 대해 설명한다.
Jakarta Commons Validator는 필수값, 각종 primitive type(int, long, float...), 최대-최소 길이, 이메일, 신용카드 번호 등의 값 체크를 할 수 있도록 Template이 제공된다.
이 Template은 Java 뿐만 아니라 Javascript로도 제공되어 client-side, server-side의 검증을 함께 할 수 있으며, Configuration과 에러메시지를 client-side, server-side 별로 따로 하지 않고 한 곳에서 같이 쓰는 관리상의 장점이 있다. 
Spring에서는 Spring Modules 프로젝트에서 연계 모듈을 제공한다. 



### 필요 라이브러리

* commons-validator : ver 1.4.0
* commons-beanutils : ver 1.8.3
* commons-digester : ver 1.8
* commons-logging : ver 1.1.2
* junit : ver 3.8.2
* spring-modules-validation.jar



### DefaultValidator, DefaultBeanValidator 설정

* DefaultValidatorFactory
프로퍼티 'validationConfigLocationsApache'에 정의된 validation rule을 기반으로 Commons Validator들의 인스턴스를 얻는다.

* DafaultBeanValidator
DefaultBeanValidator는 org.springframework.validation.Validator를 implements하고 있지만,
DefaultValidatorFactory가 가져온 Commons Validator의 인스턴스를 이용해 validation을 수행한다.Controller에 validation 수행할때 이 DefaultBeanValidator를 참조하면 된다.


### 빈 정의 파일에 ValidatorFactory, Validator, validator-rules.xml, validation.xml 파일 등록

```

<!-- Integration Apache Commons Validator by Spring Modules -->				
    <bean id="beanValidator" class="org.springmodules.validation.commons.DefaultBeanValidator">
	<property name="validatorFactory" ref="validatorFactory"/>
    </bean>
 
    <bean id="validatorFactory" class="org.springmodules.validation.commons.DefaultValidatorFactory">
	<property name="validationConfigLocations">
		<list>
                      <!-- validator-rules.xml, validator.xml의 위치-->
			<value>/WEB-INF/conf/validator-rules.xml</value>
			<value>/WEB-INF/conf/validator.xml</value>
		</list>
	</property>
    </bean>

```


### validator-rules.xml 설정

validator-rules.xml은 application에서 사용하는 모든 validation rule에 대해 정의하는 파일이다.
예)
```

<validator name="required"
	classname="org.springmodules.validation.commons.FieldChecks"
             method="validateRequired"
         	methodParams="java.lang.Object,
                       	          org.apache.commons.validator.ValidatorAction,
                                     org.apache.commons.validator.Field,
                                     org.springframework.validation.Errors"
             msg="errors.required">
         	<javascript>
		<![CDATA[
         			.....
           	 	]]>
         	</javascript>
</validator>

```

| 구분 | 내용 |
| : --- | : --- |
| name | validation rule (required, mask, integer, email...) |
| classname | vlidation check를 수행하는 클래스명 |
| method | validation check를 수행하는 클래스의 메소드명 |
| methodParams | validation check를 수행하는 클래스의 메소드의 파라미터 |
| msg | 에러 메시지 key |
| javascript | client-side validation을 위한 자바스크립트 코드 |




### Spring Modules 에서 제공하는 validation rule

(FiledCheck 클래스는 모두 org.springmodules.validation.commons.FieldChecks)

| name (validation rule) | 메소드 | 기능 |
| : --- | : --- | : --- |
| required | validateRequired | 필수값 체크 |
| minlength | validateMinLength | 최소 길이 체크 |
| maxlength | validateMaxLength | 최대 길이 체크 |
| mask | validateMask | 정규식 체크 |
| byte | validateByte | Byte형 체크 |
| short | validateShort | Short형 체크 |
| integer | validateInteger | Integer형 체크 | 
| long | validateLong | Long형 체크 |
| float | validateFloat | Float형 체크 |
| double | validateDouble | Double형 체크 |
| date | validateDate | Date형 체크 |
| range | validateRange | 범위 체크 |
| intRange | validateIntRange | int형 범위 체크 |
| floatRange | validateFloatRange | float형 범위 체크 |
| creditCard | validateCreditCard | 신용카드번호체크 |
| email | validateEmail | 이메일체크 | 



### validator.xml 설정

validator.xml은 validation rule과 validation할 Form을 매핑한다.
form name과 field property의 name-rule은 Server-side와 Client-side인 경우에 따라 다르다.


_**Server-side validation의 경우는,**_

form name 과 field property는 validation할 폼 클래스의 이름, 필드와 각각 매핑된다. (camel case)
e.g. 폼 클래스가 DepartmentForm 이면, departmentForm


_**Client-side의 경우는,**_

form name은 JSP에서 설정한 <validator:javascript formName="employee" .../> 태그의 formName과 매핑되고, field property는 각각의 폼 필드의 이름과 일치하면 된다.


_**따라서, Server-side, Client-side 둘 다 수행하려면,**_

JSP의 <validator:javascript formName="employee" .../> 태그의 formName은 폼 클래스의 이름이 되어야 하고, JSP의 폼필드들은 폼 클래스의 필드와 일치해야 한다. 


예)

```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE form-validation PUBLIC 
    "-//Apache Software Foundation//DTD Commons Validator Rules Configuration 1.1//EN" 
    "http://jakarta.apache.org/commons/dtds/validator_1_1.dtd">
 
<form-validation>
 
    <formset>
 
        <form name="employee">
        	<field property="name" depends="required">
        		<arg0 key="employee.name" />
		</field>
		<field property="age" depends="integer">
        		<arg0 key="employee.age" />
		</field>
		<field property="email" depends="required,email">
        		<arg0 key="employee.email" />
		</field>		
        </form>
 
    </formset>
 
</form-validation>

```