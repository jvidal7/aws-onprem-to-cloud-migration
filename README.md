# aws-onprem-to-cloud-migration
Migrated an on-prem Employee Directory application to AWS using EC2, Amazon RDS, and AWS DMS. Implemented secure networking, database migration, and application cutover testing to build a scalable cloud-native architecture with high availability and improved reliability.

---

# Project Overview

In this project, I migrated an on-premises Employee Directory Web Application to AWS using a scalable and cloud-native architecture. The original application was hosted on a single Linux server with a local MySQL database, which created several operational and scalability challenges as the company expanded.

I designed and implemented a two-tier AWS architecture using Amazon EC2 for the application layer and Amazon RDS for the database layer. I also used AWS Database Migration Service (DMS) to replicate and migrate the MySQL database from the on-premises environment into AWS.

This project demonstrates real-world cloud migration practices including infrastructure deployment, database migration, networking configuration, security implementation, testing, and migration cutover.

---

### Scenario

CloudHR Systems is a growing HR software provider that relies on an internal Employee Directory Web Application to manage:

- Employee profiles
- Departments
- Roles
- Employee documents

The environment was originally hosted on a single on-premises Linux server running:

- Application backend
- Local MySQL database

As the company expanded across multiple office locations, the infrastructure began experiencing several issues:

- Frequent server downtime
- Storage limitations
- Poor scalability
- Increased maintenance overhead
- Risk of data loss due to lack of redundancy

To improve reliability, scalability, and long-term operational efficiency, I migrated the application and database infrastructure to AWS.

---

### My Role as the Cloud Engineer

As the Cloud Engineer for this project, I was responsible for performing a complete migration of the Employee Directory Application from the on-premises environment to AWS.

My responsibilities included:

- Migrating the application backend to Amazon EC2
- Migrating the MySQL database to Amazon RDS
- Using AWS DMS for database replication and migration
- Configuring networking and security
- Updating application configurations
- Performing migration testing and validation
- Completing the final migration cutover

---

### About the Project

In this hands-on cloud migration project, I:

- Set up and ran the Employee Directory Application locally
- Deployed the application backend on Amazon EC2
- Migrated the MySQL database into Amazon RDS using AWS DMS
- Performed migration testing and cutover validation

By completing this project, I successfully deployed a fully functional cloud-hosted Employee Directory Application running entirely on AWS.

This project also serves as a professional portfolio project demonstrating practical cloud migration experience.

---

### Project Steps

The following migration phases were completed during this project:

1. Set up the local “on-premises” application
2. Migrated the application server to Amazon EC2
3. Migrated the database to Amazon RDS using AWS DMS
4. Updated application configurations and performed testing
5. Completed the final migration cutover

---

### AWS Services Used

| Service | Purpose |
|---|---|
| Amazon EC2 | Hosted the application backend |
| Amazon RDS (MySQL) | Managed relational database service |
| AWS DMS | Database migration and replication |
| IAM | Identity and access management |
| VPC | Network isolation and infrastructure |
| Security Groups | Controlled inbound and outbound traffic |
| Subnets | Organized AWS network resources |

---

### Architecture Diagram

![Architecture Diagram](images/architecture-diagram.png)

---
## Setting Up the Local “On-Prem” Application

### Purpose

Before migrating the application to AWS, I first deployed and tested the Employee Directory Application in a local on-premises environment on my machine.

This step allowed me to establish a baseline version of the application before beginning the cloud migration process.

By running the application locally, I was able to:

- Understand how the application behaves in a traditional on-premises environment
- Capture “before migration” screenshots for project documentation
- Prepare the same environment that would later be recreated on Amazon EC2
- Compare local versus cloud performance and functionality after migration

---

### Step 1: Install Node.js

The Employee Directory Application uses Node.js for the backend server, so I first installed Node.js and npm on my local machine.

I downloaded the LTS version from the official Node.js website:

- https://nodejs.org/en/download/prebuilt-installer

After installation, I verified both Node.js and npm were installed successfully by running:

```bash
node -v
npm -v
```

---

### Step 2: Install MySQL (Local Database Layer)

The application uses MySQL as its relational database for storing employee records and application data.

I installed MySQL Community Server from:

- https://dev.mysql.com/downloads/mysql/

During installation, I recorded:

- MySQL username
- MySQL password
- Port number (3306)

---

### Step 3: Create the Database and Application User

I logged into MySQL as the root user:

```bash
mysql -u root -p
```

I then created the database:

```sql
CREATE DATABASE employee_db;
```

Created the application user:

```sql
CREATE USER 'employee_user'@'%' IDENTIFIED BY 'StrongPassword123';
```

Granted permissions:

```sql
GRANT ALL PRIVILEGES ON employee_db.* TO 'employee_user'@'%';
FLUSH PRIVILEGES;
```

Selected the database:

```sql
USE employee_db;
```

Created the employees table:

```sql
CREATE TABLE employees (
  id INT AUTO_INCREMENT PRIMARY KEY,
  full_name VARCHAR(100) NOT NULL,
  email VARCHAR(100) NOT NULL,
  role VARCHAR(100),
  department VARCHAR(100),
  location VARCHAR(100),
  join_date DATE NULL,
  photo_url VARCHAR(255) DEFAULT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

Exited MySQL:

```sql
EXIT;
```

---

### Step 4: Download the Employee Directory Application

I cloned the repository:

```bash
git clone https://github.com/techwithlucy/ztc-projects.git
```

Moved into the project directory:

```bash
cd ztc-projects/projects/cloud-engineer-projects/project-1
```

Installed dependencies:

```bash
npm install
```

---

### Step 5: Configure Environment Variables

I created the `.env` file:

```bash
vim .env
```

Added the following configuration:

```env
DB_HOST=localhost
DB_USER=employee_user
DB_PASSWORD=StrongPassword123
DB_NAME=employee_db
PORT=3000
```

---

### Step 6: Start the Local Application

I started the application server:

```bash
npm start
```

Successful startup output:

```bash
Server running on http://localhost:3000
Connected to MySQL successfully
```

---

### Step 7: Access the Employee Directory UI

I opened the application in my browser:

```text
http://localhost:3000
```

I tested the application by adding sample employee records to verify database connectivity and application functionality.

---

### Final Outcome

By the end of this section, I had:

- A fully working Employee Directory Application running locally
- A functioning MySQL database with employee records
- A complete on-premises simulation of the application
- The “before migration” version of the environment

In the next section, I will migrate the application from my local machine to Amazon EC2.

---
