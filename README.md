# 📘 Department-Course-Subquery-and-Access-Control

This SQL project involves creating a normalized academic database schema to manage departments and the courses they offer. It includes sample data insertion, a subquery to extract specific insights, and a Data Control Language (DCL) command to restrict data access.

## 📂 Project Structure

/Department-Course-Subquery-and-Access-Control
├── department_course.sql # Complete SQL script (Tables, Data, Subquery, DCL)
├── README.md # Project documentation

## ✅ Overview

### 🔹 Part A: Create Tables with Normalization (3NF)

Defines two normalized tables:

#### 🗃️ Departments
- `dept_id` (INT, Primary Key)
- `dept_name` (VARCHAR(50), Unique)

#### 📘 Courses
- `course_id` (INT, Primary Key)
- `course_name` (VARCHAR(100))
- `dept_id` (INT, Foreign Key referencing Departments)

> ✅ Each course belongs to exactly one department  
> ✅ Department names are unique  
> ✅ Data model follows **Third Normal Form (3NF)**


### 🔹 Part B: Insert Sample Data

Inserts:
- **5 departments**: Computer Science, Electrical, Mechanical, Civil, Electronics
- **10 courses**: 2 per department (e.g., DBMS, Power Systems, Thermodynamics, etc.)

> 🔗 All courses are properly linked to their departments using foreign keys.


### 🔹 Part C: Subquery — Departments Offering More Than 2 Courses

Retrieves names of departments that offer **more than two courses** using a `GROUP BY` and `HAVING` clause inside a subquery.


#### ✅ Query:
SELECT dept_name
FROM Departments
WHERE dept_id IN (
    SELECT dept_id
    FROM Courses
    GROUP BY dept_id
    HAVING COUNT(course_id) > 2
);


🔹 Part D: Grant SELECT Access (DCL)
Grants read-only access on the Courses table to a user named viewer_user.

✅ Command:
GRANT SELECT ON your_database_name.Courses TO 'viewer_user'@'localhost';
🔐 Replace your_database_name with your actual DB name.


🚀 How to Run
Open MySQL CLI or GUI (MySQL Workbench, phpMyAdmin, etc.).

Execute the contents of department_course.sql.

(Optional) Create the user if not already done:
CREATE USER 'viewer_user'@'localhost' IDENTIFIED BY 'password';


🧠 Learning Objectives:

✅ Database Normalization (3NF)

✅ Foreign Key Relationships

✅ Aggregate Subqueries

✅ Data Control Language (DCL) – GRANT

✅ Unique Constraints

✅ Relational Schema Design


