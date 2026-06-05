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
