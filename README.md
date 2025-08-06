# Department-Course-Subquery-and-Access-Control
✅ Overview
This SQL practice involves designing, normalizing, and interacting with a small academic database that manages departments and the courses they offer. The task is divided into four parts: schema creation, data insertion, subquery usage, and access control.

🔹 Part A: Create Department and Course Tables (Normalized to 3NF)
Departments Table

dept_id (Primary Key)

dept_name (Unique, VARCHAR)

Courses Table

course_id (Primary Key)

course_name (VARCHAR)

dept_id (Foreign Key referencing Departments)

Goal: Ensure that:

Each course belongs to exactly one department.

Department names are not duplicated.

Data model is in Third Normal Form (3NF).

🔹 Part B: Insert Sample Data
Insert at least 5 departments with names like:

"Computer Science", "Electrical", "Mechanical", "Civil", "Electronics"

Insert at least 10 courses with names like:

"DBMS", "Operating Systems", "Power Systems", etc.

Ensure: Each department has at least two courses linked via dept_id.

🔹 Part C: Retrieve Departments Offering More Than Two Courses
Use a subquery with GROUP BY and HAVING to identify departments with more than 2 courses.

📌 Sample Query:
sql
Copy code
SELECT dept_name
FROM Departments
WHERE dept_id IN (
    SELECT dept_id
    FROM Courses
    GROUP BY dept_id
    HAVING COUNT(*) > 2
);
🔹 Part D: Grant SELECT Access Using DCL
Allow a user named viewer_user to only read (SELECT) data from the Courses table.

📌 DCL Command:
sql
Copy code
GRANT SELECT ON your_database_name.Courses TO 'viewer_user'@'localhost';
Replace your_database_name with the name of your actual database.

🛠️ Setup Instructions
Open your MySQL/MariaDB client (e.g., MySQL CLI, phpMyAdmin, MySQL Workbench).

Run the full SQL script provided to:

Drop existing tables (if any)

Create and populate tables

Perform the subquery

Grant access to user

(Optional) Create the user using:

sql
Copy code
CREATE USER 'viewer_user'@'localhost' IDENTIFIED BY 'password';
📂 File Structure (If you're using files)
pgsql
Copy code
.
├── setup.sql         -- Full SQL script (all parts)
├── README.md         -- Project instructions (this file)
🧠 Learning Objectives
Practice data modeling using 3NF

Implement foreign key constraints

Write aggregate subqueries with GROUP BY and HAVING

Use DCL (GRANT) to control data access

