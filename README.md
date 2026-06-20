# Employee Management System

## Overview

This is a Spring Boot RESTful CRUD application developed for managing employees and departments.

The project implements:
- Employee CRUD Operations
- Department CRUD Operations
- Business Logic Validations
- Filtering APIs
- Search APIs
- Transfer Employee APIs
- Global Exception Handling

---

# Tech Stack

- Java 8
- Spring Boot 2.7.x
- Spring Data JPA
- Hibernate
- MySQL 5.7
- Maven

---

# Database Setup

## Step 1: Create Database

Run the following query in MySQL:

CREATE DATABASE leadicon_tech;

---

# Configure application.properties

Update your database username and password.

properties:

spring.datasource.url=jdbc:mysql://localhost:3306/leadicon_tech

spring.datasource.username=root

spring.datasource.password=system

spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.jpa.hibernate.ddl-auto=update

spring.jpa.show-sql=true

spring.jpa.properties.hibernate.format_sql=true

server.port=8080

---

# Run the Project

1. Import project into Eclipse or IntelliJ
2. Update Maven dependencies
3. Run:
   EmpManagementApi1Application.java
4. Server runs on:
   http://localhost:8080

---

# API Endpoints

# Department APIs

## Create Department

POST /api/departments

Sample Request:

{
  "name": "IT",
  "location": "Bangalore",
  "maxCapacity": 20
}

---

## Get All Departments

GET /api/departments

---

## Get Department By Id

GET /api/departments/1

---

## Update Department

PUT /api/departments/1

Sample Request:

{
  "name": "HR",
  "location": "Mysore",
  "maxCapacity": 15
}

---

## Delete Department

DELETE /api/departments/1

---

## Get Employees By Department

GET /api/departments/1/employees

---

# Employee APIs

## Create Employee

POST /api/employees

Sample Request:

{
  "firstName": "Swapna",
  "lastName": "Nagavi",
  "email": "swapna@example.com",
  "phone": "9876543210",
  "salary": 35000,
  "status": "ON_LEAVE",
  "joinedDate": "2024-05-20",
  "departmentId": 2
}

---

## Get All Employees

GET /api/employees

---

## Filter Employees

GET /api/employees?status=ACTIVE

GET /api/employees?departmentId=1

GET /api/employees?minSalary=30000&maxSalary=80000

GET /api/employees?status=ACTIVE&departmentId=1&minSalary=30000&maxSalary=80000

---

## Get Employee By Id

GET /api/employees/1

---

## Update Employee

PUT /api/employees/1

---

## Change Employee Status

PATCH /api/employees/1/status?status=ON_LEAVE

---

## Delete Employee

DELETE /api/employees/1

---

## Search Employee By Name

GET /api/employees/search?name=swapna

---

## Transfer Employee

PUT /api/employees/1/transfer/2

---

# Business Rules Implemented

- Unique employee email validation
- Unique department name validation
- Salary validation
- Salary hike validation
- Department capacity validation
- Future joined date restriction
- INACTIVE employee transfer restriction
- Cannot delete department with employees
- Filtering logic with multiple conditions

---

# Exception Handling

Global exception handling implemented using:

@ControllerAdvice

Standard JSON error response:

{
  "timestamp": "2026-05-27T10:30:00",
  "status": 400,
  "error": "Bad Request",
  "message": "Department has reached its maximum capacity.",
  "path": "/api/employees"
}

---

# Project Structure

src/main/java/com/empmanagement/ems/

├── controller

├── service

├── repository

├── entity

├── dto

├── exception

└── EmpManagementApi1Application.java
