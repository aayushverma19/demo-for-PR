#    **Attendance API POC**


| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Internal Reviewer** |**Reviewer L0** |**Reviewer L1** |**Reviewer L2** |
|------------|---------------------------|-------------|----------------|-----|-------------|-------------|-------------|-------------|
| Aayush Verma|   10-02-2025             | v1          | Aayush Verma   |18-02-2025    |  Komal Jaiswal | Akshit kapil | Taranddeep | Abhishek  Dubey|


## **Table of Contents**

<details>
  <summary>Installation Steps</summary>

  - [1. Update Package List](#1-update-package-list)
  - [2. Clone the Repository](#2-clone-the-repository)
  - [3. Install Postgresql](#3-install-postgresql)
  - [4. Install Redis](#4-install-redis)
  - [5. Install Python](#5-install-python)
  - [6. Install Poetry](#6-install-poetry)
  - [7. Install Liquibase](#7-install-and-add-liquibase-repository)
  - [8. Install Development Libraries ](#8-install-development-dependencies)
  - [9. Install Make ](#9-install-make)

</details>

<details>
  <summary>Configuration Steps</summary>

  - [10. Create User for Postgresql](#10-create-a-user-to-access-postgresql)
  - [11. PostgreSQL Configuration](#11-edit-postgresql-configuration)
  - [12. PostgreSQL Authentication Configuration](#12-edit-postgresql-authentication-configuration)
  - [13. Restart PostgreSQL](#13-restart-postgresql)
  - [14. Update Redia Configuration](#14-update-redis-configuration)

</details>


<details>
  <summary>Project Setup</summary>

  - [15. Navigate to Project Directory](#15-navigate-to-the-project-directory)
  - [16. Set Python Version for Poetry](#16-set-python-version-for-poetry)
  - [17. Edit Configuration Files](#17-edit-configuration-files)
  - [18. Initialize Database](#18-initialize-the-database)
  - [19. Install Project Dependencies](#19-install-project-dependencies)
  - [20. Run Migration Command](#20-run-database-migrations)
  - [21. Add Gunicorn and Reinstall Dependencies](#21-add-gunicorn-and-reinstall-dependencies)
  - [22. Run the Application](#22-run-the-application)
  - [23. Page will be accessible](#23-the-swagger-page-will-be-accessible)

</details>
<details>
 <summary >Contact Information and References</summary>
 
  - [Contact Information](#contact-information)
  - [References](#references)

 
</details>

  
---



# Step-by-step installation of Attendance API

### **1. Update Package List**
```bash
sudo apt update
```
  Updates the list of available packages and their versions from the configured repositories.
 Ensures you have the latest information about available software packages before installing anything.

---

### **2. Clone the Repository**
```bash
git clone https://github.com/OT-MICROSERVICES/attendance-api.git
```
Clone the `attendance-api` repository from GitHub to your local machine.

To get the source code of the project so you can set it up and run it locally

---


### **3. Install PostgreSQL**
```bash
sudo apt install postgresql postgresql-contrib -y
```
Install's PostgreSQL (a relational database) and additional contributed packages. The `attendance-api` project is using PostgreSQL as it’s database backend, so it need to be install.

---

### **4. Install Redis**
- To install Redis on your system, please follow the link below for the Redis Installation Guide. :- [Redis Installation Guide](https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/Mohit-SCRUM-12/Common/Software/Redis/Installation/README.md)

---

### **5. Install Python**

- To install Python on your system, please follow the link below for the Python Installation Guide. :- [Python Installation Guide](https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/Aayush-SCRUM-2/Common/Software/Python/Installation/README.md#how-to-install-python-using-deadsnakes-ppa-ubuntu-only)

Install's Python 3.11, required for the project.

---

### **6. Install Poetry**

- To install Poetry on your system, please follow the link below for the Poetry Installation Guide. :- [Poetry Installation Guide](https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/Aayush-SCRUM-2/Common/Software/Poetry/Installation/README.md)

Install's Poetry, a dependency management and packaging tool for Python. The project uses Poetry to manage Python dependencies and virtual environments.

---

### **7. Install and Add Liquibase Repository**
- To install Liquibase on your system, please follow the link below for the Liquibase Installation Guide. :- [Liquibase Installation Guide](https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/Aayush-SCRUM-2/Common/Software/Liquibase/Installation/README.md)

Installs Liquibase. To manage database migrations for the project.

---

### **8. Install Development Dependencies**
- To install Dev-Dependencies on your system, please follow the link below for the Development Dependencies Installation Guide. :- [Dev-Dependencies Installation Guide](https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/Aayush-SCRUM-2/Common/Software/Python/Dependencies/README.md#install-development-dependencies)

Installs development libraries and tools required for building Python packages. Some dependencies (e.g., `psycopg2` for PostgreSQL) require these libraries.

---

### **9. Install Make**
- To install Make on your system, please follow the link below for the Make Installation Guide. :- [Make Installation Guide](https://github.com/snaatak-Zero-Downtime-Crew/Documentation/tree/Nikita-SCRUM-8/Common/Software/Make/Installation%20)

 Installs the `make` utility.
 To run Makefile commands for tasks like database migrations.

---

### **10. Install PostgreSQL & Create a user**

- To install PostgreSQL on your system, please follow the link below for the PostgreSQL Installation Guide. :- [PostgreSQL Installation Guide](https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/Pooja-SCRUM-14/Common/Software/PostgreSql/installation/Readme.md)

```bash
sudo -u postgres psql
```
```bash
ALTER USER postgres PASSWORD '<password>';
```
  Open the PostgreSQL interactive terminal as the `postgres` user (the default superuser for PostgreSQL).
 To perform administrative tasks like creating databases and users.

**Note:-** If you are facing a PostgreSQL authentication error due to an incorrect password for the user 'postgres' on localhost (127.0.0.1) at port 5432, you will need to reset the password.

Never use the default username and password when setting up your database.

We have to use a strong password for best practice.

https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/Pooja-SCRUM-14/Common/Software/PostgreSql/installation/Readme.md

---

### **11. Edit PostgreSQL Configuration**
```bash
sudo vi /etc/postgresql/16/main/postgresql.conf
```
change

```bash
listen_addresses = '127.0.0.1 <private ip>' 
```
**example :-**
```bash
   listen_addresses = '127.0.0.1,172.31.0.1'
```

  Open the PostgreSQL configuration file for editing.
 To configure settings like listening addresses, port, and other database parameters.

https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/Pooja-SCRUM-14/Common/Software/PostgreSql/configuration/Readme.md#step-3-configure-postgresql-for-external-connections

---

### **12. Edit PostgreSQL Authentication Configuration**
```bash
sudo vi /etc/postgresql/16/main/pg_hba.conf
```
Add

```bash
    host    <db_name>             <db_user_name>             <private ip>/16           scram-sha-256
```
**example :-**

```bash
    host    attendance_db   postgres        172.31.0.1/16           scram-sha-256  #172.31.0.1/16 → Allows only the specific IP 172.31.0.1.
```

 Open the PostgreSQL client authentication configuration file.
 To configure which IPs or users are allowed to connect to the database and how they authenticate.

https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/Pooja-SCRUM-14/Common/Software/PostgreSql/configuration/Readme.md#step-4-edit-pg_hbaconf

---

### **13. Restart PostgreSQL**

```bash
sudo systemctl restart postgresql
```
  Restarts the PostgreSQL service.
 To apply changes made to the configuration files (`postgresql.conf` and `pg_hba.conf`).

---

### **14. Update Redis Configuration**

- Kindly follow the link below for this  :- [ Redis Configuration and Security](https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/Mohit-SCRUM-12/Common/Software/Redis/Configuration/README.md)

  
  Opens the Redis configuration file for editing.
 To bind Redis to specific IP addresses (e.g., `127.0.0.1,172.31.24.234` and a private IP) for security and accessibility and after that restart Radis.

---



### **15. Navigate to the Project Directory**
```bash
cd attendance-api/
```
  Changes the current directory to the `attendance-api` project folder.
 To work within the project's context.

---

### **16. Set Python Version for Poetry**
```bash
poetry env use python3.11
```
  Specifies Python 3.11 as the interpreter for the Poetry virtual environment.
 To ensure the project uses the correct Python version.

---

### **17. Edit Configuration Files**
- **`liquibase.properties`**: Updates the database connection URL to point to the correct PostgreSQL instance and full path of this configuration File **attendance-api/liquibase.properties**
```bash
url=jdbc:postgresql://<private_ip>:5432/attendance_db  # Private IP of the PostgreSQL database server
```
**Example**

```bash
url=jdbc:postgresql://172.31.0.1:5432/attendance_db  # Private IP of the PostgreSQL database server
```

- **`pyproject.toml`**: Ensures the correct Python packages are included in the build  and full path of this configuration File **attendance-api/pyproject.toml**
```bash
packages = [{ include = "attendance_api" }]
```

**or**

```bash
packages = [
                    { include = "client" },
                    { include = "models" },
                    { include = "router" },
                    { include = "utils" }
               ]
```
To add a single package to the list, follow the same format as the existing ones. For example, if you want to add the router package, include it.

- **`config.yaml`**: Updates the host IP address for the application and full path of this configuration File **attendance-api/config.yaml**
  
```bash
host: <private ip>  # Private IP of the PostgreSQL database server and radis server.
```
**Example:-**

```bash
host: 172.31.0.1
```

---

### **18. Initialize the Database**

```bash
bash scripts/db_init.sh
```
  Runs a script to initialize the database.
 To set up the database schema and initial data.
 
**`db_init.sh`** This script already exists in your project, and full path is: **attendance-api/scripts/db_init.sh**

**NOTE:-** If you haven't run the db_init.sh script,

**1.** Database Not Found – The attendance_db database won't exist, causing connection failures.

**2.** Table Not Found – Queries will fail because the records table is missing.

**3.** Application Startup Failure – The app may crash or show errors due to missing schema elements.

---

### **19. Install Project Dependencies**
```bash
poetry install
```
  Installs all Python dependencies listed in `pyproject.toml`.
 To set up the project's virtual environment with the required packages.

---

### **20. Run Database Migrations**
```bash
make run-migrations
```
  Executes database migrations using Liquibase.
 To apply changes to the database schema.

If liquibase is unable to connect to the PostgreSQL database at <IP>:5432. The connection is being refused, likely due to one of the following reasons:

**1.** Database server is down – Ensure the PostgreSQL server is running.

**2.** Incorrect hostname or port – Verify that <ip> and 5432 are correct.

**3.** Firewall or network issues – The server might be blocking external connections.

**4.** PostgreSQL is not accepting remote connections – Check postgresql.conf and pg_hba.conf.

**5.** Invalid credentials – Verify the username and password in liquibase.properties.

---

### **21. Add Gunicorn and Reinstall Dependencies**
```bash
poetry add gunicorn
poetry install
```
Adds Gunicorn (a WSGI server) as a dependency to the project. Gunicorn is used to serve the Python application in production and Reinstalls all dependencies listed in `pyproject.toml`


### **22. Run the Application**
```bash
poetry run gunicorn app:app --log-config log.conf -b 0.0.0.0:8080
```
  Starts the application using Gunicorn, a WSGI server.
 To serve the application on port 8080, accessible from any IP address.

### **23. The swagger page will be accessible**
```bash
http://<localhost or Public ip>:8080/apidocs
```

**Example:-**

```bash
http://35.175.137.95:8080/apidocs
```

# Contact Information

| **Name**       | **Email Address**            |
|-----------------|------------------------------|
| Aayush Verma    | <aayush.verma@mygurukulam.co>     |

# References

| **Link**                                                                                                                     | **Description**                                    |
|-----------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|
| [How to install and configure PostgreSQL on Ubuntu 20.04](https://medium.com/devops-technical-notes-and-manuals/how-to-install-and-configure-postgresql-on-ubuntu-20-04-4fd3cf072d6f) | PostgreSQL installation and configuration       |
|[Attendance API Project Link](https://github.com/OT-MICROSERVICES/attendance-api/blob/main/README.md) |Attendance-API Documentation |
