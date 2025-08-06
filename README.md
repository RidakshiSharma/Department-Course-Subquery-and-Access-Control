# 📚 Department-Course-Subquery-and-Access-Control
This SQL project demonstrates how to design a normalized academic database with departments and their offered courses, retrieve data using subqueries, and control data access using DCL.

## ✅ Project Parts

### 🔹 Part A: Create Tables with 3NF Normalization

**Tables:**

- `Departments`
  - `dept_id` (INT, Primary Key)
  - `dept_name` (VARCHAR, Unique)
- `Courses`
  - `course_id` (INT, Primary Key)
  - `course_name` (VARCHAR)
  - `dept_id` (Foreign Key → Departments)

> Ensures each course is linked to exactly one department and avoids duplicate department names.

---

### 🔹 Part B: Insert Sample Data

- Adds **5 departments**:
  - Computer Science, Electrical, Mechanical, Civil, Electronics
- Adds **10+ courses**, at least **2 per department**.

> Example: DBMS, Operating Systems, Power Systems, Thermodynamics, etc.

---

### 🔹 Part C: Retrieve Departments Offering More Than 2 Courses

Uses a subquery to list department names with more than two courses:

```sql
SELECT dept_name
FROM Departments
WHERE dept_id IN (
    SELECT dept_id
    FROM Courses
    GROUP BY dept_id
    HAVING COUNT(course_id) > 2
);

🔹 Part D: Grant SELECT Access on Courses Table
Grants read-only access to the Courses table for a user named viewer_user:


sql
Copy code
GRANT SELECT ON your_database_name.Courses TO 'viewer_user'@'localhost';
Replace your_database_name with the actual name of your database.


🛠️ How to Run
Open your MySQL CLI or GUI (phpMyAdmin, MySQL Workbench).

Run the SQL script:

Drop existing tables (if any)

Create Departments and Courses tables

Insert sample data

Execute the subquery

Grant SELECT access to viewer_user

(Optional) Create the user with:

sql
Copy code
CREATE USER 'viewer_user'@'localhost' IDENTIFIED BY 'password';


📂 File Structure
pgsql
Copy code
/Department-Course-Subquery-and-Access-Control
├── department_course.sql      # Full SQL script with all parts (A–D)
├── README.md                  # Project documentation


🧠 Learning Objectives
Database normalization (3NF)

Foreign key constraints

Aggregate subqueries using GROUP BY and HAVING

SQL DCL commands (GRANT)

Secure and structured database design
