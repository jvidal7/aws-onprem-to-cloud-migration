# aws-onprem-to-cloud-migration

Migrated a legacy on-premises Employee Directory application to AWS by implementing a secure and scalable two-tier architecture using Amazon EC2, Amazon RDS for MySQL, and AWS Database Migration Service (DMS). This project demonstrates application migration, database modernization, networking configuration, and migration cutover validation in a cloud environment.

---

## Project Overview

This project demonstrates the migration of a traditional on-premises Employee Directory application to AWS. The original environment consisted of a Linux-based application server and a locally managed MySQL database, creating challenges around scalability, availability, and operational maintenance.

To modernize the environment, I migrated the application to Amazon EC2, migrated the database to Amazon RDS for MySQL, and used AWS Database Migration Service (DMS) to perform database replication and migration.

---

## Architecture Diagram

![Architecture Diagram](images/architecture-diagram.png)

---

## Solution Architecture

The migrated environment consists of:

- Amazon EC2 for application hosting
- Amazon RDS for MySQL database management
- AWS DMS for database migration and replication
- Amazon VPC for network isolation
- Security Groups for traffic control
- IAM for identity and access management

---

## Key Responsibilities

During this project, I:

- Deployed the application on Amazon EC2
- Migrated the MySQL database to Amazon RDS
- Configured AWS DMS replication tasks
- Implemented VPC networking and Security Groups
- Updated application configuration settings
- Performed migration testing and validation
- Executed the final migration cutover

---

## AWS Services Used

| Service | Purpose |
|----------|----------|
| Amazon EC2 | Application hosting |
| Amazon RDS (MySQL) | Managed relational database |
| AWS DMS | Database migration and replication |
| IAM | Identity and access management |
| VPC | Network isolation |
| Security Groups | Traffic filtering and access control |

---

## Outcome

By completing this project, I successfully:

- Migrated an on-premises application to AWS
- Deployed the application on Amazon EC2
- Migrated the database to Amazon RDS for MySQL
- Implemented secure networking and access controls
- Performed database replication using AWS DMS
- Validated application functionality after migration
- Delivered a fully operational cloud-hosted Employee Directory application

---

## Setting Up the Local On-Premises Environment

### Purpose

Before migrating the application to AWS, I deployed and validated the Employee Directory application in a local on-premises environment. This established a baseline environment that would later be migrated to AWS and served as a reference point for post-migration validation.

---

### Step 1: Install Node.js

I installed Node.js and npm to support the application backend and verified the installation by checking the installed versions.

```bash
node -v
npm -v
```

### Screenshot

![Node.js Verification](images/01-nodejs-verification.png)

---

### Step 2: Install and Configure MySQL

I installed MySQL Community Server and configured the local database environment required by the application.

This included:

* Creating the `employee_db` database
* Creating a dedicated application user
* Assigning database permissions
* Creating the `employees` table

### Screenshot

![MySQL Database Setup](images/02-mysql-database-setup.png)

---

### Step 3: Download and Configure the Application

I cloned the application repository and installed all required dependencies.

```bash
git clone https://github.com/techwithlucy/ztc-projects.git

cd ztc-projects/projects/cloud-engineer-projects/project-1

npm install
```

### Screenshot

![Application Installation](images/03-application-installation.png)

---

### Step 4: Configure Environment Variables

I created a `.env` file containing the application database connection details and runtime configuration.

---

### Step 5: Start the Application

After completing the configuration, I started the application and verified successful connectivity between the application and the MySQL database.

```bash
npm start
```

### Screenshot

![Application Startup](images/04-application-startup.png)

---

### Step 6: Validate Application Functionality

After successfully starting the application, I accessed the Employee Directory web interface and performed functional testing by creating multiple employee records across different departments and locations.

This validation confirmed that the application was functioning correctly and that employee data was being successfully stored in the MySQL database.

### Screenshot

![Employee Directory UI](images/05-employee-directory-ui.png)

---

### Outcome

At the end of this phase, I successfully:
- Deployed the application in a local on-premises environment
- Configured and connected the MySQL database
- Verified successful application-to-database connectivity
- Created and stored employee records in the database
- Validated application functionality and data persistence
- Established the baseline environment for migration to AWS

---

## Simulated On-Premises Server on Amazon EC2

### Objective

I deployed the Employee Directory application and MySQL database on an Ubuntu EC2 instance to create a Linux-based simulated on-premises environment.

This environment will serve as the source workload for the upcoming database migration to Amazon RDS using AWS Database Migration Service (DMS).

---

### Step 1: Launch and Configure the EC2 Instance

I launched an Ubuntu EC2 instance to host the Employee Directory application and MySQL database.

I configured:

* Ubuntu Server 24.04 LTS
* Public IPv4 connectivity
* SSH access for server administration
* TCP port `3000` for application access
* Security Group rules to control inbound traffic

### Screenshot

![EC2 Instance](images/06-ec2-instance.png)

**Capture:** The EC2 console showing the instance in the **Running** state. Include the instance name, instance type, and status.

---

### Step 2: Connect to the EC2 Instance

I connected to the Ubuntu EC2 instance using SSH to perform the server configuration and application deployment.

```bash
ssh -i your-key.pem ubuntu@<EC2_PUBLIC_IP>
```

I then installed and verified Node.js, npm, and Git to prepare the server for the Employee Directory application.

```bash
node -v
npm -v
git --version
```

### Screenshot

![EC2 Server Environment](images/07-ec2-environment.png)


**Capture:** The SSH terminal showing the successful connection and the Node.js, npm, and Git versions.

---

### Step 3: Configure MySQL on EC2

I installed and configured MySQL Server on the EC2 instance to provide the database layer for the Employee Directory application.

I created:

* `employee_db` database
* `employee_user` application account
* Required database privileges
* `employees` table

I verified the database configuration using:

```sql
SHOW DATABASES;
USE employee_db;
SHOW TABLES;
```

### Screenshot

![EC2 MySQL Database](images/08-ec2-mysql-database.png)

**Screenshot filename:** `08-ec2-mysql-database.png`

**Capture:** The MySQL terminal showing that `employee_db` exists and `SHOW TABLES;` returns the `employees` table.

---

### Step 4: Deploy the Employee Directory Application

I cloned the Employee Directory application onto the EC2 instance and installed the required Node.js dependencies.

```bash
git clone https://github.com/techwithlucy/ztc-projects.git

cd ztc-projects/projects/cloud-engineer-projects/project-1

npm install
```

I then configured the application environment variables to connect the Node.js backend to the MySQL database running on the EC2 instance.

---

### Step 5: Start the Application on EC2

I started the Node.js application and verified that it successfully connected to the MySQL database.

```bash
npm start
```

### Screenshot

![EC2 Application Startup](images/09-ec2-application-startup.png)

**Screenshot filename:** `09-ec2-application-startup.png`

**Capture:** The terminal showing both the application server running on port `3000` and the successful MySQL connection.

For example:

```text
Server running at http://localhost:3000
Connected to MySQL as: employee_user
```

---

### Step 6: Validate Application Functionality

I accessed the Employee Directory application remotely through the EC2 instance and created multiple employee records to validate application functionality and database persistence.

This confirmed that:

* The application was successfully running on EC2
* The application was remotely accessible
* The Node.js backend successfully connected to MySQL
* Employee records could be created and retrieved
* Employee data persisted in the MySQL database

### Screenshot

![Employee Directory Running on EC2](images/10-ec2-employee-directory.png)

**Screenshot filename:** `10-ec2-employee-directory.png`

**Capture:** My browser showing the Employee Directory running from the EC2 instance with several employee records visible.

---

### Outcome

At the end of this phase, I successfully:

* Provisioned an Ubuntu EC2 instance
* Configured network access using Security Groups
* Installed the required application runtime and dependencies
* Installed and configured MySQL Server
* Deployed the Employee Directory application
* Established application-to-database connectivity
* Validated remote application access and data persistence
* Established the EC2-hosted MySQL database as the source environment for the upcoming AWS DMS migration

The next phase will migrate the MySQL database from this simulated on-premises environment to Amazon RDS for MySQL using AWS Database Migration Service (DMS).

---
