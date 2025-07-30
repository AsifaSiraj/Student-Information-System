Perfect 👍 Let’s create a **detailed GitHub README.md** for your project.

Here’s a professional, structured **README** that explains your **Student Information System with roles (Admin, Teacher, Student), course management, registrations, and dashboards**.

---

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


