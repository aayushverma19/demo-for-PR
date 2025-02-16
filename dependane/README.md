#  Install Python Package POC

| **Author** | **Created on** | **Version** | **Last updated by**|**Internal Reviewer** |**Reviewer L0** |**Reviewer L1** |**Reviewer L2** |
|------------|---------------------------|-------------|---------------------|-------------|-------------|-------------|-------------|
| Aayush Verma|   13-02-2025             | v1          | Aayush Verma        |  Komal Jaiswal |  |   |      |

---

### **Setting Up Development Dependencies for Python Projects**

When working on Python projects, especially those involving database integrations or packages with native extensions, having the right development tools and libraries is essential. This guide will walk you through the pre-installation steps and the installation command, ensuring your environment is ready for seamless development.

---

### **Pre-Installation Checklist**

Before running the installation command, follow these steps to prepare your system:

1. **Verify System Requirements**  
   - Ensure you are on a Debian-based Linux distribution (e.g., Ubuntu) with `apt` as the package manager.  
   - Confirm that you have sudo access to execute administrative commands.

2. **Check Python Version**  
   - Confirm Python 3.11 is installed by running:  
     ```bash
     python3.11 --version
     ```  
   - If not installed, add it using:  
     ```bash
     sudo apt update
     sudo apt install -y python3.11
     ```

3. **Update Package Index**  
   - Update your package index to ensure you’re installing the latest versions:  
     ```bash
     sudo apt update
     ```

4. **Verify PostgreSQL Installation (Optional)**  
   - If your project involves PostgreSQL, ensure PostgreSQL is installed and configured:  
     ```bash
     psql --version
     ```  
   - If missing, install it with:  
     ```bash
     sudo apt install -y postgresql
     ```

6. **Ensure Sufficient Disk Space**  
   - Make sure your system has at least 500MB of free disk space to accommodate the tools and libraries.

---

### **Command to Install Development Dependencies**

Once the pre-installation checklist is complete, run the following command to install the necessary libraries and tools:

```bash
sudo apt install -y python3.11-dev libpq-dev 
```

#### **Breakdown of the Command**
- **`python3.11-dev`**: Provides header files and static libraries for Python 3.11, essential for building Python packages with native extensions.  
- **`libpq-dev`**: Includes PostgreSQL development libraries and headers, required for Python packages like `psycopg2` that interact with PostgreSQL.  

---

### **Conclusion**

Installing development dependencies is a crucial step in setting up a robust Python development environment. By completing the pre-installation checklist and running the installation command, you can ensure your system is ready for building and running Python projects seamlessly. These tools and libraries help avoid errors and allow for smooth integration of high-performance packages like `psycopg2` modules.  

## Contact Information

| **Name**       | **Email Address**            |
|-----------------|------------------------------|
| Aayush Verma    | <aayushverma4481@gmail.com>     |

## References

| **Link**                                                                                                                     | **Description**                   |
|---------------------------------------------------------------------------------------------------------------|--------------------------------------------------|
| [How to install Python Dependencies](https://medium.com/django-unleashed/fixing-psycopg2-installation-errors-on-ubuntu-and-mac-a-simple-guide-277a777b3c50) | Python Dependencies  |
