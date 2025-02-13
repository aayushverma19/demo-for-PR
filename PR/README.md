#    **Attendance API POC**


| **Author** | **Created on** | **Version** | **Last updated by**|**Internal Reviewer** |**Reviewer L0** |**Reviewer L1** |**Reviewer L2** |
|------------|---------------------------|-------------|---------------------|-------------|-------------|-------------|-------------|
| Aayush Verma|   10-02-2025             | v1          | Aayush Verma        |  Komal Jaiswal |  |   |      |

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
Clones the `attendance-api` repository from GitHub to your local machine.

To get the source code of the project so you can set it up and run it locally

---


### **3. Install PostgreSQL**
```bash
sudo apt install postgresql postgresql-contrib -y
```
Install's PostgreSQL (a relational database) and additional contributed packages. The `attendance-api` project is using PostgreSQL as it’s database backend, so it need to be install.

---

### **4. Create a user to Access PostgreSQL**
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

---

### **5. Edit PostgreSQL Configuration**
```bash
sudo vi /etc/postgresql/16/main/postgresql.conf
```
change

```bash
listen_addresses = '127.0.0.1,<private ip>' 
```
**example :-**
```bash
   listen_addresses = '127.0.0.1,172.31.0.1'
```

  Open the PostgreSQL configuration file for editing.
 To configure settings like listening addresses, port, and other database parameters.

---

### **6. Edit PostgreSQL Authentication Configuration**
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

---

### **7. Restart PostgreSQL**
```bash
sudo systemctl restart postgresql
```
  Restarts the PostgreSQL service.
 To apply changes made to the configuration files (`postgresql.conf` and `pg_hba.conf`).

---

### **8. Install Redis**
```bash
sudo apt install redis-server -y
```
  Install's Redis, an in-memory data store.
 The project might use Redis for caching, session management, or other purposes.

---

### **9. Edit Redis Configuration**
```bash
sudo vi /etc/redis/redis.conf
```
  Opens the Redis configuration file for editing.
 To bind Redis to specific IP addresses (e.g., `127.0.0.1` and a private IP) for security and accessibility.

---

### **10. Restart Redis**
```bash
sudo systemctl restart redis
```
  Restarts the Redis service.
 To apply changes made to the Redis configuration file.

---

### **11. Install Poetry**
```bash
curl -sSL https://install.python-poetry.org | python3 -
```
  Install's Poetry, a dependency management and packaging tool for Python.
 The project uses Poetry to manage Python dependencies and virtual environments.

---

### **12. Add Poetry to PATH**
```bash
export PATH="$HOME/.local/bin:$PATH"
```
Adds Poetry's installation directory ($HOME/.local/bin) to the system's PATH environment variable using the command export PATH="$HOME/.local/bin:$PATH", making the poetry command available globally in the terminal."

---

### **13. Reload Bash Configuration**
```bash
source ~/.bashrc
```
  Reloads the Bash shell configuration file.
 To apply changes to the `PATH` or other environment variables.

---

### **14. Add Python PPA**
```bash
sudo add-apt-repository ppa:deadsnakes/ppa
```
  Adds the `deadsnakes` PPA (Personal Package Archive) to the system.
 To access newer versions of Python (e.g., Python 3.11) that may not be available in the default repositories.

---

### **15. Install Python**
```bash
sudo apt install python3.11 -y
```
Install's Python 3.11, required for the project.

---

### **16. Install OpenJDK(Java)**
```bash
sudo apt install openjdk-11-jdk -y
```
  Install's the OpenJDK 11 Java Development Kit.
 Required for running Liquibase, a database migration tool.

---

### **17. Add Liquibase Repository**
```bash
wget -O- https://repo.liquibase.com/liquibase.asc | gpg --dearmor > liquibase-keyring.gpg && cat liquibase-keyring.gpg | sudo tee /usr/share/keyrings/liquibase-keyring.gpg > /dev/null && echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/liquibase-keyring.gpg] https://repo.liquibase.com stable main' | sudo tee /etc/apt/sources.list.d/liquibase.list
```
  Adds the Liquibase repository and its GPG key to the system.
 To install Liquibase from the official repository.

---

### **18. Update Package List**
```bash
sudo apt update
```
  Updates the package list again after adding the Liquibase repository.
 To ensure the system recognizes the new repository.

---

### **19. Install Liquibase**
```bash
sudo apt install liquibase
```
  Installs Liquibase.
 To manage database migrations for the project.

---

### **20. Navigate to the Project Directory**
```bash
cd attendance-api/
```
  Changes the current directory to the `attendance-api` project folder.
 To work within the project's context.

---

### **21. Set Python Version for Poetry**
```bash
poetry env use python3.11
```
  Specifies Python 3.11 as the interpreter for the Poetry virtual environment.
 To ensure the project uses the correct Python version.

---

### **22. Edit Configuration Files**
- **`liquibase.properties`**: Updates the database connection URL to point to the correct PostgreSQL instance.
```bash
url=jdbc:postgresql://<private_ip>:5432/attendance_db  # Private IP of the PostgreSQL database server
```

- **`pyproject.toml`**: Ensures the correct Python packages are included in the build.
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

- **`config.yaml`**: Updates the host IP address for the application.
  
```bash
host: <private ip>  # Private IP of the PostgreSQL database server and radis server.
```

---

### **23. Initialize the Database**

```bash
bash scripts/db_init.sh
```
  Runs a script to initialize the database.
 To set up the database schema and initial data.
 
**`db_init.sh`** This script already exists in your project, and its full path is: **attendance-api/scripts/db_init.sh**

**NOTE:-** If you haven't run the db_init.sh script,

**1.** Database Not Found – The attendance_db database won't exist, causing connection failures.

**2.** Table Not Found – Queries will fail because the records table is missing.

**3.** Application Startup Failure – The app may crash or show errors due to missing schema elements.

---

### **24. Install Development Dependencies**
```bash
sudo apt install -y python3.11-dev libpq-dev gcc
```
  Installs development libraries and tools required for building Python packages.
 Some dependencies (e.g., `psycopg2` for PostgreSQL) require these libraries.

---

### **25. Install Project Dependencies**
```bash
poetry install
```
  Installs all Python dependencies listed in `pyproject.toml`.
 To set up the project's virtual environment with the required packages.

---

### **26. Install Make**
```bash
sudo apt install make
```
  Installs the `make` utility.
 To run Makefile commands for tasks like database migrations.

---

### **27. Run Database Migrations**
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

### **28. Add Gunicorn and Reinstall Dependencies**
```bash
poetry add gunicorn
poetry install
```
Adds Gunicorn (a WSGI server) as a dependency to the project. Gunicorn is used to serve the Python application in production and Reinstalls all dependencies listed in `pyproject.toml`


### **29. Run the Application**
```bash
poetry run gunicorn app:app --log-config log.conf -b 0.0.0.0:8080
```
  Starts the application using Gunicorn, a WSGI server.
 To serve the application on port 8080, accessible from any IP address.

### **30. The swagger page will be accessible**
```bash
http://<localhost or Public ip>:8080/apidocs
```

# Contact Information

| **Name**       | **Email Address**            |
|-----------------|------------------------------|
| Aayush Verma    | <aayushverma4481@gmail.com>     |

# References

| **Link**                                                                                                                     | **Description**                                    |
|-----------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|
| [How to install and configure PostgreSQL on Ubuntu 20.04](https://medium.com/devops-technical-notes-and-manuals/how-to-install-and-configure-postgresql-on-ubuntu-20-04-4fd3cf072d6f) | PostgreSQL installation and configuration       |
| [How to install Liquibase Database DevOps](https://chandrapurnimabhatnagar.medium.com/how-to-install-liquibase-database-devops-34ca9a6d9705) | Liquibase installation                          |
