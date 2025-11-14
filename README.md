# SpringHibernateApps

**Complete Spring & Hibernate Java Applications** - Dependency Injection, CRUD Operations, and Transaction Management System

## 📋 Overview

This repository contains three independent Java modules demonstrating core Spring and Hibernate concepts:

1. **Part A**: Spring Dependency Injection using Java Configuration
2. **Part B**: Hibernate CRUD Operations with MySQL
3. **Part C**: Spring + Hibernate Transaction Management System

## 🛠 Technology Stack

- **Java**: 8 or higher
- **Spring Framework**: 5.3.x
- **Hibernate**: 5.6.x
- **MySQL**: 8.0
- **Maven**: 3.6+

## 📁 Repository Structure

```
SpringHibernateApps/
├── PartA_SpringDI/
│   ├── src/main/java/com/example/di/
│   │   ├── AppConfig.java
│   │   ├── Course.java
│   │   ├── Student.java
│   │   └── MainApp.java
│   ├── pom.xml
│   └── README.md
│
├── PartB_HibernateCRUD/
│   ├── src/main/java/com/example/hibernate/
│   │   ├── Student.java
│   │   ├── HibernateUtil.java
│   │   ├── StudentDAO.java
│   │   └── MainApp.java
│   ├── src/main/resources/
│   │   └── hibernate.cfg.xml
│   ├── student.sql
│   ├── pom.xml
│   └── README.md
│
├── PartC_SpringHibernateTransaction/
│   ├── src/main/java/com/example/bank/
│   │   ├── config/AppConfig.java
│   │   ├── entity/Account.java
│   │   ├── entity/Transaction.java
│   │   ├── dao/AccountDAO.java
│   │   ├── service/BankService.java
│   │   ├── service/BankServiceImpl.java
│   │   └── MainApp.java
│   ├── src/main/resources/
│   │   └── hibernate.cfg.xml
│   ├── bank.sql
│   ├── pom.xml
│   └── README.md
│
└── README.md
```

## 🚀 Quick Start

### Prerequisites

1. **Install Java JDK 8+**
   ```bash
   java -version
   ```

2. **Install Maven**
   ```bash
   mvn -version
   ```

3. **Install MySQL**
   - Download from: https://dev.mysql.com/downloads/
   - Start MySQL service

### Database Setup

```sql
-- Create databases
CREATE DATABASE IF NOT EXISTS studentdb;
CREATE DATABASE IF NOT EXISTS bankdb;

-- Verify creation
SHOW DATABASES;
```

## 📦 Part A: Spring Dependency Injection

### Description
Demonstrates Spring DI using Java Configuration with Student and Course beans.

### Run Instructions

```bash
cd PartA_SpringDI
mvn clean compile
mvn exec:java -Dexec.mainClass="com.example.di.MainApp"
```

### Expected Output
```
Student: John Doe, Email: john@example.com
Enrolled Course: Course{courseName='Java Spring Framework', duration=40 hours}
```

### Key Files
- **AppConfig.java**: Spring configuration with @Bean definitions
- **Course.java**: Course model class
- **Student.java**: Student class with Course dependency
- **MainApp.java**: Application entry point

---

## 📦 Part B: Hibernate CRUD Operations

### Description
Complete CRUD operations using Hibernate ORM with MySQL database.

### Database Setup

```bash
cd PartB_HibernateCRUD
mysql -u root -p < student.sql
```

### Run Instructions

```bash
mvn clean compile
mvn exec:java -Dexec.mainClass="com.example.hibernate.MainApp"
```

### Expected Output
```
=== Adding Students ===
Student added with ID: 1
Student added with ID: 2

=== Retrieving Student ===
Student{id=1, name='Alice Johnson', email='alice@example.com', age=20}

=== Updating Student ===
Student updated successfully!

=== All Students ===
Student{id=1, name='Alice Johnson', email='alice.updated@example.com', age=21}
Student{id=2, name='Bob Smith', email='bob@example.com', age=22}

=== Deleting Student ===
Student deleted successfully!
```

### Key Files
- **Student.java**: Entity class with JPA annotations
- **HibernateUtil.java**: SessionFactory configuration
- **StudentDAO.java**: Data Access Object with CRUD methods
- **MainApp.java**: Demonstrates all CRUD operations
- **hibernate.cfg.xml**: Hibernate configuration
- **student.sql**: Database schema

---

## 📦 Part C: Spring + Hibernate Transaction Management

### Description
Bank transaction system with Spring declarative transaction management using @Transactional.

### Features
- Money transfer between accounts
- Automatic rollback on errors
- Transaction logging
- Declarative transaction management

### Database Setup

```bash
cd PartC_SpringHibernateTransaction
mysql -u root -p < bank.sql
```

### Run Instructions

```bash
mvn clean compile
mvn exec:java -Dexec.mainClass="com.example.bank.MainApp"
```

### Expected Output
```
=== Initial Account Balances ===
Account{id=1, accountNumber='ACC001', accountHolder='Alice', balance=5000.0}
Account{id=2, accountNumber='ACC002', accountHolder='Bob', balance=3000.0}

=== Performing Transfer: Alice -> Bob: $500 ===
Transfer successful!

=== Updated Account Balances ===
Account{id=1, accountNumber='ACC001', accountHolder='Alice', balance=4500.0}
Account{id=2, accountNumber='ACC002', accountHolder='Bob', balance=3500.0}

=== Transaction History ===
Transaction{id=1, fromAccount='ACC001', toAccount='ACC002', amount=500.0, timestamp=...}

=== Testing Rollback (Insufficient Funds) ===
Error: Insufficient funds
Rollback successful - balances unchanged
```

### Key Files
- **AppConfig.java**: Spring configuration with transaction management
- **Account.java**: Account entity
- **Transaction.java**: Transaction log entity
- **AccountDAO.java**: Data access layer
- **BankService.java**: Service interface
- **BankServiceImpl.java**: Service implementation with @Transactional
- **MainApp.java**: Demonstrates transactions and rollback
- **bank.sql**: Database schema with sample data

---

## 📝 Complete Code Listings

For complete code of all files, please see the individual module README files:
- [Part A README](./PartA_SpringDI/README.md)
- [Part B README](./PartB_HibernateCRUD/README.md)
- [Part C README](./PartC_SpringHibernateTransaction/README.md)

## 🔧 Configuration Notes

### MySQL Connection Settings

Update the following in configuration files based on your MySQL setup:

```xml
<property name="hibernate.connection.username">root</property>
<property name="hibernate.connection.password">your_password</property>
<property name="hibernate.connection.url">jdbc:mysql://localhost:3306/dbname</property>
```

### Common Issues & Solutions

**Issue**: `ClassNotFoundException: com.mysql.cj.jdbc.Driver`
**Solution**: Ensure MySQL connector dependency is in pom.xml

**Issue**: `Access denied for user 'root'@'localhost'`
**Solution**: Update MySQL username/password in hibernate.cfg.xml

**Issue**: `Unknown database`
**Solution**: Run the SQL scripts to create databases first

**Issue**: `mvn: command not found`
**Solution**: Install Maven and add to system PATH

## 📚 Learning Objectives

### Part A
- ✅ Spring IoC Container
- ✅ Java-based Configuration
- ✅ Dependency Injection
- ✅ Bean lifecycle

### Part B
- ✅ Hibernate ORM basics
- ✅ Entity mapping
- ✅ SessionFactory configuration
- ✅ CRUD operations
- ✅ HQL queries

### Part C
- ✅ Spring Transaction Management
- ✅ @Transactional annotation
- ✅ Declarative transactions
- ✅ Rollback handling
- ✅ Integration of Spring + Hibernate

## 🎯 Key Concepts Demonstrated

1. **Dependency Injection**: Loose coupling through Spring IoC
2. **ORM Mapping**: Object-Relational mapping with Hibernate
3. **Transaction Management**: ACID properties with automatic rollback
4. **DAO Pattern**: Separation of data access logic
5. **Configuration Management**: XML and Java-based configuration

## 🤝 Contributing

Feel free to fork this repository and submit pull requests for improvements!

## 📄 License

This project is open source and available for educational purposes.

## 📧 Contact

For questions or suggestions, please open an issue in this repository.

---

**Note**: Each module is independent and can be run separately. Make sure to set up the required databases before running Part B and Part C.

## 🎓 Next Steps

1. Clone this repository
2. Set up MySQL databases
3. Navigate to each module directory
4. Follow the individual README instructions
5. Run and explore the code!

Happy Learning! 🚀
