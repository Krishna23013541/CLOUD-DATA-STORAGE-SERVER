# EX-3(a) : CLOUD-DATA-STORAGE-SERVER
## Name : Krishna Kumar R
## Register Number : 212223230107
## Aim

To create a highly available MySQL database using **Amazon RDS**, configure secure connectivity between an EC2 web server and the RDS database, and interact with the database through a web application.

## Algorithm

1. Open the AWS Management Console and access the VPC service.
2. Create a security group named `DB Security Group` in `Lab VPC`.
3. Configure an inbound rule to allow MySQL/Aurora traffic on port `3306` from `Web Security Group`.
4. Open Amazon RDS and create a DB subnet group named `DB-Subnet-Group`.
5. Select Availability Zones `us-east-1a` and `us-east-1b`.
6. Select the subnets with CIDR ranges `10.0.1.0/24` and `10.0.3.0/24`.
7. Create an RDS MySQL database named `lab-db`.
8. Configure the database as a **Multi-AZ DB instance** using `db.t3.micro`.
9. Configure the database name as `lab` and username as `main`.
10. Associate the database with `Lab VPC`, `DB Security Group`, and `DB-Subnet-Group`.
11. Wait until the RDS instance status becomes **Available**.
12. Copy the RDS database endpoint.
13. Open the web application using the WebServer IP address.
14. Select the **RDS** option in the web application.
15. Enter the RDS endpoint, database name, username, and password.
16. Submit the configuration to connect the web application to RDS.
17. Test the Address Book application by adding, editing, and deleting contacts.
18. Verify that the data is successfully persisted in the RDS database.

## Program

### RDS Configuration

```text
Database Engine      : MySQL
DB Instance Identifier: lab-db
Deployment            : Multi-AZ DB Instance
Instance Class        : db.t3.micro
Storage               : 20 GB General Purpose SSD
Database Name         : lab
Master Username       : main
VPC                   : Lab VPC
DB Subnet Group       : DB-Subnet-Group
Security Group        : DB Security Group
MySQL Port            : 3306
```

### Security Group Configuration

```text
Security Group Name : DB Security Group
Description         : Permit access from Web Security Group
Inbound Protocol    : TCP
Port                : 3306
Source              : Web Security Group
```

### DB Subnet Group

```text
Name        : DB-Subnet-Group
VPC         : Lab VPC

Availability Zones:
- us-east-1a
- us-east-1b

Subnets:
- 10.0.1.0/24
- 10.0.3.0/24
```

### Web Application Configuration

```text
Endpoint : <RDS endpoint>
Database : lab
Username : main
Password : <lab password>
```

> For a public GitHub repository, do not include the actual database password or other credentials.

## Output

### 1. DB Security Group

The RDS security group was successfully created with MySQL port `3306` accessible from the Web Security Group.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b56cc233-76fd-4aa7-8071-169eafb3ffdc" />

---

### 2. DB Subnet Group

The DB subnet group was successfully created using two Availability Zones and the required subnets.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/632634d9-6694-476f-bd80-309e1cb743ee" />

---

### 3. RDS Database

The MySQL RDS instance `lab-db` was successfully created with a Multi-AZ deployment.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c5183eae-084f-4162-88e9-fec2bd0432b0" />

---

### 4. RDS Connection

The web application was configured with the RDS endpoint and database credentials.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a6b5655c-c5bb-420b-a2c6-ab56bd450f1f" />


---

### 5. Address Book Application

The web application successfully connected to the RDS database and displayed the Address Book.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d729ae96-9f62-428c-9b93-c6bc272b8a53" />

---

### 6. CRUD Operations

Contacts were successfully added, edited, and removed through the web application, confirming that the application was interacting with the RDS database.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d9c4c519-c6dd-4a3a-830c-7b398b67138b" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/caed9d61-14fe-4899-b757-da15c7f539f9" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/69f0a0be-0712-41f3-adb6-9317babf9c52" />

## Result

The **Amazon RDS MySQL database** was successfully created with **Multi-AZ high availability**. The EC2 web application was successfully connected to the RDS database through port `3306`, and CRUD operations were successfully performed using the Address Book application.

Therefore, the objective of creating an AWS-managed relational database and interacting with it through a web application was successfully achieved.
