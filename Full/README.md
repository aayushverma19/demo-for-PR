# Fullstack Documentation

| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Internal Reviewer** |**Reviewer L0** |**Reviewer L1** |**Reviewer L2** |
|------------|---------------------------|-------------|----------------|-----|-------------|-------------|-------------|-------------|
| Aayush Verma|   18-02-2025             | v1          | Aayush Verma   |-02-2025    |  Komal Jaiswal | Akshit kapil | Taranddeep | Abhishek  Dubey|

## Table of Contents
1. [Introduction](#introduction)
2. [Overall Component Architecture Flow](#overall-component-architecture-flow)
   * [Frontend Flow](#frontend-flow)
   * [Backend Management](#backend-management)
      * [Employee API](#1-employee-api)
      * [The Salary API](#2-the-salary-api)
      * [The Attendance API](#3-the-attendance-api)
    * [Database Management](#database-management)

3. [User Flow](#user-flow)
5. [Conclusion](#conclusion)
6. [Contact Information](#contact-information)
7. [Refrences](#refrences)

## Introduction

Full Stack Development is the process of creating a complete web application that includes front-end, back-end, and database management. 

**Front-End**: This is what users see and interact with on the website. It focuses on the look and feel, making sure the site is easy to use and looks good.

**Back-End**: This is the behind-the-scenes part. It handles the server, the logic of the application, and ensures everything works correctly. It also manages security and data processing.

**Database Management**: This part is about storing and organizing all the data the application needs. It makes sure data can be easily accessed and managed.


## Overall Component Architecture Flow

### Frontend Flow

Front-end development focuses on the part of a web application that users see and interact with. It's all about designing how the app looks (user interface) and how it feels to use (user experience). Front-end developers use languages like HTML, CSS, and JavaScript to build this visual part of the website, making sure it's easy to use and works smoothly.

## Pre-Requisites
The frontend application have dependencies on other REST API of OT-Microservices.

![image](https://github.com/user-attachments/assets/c8e662c8-7983-49bf-b30a-959ebab5d6f7)


To run the application successfully, These things should be configured
For Refrence Links Below
* [Frontend POC]() 
* [Employee API]()
* [Attendance API]()
* [Salary API]()


### Backend Management

#### 1. Employee-API
The Employee REST API is a Go-based microservice that manages all employee-related transactions within the OT-Microservices stack. It is fully platform-independent, meaning it can run on any type of operating system or platform.

<img width="1294" alt="Screenshot 2025-02-18 at 6 00 50 PM" src="https://github.com/user-attachments/assets/03142fc4-65a8-45e9-8e47-b92ea993e5fd" />

Create this same as above.
Pre-Requisites
For running the application, we need following things configured:
For Refrence Links Below
* [Documentation]() 
* [Employee POC]() 
* [ScyllaDB]()
* [Redis]()

#### 2. The Salary API
The Salary API is a Java-based microservice that handles all salary-related transactions and records within the OT-Microservices stack. It is platform-independent, meaning it can run on various operating systems. However, to run this application, a Java Runtime Environment (JRE) is required.

<img width="1294" alt="Screenshot 2025-02-18 at 6 01 49 PM" src="https://github.com/user-attachments/assets/35508d17-3ddd-4a71-a6a0-44a1573cb2b3" />


We only need maven as build tool, but for running the application following things are required
For Refrence Link are below 
* [Documentation]()
* [Salary POC]()
* [ScyllaDB]()
* [Redis]()
* [Java]()

#### 3. The Attendance api
The Attendance REST API is a Python-based microservice that manages all attendance-related transactions within the OT-Microservices stack. This application is cross-platform, meaning it can run on different operating systems. The only requirement to run it is the Python runtime environment.


![image](https://github.com/user-attachments/assets/93a1d514-0ab6-4ae7-8a94-e47a914bf8a3)


To run the application successfully, we need these things configured

PostgresSQL as a primary database for storing all the attendance records
Redis as cache management middleware for storing all API response
Below Have Refrence Links in detail
* [Documentation]() 
* [Attendance POC]() 
* [PostgresSQL]()
* [Redis]()
* [Poetry]()
* [Liquibase]()

### Database Management

Database management is responsible for storing, accessing, and managing data for an application. It involves tasks such as creating databases, maintaining their performance, and optimizing them to ensure efficient data handling.
For Refrence Links Below
* [ScyllaDB]()
  
* [PostgresSQL]()
  
* [Redis]()

### User Flow

---

| **User Registration Flow** |                
|---------------|
| 1. User submits the registration form. |     
| 2. Frontend validates the input. |                                     
| 3. The request is sent to the backend. |                       
| 4. The backend processes the registration and stores the data in the database. |        
| 5. A response is sent back to the frontend. |                                      
---

| **User Login Flow** |                                                  
|---------------------|                                      
| 1. User submits the login form. |                                       
| 2. Frontend validates the input. |                                           
| 3. The request is sent to the backend. |                                     
| 4. The backend authenticates the user. |                                    
| 5. A response is sent back to the frontend with a token. |            
---

| **Data Processing Flow** |                                                                                        
|---------------------------|
| 1. Data is submitted from the frontend. |                                                               
| 2. The backend processes the data. |                                                                         
| 3. Data is validated and transformed. |                                                                
| 4. Processed data is stored in the database. |                                                           
| 5. Confirmation is sent back to the frontend. |      
                                                 
---
### Conclusion
This document gives a clear overview of full-stack development for the OT-MICROSERVICES project. It explains how the front end and back end work together and shares important practices for building strong and easy-to-maintain applications. 

## Contact Information

| **Name**    | **Email address**         |
|-------------|---------------------------|
| Aayush Verma | <aayush.verma@mygurukulam.co>   |

## References

| **Link**                                                                                                                     | **Description**                                    |
|-----------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|
| [API Repo Link](https://github.com/OT-MICROSERVICES) | APIs Documentation    |
