# 📚 Student Information System

A role-based **Student Information System (SIS)** built with **PHP, MySQL, HTML, CSS, and FontAwesome**.
This project provides **three roles (Admin, Teacher, Student)** with dedicated dashboards, course/department management, student registrations, and statistics.

---

## 🚀 Features

### 🔹 Admin Panel

* ✅ Manage Students (CRUD)
* ✅ Manage Teachers (CRUD)
* ✅ Manage Departments (CRUD)
* ✅ Manage Courses (CRUD)

  * Assign teacher **optional** when creating a course
  * Teacher can self-register in unassigned courses
  * Once a teacher is assigned, only admin can reassign
* ✅ Register Students in Courses

  * Prevents duplicate registrations
  * **Unregister students** (only admin can perform this action)
* ✅ View all course, teacher, and student records in a clean dashboard

---

### 🔹 Teacher Dashboard

* ✅ View personal profile & assigned courses
* ✅ Self-register in **available (unassigned)** courses
* ✅ View **total students** across all their courses
* ✅ See **enrolled student names** for each course
* ❌ Cannot unregister students (restricted to admin)

---

### 🔹 Student Dashboard

* ✅ View profile and enrolled courses
* ✅ View announcements/notifications
* ✅ Statistics cards for quick overview
* ✅ Clean UI with responsive sidebar and modern design

---

## 🏗️ Tech Stack

* **Frontend:** HTML, CSS, JavaScript (Vanilla)
* **Styling:** Custom CSS (Dashboard-style, Sidebar, Cards, Tables)
* **Icons:** [Font Awesome](https://fontawesome.com/)
* **Backend:** PHP (Procedural)
* **Database:** MySQL

## ⚙️ Installation Guide

1. Clone the repository

   ```bash
   git clone https://github.com/AsifaSiraj/Student-Information-System.git
   cd student-information-system
   ```

2. Import the database

   * Open **phpMyAdmin** or MySQL CLI
   * Create a new database:

     ```sql
     CREATE DATABASE sis_db;
     ```
   * Import the provided `sis_db.sql` file

3. Configure database connection

   * Open `config/db.php`
   * Update credentials:

     ```php
     $conn = new mysqli("localhost", "root", "", "sis_db");
     ```

4. Start server

   * Place project in `htdocs/` (XAMPP) or `www/` (WAMP)
   * Run Apache + MySQL
   * Visit: [http://localhost/Student-Information-System](http://localhost/Student-Information-System)

---

## 🔐 Default Credentials

| Role    | Username | Password |
| ------- | -------- | -------- |
| Admin   | admin    | admin123 |
| Teacher | T1@gmail.com | teacher123  |
| Student | S1@gmail.com | student123  |

# 🔒 System-Level Restrictions

This project enforces strict rules at **system**, **database**, and **application** levels to ensure **security** and **consistency**.

## 1. Role-Based Access Control

### Admin
- Add, edit, and delete students, teachers, departments, and courses
- Register/unregister students in courses
- Reassign teachers to courses

### Teacher
- Can self-assign to unassigned courses
- Cannot reassign once a course already has a teacher
- Cannot add/edit/delete students or departments

### Student
- Can only view their own courses and registrations
- Cannot self-register (unless extended in future)
- Unauthorized access redirects to login (`index.html`)

## 2. Database-Level Restrictions

### Students Table
- `id` → Auto Increment Primary Key
- `email` → UNIQUE, NOT NULL
- `roll_no` → UNIQUE, NOT NULL
- `department_id` → Foreign Key (must exist in departments)
- `password` → NOT NULL

### Teachers Table
- `id` → Auto Increment Primary Key
- `email` → UNIQUE, NOT NULL

### Courses Table
- `teacher_id` → Nullable (course may be unassigned)
- Once a teacher assigns themselves → only admin can reassign

### Registrations Table
- Combination of `student_id + course_id` must be unique
- Prevents duplicate registrations
- `registered_by` field tracks whether Admin or Student registered

## 3. Application/Form Restrictions

### Student Form
- Name, Email, Roll No, Department → required
- Email must be valid format
- Password required on add, optional on update

### Course Form
- Course Name and Code → required
- Department → required
- Teacher assignment → optional

### Delete Operations
- Confirmation prompt required before deletion

### Teacher Dashboard
- Teacher can register themselves only in unassigned courses
- Teacher cannot unregister or delete courses

## 4. Session & Security Restrictions
- Every page checks `$_SESSION['role']` to confirm access rights
- Direct URL access without a valid session → redirects to login
- Prevents role escalation (e.g., student pretending to be admin)
- Teacher self-assign actions are logged in `teacher_course_logs`

## 5. Business Logic Restrictions
- Teacher assignment is not mandatory for admin when creating a course
- Only admin can unregister a student from a course
- Duplicate prevention:
  - Students cannot be added with duplicate email or roll number
  - Students cannot be registered in the same course more than once
- Teacher self-registrations are logged (audit trail)

## 6. Error Handling Restrictions
- Database errors (duplicate email/roll, invalid foreign keys) prevent insertion
- By default, user is redirected without error feedback (extendable)
- Delete/Update operations fail silently if invalid ID is provided (extendable with error reporting)
By default, user is redirected without error feedback (extendable).

Delete/Update operations fail silently if invalid ID is provided (extendable with error reporting).

