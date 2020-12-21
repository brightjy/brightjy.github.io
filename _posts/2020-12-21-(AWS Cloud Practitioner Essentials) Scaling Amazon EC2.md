---
layout: post
title: "(AWS Cloud Practitioner Essentials) Scaling Amazon EC2"
date: '2020-12-21 21:30:00'
author: BBarkji
categories: AWS
tags: AWS
cover:  "/assets/instacode.png"
---



# Scaling Amazon EC2   
            
           
            
### Scalability
* automatically respond to changing demand by scaling out or in.
* you pay for only the resources you use.
* don't have to worry about a lack of computing capacity to meet your customers' needs.
            
          
           
### Amazon EC2 Auto Scaling
* eanables you to automatically add or remove Amazon EC2 instances in response to changing application demand.
* By automatically scaling your instances in and out as needed, you are able to maintain a greater sense of application availability.        
* two approaches: dynamic scaling and predictive scaling.   
> 1. Dynamic scaling responds to changing demand. 
> 2. Predictive scaling automatically schedules the right number of Amazon EC2 instances based on predicted demand.            
           
            
               
### Example
By adding Amazon EC2 Auto Scaling to an application, you can add new instances to the application when necessary and terminate them when no longer needed.            

_When configuring the size of your Auto Scaling group_      
                
1. set the **minimum** number of Amazon EC2 instances at one.        
This means that at all times, there must be at least one Amazon EC2 instance running.        
The **minimum capacity** is the number of Amazon EC2 instances that launch immediately after you have created the Auto Scaling group.       
             
2. set the **desired capacity** at two Amazon EC2 instances              
> If you do not specify the desired number of Amazon EC2 instances in an Auto Scaling group, the desired capacity defaults to your minimum capacity.      
            
3. set in an Auto Scaling group is the **maximum capacity**   
   


