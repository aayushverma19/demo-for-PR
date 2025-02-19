<p align="center">
  <img src="./assets/logo.svg" alt="Logo" width="200">
</p>
# OT Microservices Full Stack Documentation
| **Author**            | **Created on** | **Version** | **Last updated by**       | **Last edited on** | **Reviewer**      |
|-----------------------|----------------|-------------|----------------------------|---------------------|-------------------|
| Aman Raj      | 17-02-2025       | Version 1 | Aman Raj         | 17-02-2025       | Siddharth Pawar    |
## Table Of Contents
1. [Introduction](#introduction)
2. [Prerequisites](#pre-requisites)
3. [Application Flow](#application-flow)
4. [User Flow](#user-flow)
5. [Full Stack Setup](#full-stack-setup)
6. [Contact Information](#contact-information)
7. [References](#references)
## Introduction
OT Microservice Application is a full-stack system designed to efficiently manage workforce operations. It includes dedicated APIs for employees, salaries, and attendance, ensuring smooth and accurate processing.
<br/>
### Key Technologies & Architecture:
:white_check_mark: **PostgreSQL –** A robust relational database at the core, ensuring structured data integrity.<br/>
:white_check_mark: **ScyllaDB –** A high-performance NoSQL database for managing large datasets with scalability.<br/>
:white_check_mark: **Redis –** An in-memory data store enhancing system responsiveness and agility.
With a microservices-driven approach, our application ensures scalability, flexibility, and seamless data management, making it a powerful and efficient solution for workforce operations.
## Pre-Requisites
Before starting the setup, carefully review the documentation and install all necessary dependencies. Following a step-by-step approach ensures a smooth and efficient setup of the OT Microservices Full Stack system.
### Applications
| **Application Name**           | **Port** | **Dependency**                | **Language**                                                                                                                                          | **Description**                                                                                       |
|--------------------------------|------------------|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| [attendance](https://github.com/Snaatak-Skyops/Documentation/blob/214f0e67b2e59776d47aa0604f672734baeb2e4c/OT%20MS%20understanding/Application/Attendance%20/README.md)     | 8081             | PostgreSQL                         | <img src="https://cdn.worldvectorlogo.com/logos/python-5.svg" height="32" width="32">                                                                 | Attendance is a microservice which is designed in Python to manage employee's attendance information. |
| [employee](https://github.com/Snaatak-Skyops/Documentation/blob/f790c42d498c3925339e28f7ed9c97ebec34b86e/OT%20MS%20Understanding/Application/Employee/Detailed%20Documentation/README.md)         | 8083             | ScyllaDb                 | <img src="https://cdn.worldvectorlogo.com/logos/gopher.svg" height="32" width="32">                                                                   | Employee microservice is also designed in Golang to manage employee's information.                    |
| [salary](https://github.com/Snaatak-Skyops/Documentation/blob/2c47921cb0fb386434232b2944d3ca1005463f11/OT%20MS%20Understanding/Application/Salary/POC/README.md)             | 8080             | ScyllaDb                 | <img src="https://cdn.worldvectorlogo.com/logos/java.svg" height="32" width="32">                                                                     | Salary is also a java based application which creates and manages employee's salary information.    |
| [frontend](https://github.com/Snaatak-Skyops/Documentation/blob/6627e81ec43478acef6e24dc1f163f87ab3eed46/OT%20MS%20Understanding/Application/Frontend/README.md)         | 3000             | attendance, employeee, salary | <img src="https://www.vectorlogo.zone/logos/reactjs/reactjs-icon.svg" height="32" width="32">                                                         | Frontend is written in ReactJS.                                     |
For further information, click on the application name.
## Databases
These applications are using two kinds of databases.
| **Application Name** | **Default Port** | **Dependency** | **Description**                                                                                               |
|----------------------|------------------|----------------|---------------------------------------------------------------------------------------------------------------|
| [PostgreSQL](https://github.com/Snaatak-Skyops/Documentation/blob/194ab91c7b41b9be08fac2b9c0e08558a6d85162/OT%20MS%20Understanding/Database/PostgreSQL/README.md) | 5432             | -              | PostgreSQL is being used as a structured database that employees' attendance information.  |
| [ScyllaDb](https://github.com/Snaatak-Skyops/Documentation/blob/7040e168531b00d50efa9eaad8403078f5ae9ae3/OT%20MS%20Understanding/Database/Scylla%20DB/Documentation/README.md)     | 9042             | -              | ScyllaDB is being used as a structured database that manages employees' information and salaries.    |
For further information, click on the DB.
## Middleware
These applications are using two kinds of databases.
| **Application Name** | **Default Port** | **Dependency** | **Description**                                                                                               |
|----------------------|------------------|----------------|---------------------------------------------------------------------------------------------------------------|
| [Redis](https://github.com/Snaatak-Skyops/Documentation/blob/4bae3694a33ecc1e7f443ed3b8685929745e9882/OT%20MS%20Understanding/Middleware/Redis/README.md) | 6379         | -              | Redis is being used as a caching system to optimize access to employees' attendance information.  |
For further information, click on the DB.
## Application-Flow
![alt text](<./assets/Screenshot 2025-02-18 at 12.05.16 PM.png>)
## User-FLow
### 1. User Requests Data from the Frontend
The frontend sends API requests to the respective backend service based on the type of request:
- /api/v1/employee → Employee API
- /api/v1/salary → Salary API
- /api/v1/attendance → Attendance API
### 2. Cache Lookup in Redis
- Each API first checks Redis for cached data to improve response time.
- If data is found in Redis (cache hit), the API returns the data immediately.
- If data is not found in Redis (cache miss), the API fetches data from the respective database.
### 3. Fetching Data from Databases (on Cache Miss)
If a cache miss occurs:
- Employee API queries ScyllaDB for employee data.
- Salary API queries ScyllaDB for salary details.
- Attendance API queries PostgreSQL for attendance records.
- The retrieved data is then stored in Redis to improve future request performance.
### 4. Response to Frontend
- The backend API sends the requested data to the frontend.
- The frontend displays the data to the user.
## Full Stack Setup
### Attendance API
Attendance API is a Python-based microservice designed to handle attendance-related transactions in the context of the OT-Microservices ecosystem. This microservice serves as a central component for managing attendance records and transactions, providing a set of RESTful APIs for integration with other services.
![alt text](<./assets/Screenshot 2025-02-18 at 12.56.58 PM.png>)
***
### Salary API
Salary API is a Java-based microservice which is responsible for all the salary-related transactions and records in OT-Microservices stack. The application is platform-independent and can be run on multiple operating systems. Java Runtime would be required to run this application.
![alt text](<./assets/Screenshot 2025-02-18 at 12.56.50 PM.png>)
### Employee API
Employee REST API is a golang based microservice which is responsible for all the employee related transactions in the OT-Microservices. This application is completely platform independent and can be run on any kind of platform.
![alt text](<./assets/Screenshot 2025-02-18 at 12.56.43 PM.png>)
### Frontend
Frontend Web is a REACTJS based application that is the primary user-interface for OT-Microservices stack.The app is designed for cross-platform fuctionality and requires only the presence of javascript runtime modules.The ReactJS based web framework facilitates complete web page based operations.
For setting up all the above services do follow this document.
[Full Stack Setup](https://github.com/Snaatak-Skyops/Documentation/blob/248bc065b0df7f0fcd3ce726ff8e5255232e765f/OT%20MS%20Understanding/Application/Full%20Stack/FullStackrun.md)
## Conclusion
The OT Microservices Full Stack Setup offers a modern and scalable architecture. It includes APIs for managing employees, processing salaries, and tracking attendance, ensuring accuracy in workforce processes.
Using reliable databases like PostgreSQL for structured data, ScyllaDB for large datasets, and Redis for fast data access, the system is built to handle growth and improve efficiency.
##  Contact Information
For any queries or further information, feel free to contact:
| **Name**  | **Email**                       |
|-----------------|-----------------------------------|
| Aman | aman.raj@mygurukulam.co |
---
##  References
| Source               | Description                |
| -------------------- | -------------------------- |
| [Frontend Documentation](https://github.com/Snaatak-Skyops/Documentation/blob/6627e81ec43478acef6e24dc1f163f87ab3eed46/OT%20MS%20Understanding/Application/Frontend/README.md)            | Frontend API Setup Documentation |
| [Attendence API Documentation](https://github.com/Snaatak-Skyops/Documentation/blob/214f0e67b2e59776d47aa0604f672734baeb2e4c/OT%20MS%20understanding/Application/Attendance%20/README.md)            | Attendence API Setup Documentation |
| [Employee API Documentation](https://github.com/Snaatak-Skyops/Documentation/blob/f790c42d498c3925339e28f7ed9c97ebec34b86e/OT%20MS%20Understanding/Application/Employee/Detailed%20Documentation/README.md)            | Employee API Setup Documentation |
| [Salary API Documentation](https://github.com/Snaatak-Skyops/Documentation/blob/2c47921cb0fb386434232b2944d3ca1005463f11/OT%20MS%20Understanding/Application/Salary/POC/README.md) | Salary API Setup Documentation |
| [PostgreSQL Documentation](https://github.com/Snaatak-Skyops/Documentation/blob/194ab91c7b41b9be08fac2b9c0e08558a6d85162/OT%20MS%20Understanding/Database/PostgreSQL/README.md) | PostgreSQL Setup Documentation |
| [Redis Documentation](https://github.com/Snaatak-Skyops/Documentation/blob/4bae3694a33ecc1e7f443ed3b8685929745e9882/OT%20MS%20Understanding/Middleware/Redis/README.md) | Redis Setup Documentation |
| [ScyllaDB Documentation](https://github.com/Snaatak-Skyops/Documentation/blob/7040e168531b00d50efa9eaad8403078f5ae9ae3/OT%20MS%20Understanding/Database/Scylla%20DB/Documentation/README.md) | ScyllaDB Setup Documentation |
| [FullStack POC](https://github.com/Snaatak-Skyops/Documentation/blob/248bc065b0df7f0fcd3ce726ff8e5255232e765f/OT%20MS%20Understanding/Application/Full%20Stack/FullStackrun.md) | Full stack setup documentation |






