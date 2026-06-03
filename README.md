# FIX-ITZUT
a student maintenance system that provides a plattform for reports of vandalism, iregularities and all defects in terms of the school infrasctrucutre
# 🛠️ FixIt ZUT: Campus Maintenance Reporting System

**Student Name:** [Your Full Name]  
**Student Number:** [Your Student Number]  
**Course:** Full-Stack Web Development  
**Institution:** Zambia University of Technology (ZUT)  
**Date:** [Current Date]  

---

## 📌 1. Problem Statement
Within the university environment, reporting campus maintenance issues (e.g., broken furniture, electrical faults, plumbing leaks, or damaged lab equipment) is often informal, untracked, and chaotic. This leads to delayed repairs, miscommunication, and frustrated students and staff.

## 💡 2. Proposed Solution
**FixIt ZUT** is a centralized, full-stack web application that streamlines the maintenance reporting process. It allows students to easily report campus issues by submitting a description, location, and photographic evidence. Maintenance administrators can view these reports in a dashboard, update their status (Pending → In Progress → Resolved), and manage the workflow efficiently.

## ✅ 3. Assignment Requirements Met
This project successfully demonstrates all core concepts covered in the Full-Stack Web Development module:
- [x] **User Authentication & Login:** Secure registration and login using JWT (JSON Web Tokens) and `bcryptjs` for password hashing.
- [x] **CRUD Operations:** Full Create, Read, Update, and Delete functionality for maintenance reports.
- [x] **Database Integration:** PostgreSQL used for robust, relational data management (Users and Reports tables).
- [x] **API Development:** RESTful API built with Node.js and Express.js.
- [x] **File Upload Functionality:** Implemented using `multer` to handle image uploads, storing files securely and saving paths in the database.
- [x] **Responsive Frontend:** Built with React.js and Tailwind CSS, ensuring a seamless experience on both desktop and mobile devices (crucial for on-the-go reporting).

## 🛠️ 4. Technology Stack
- **Frontend:** React.js (Vite), React Router DOM, Axios, Tailwind CSS
- **Backend:** Node.js, Express.js
- **Database:** PostgreSQL
- **Utilities:** `multer` (file uploads), `bcryptjs` (encryption), `jsonwebtoken` (auth), `dotenv` (environment variables), `cors`

---

## 🚀 5. Installation & Setup Instructions

### Prerequisites
- Node.js and npm installed on your machine.
- PostgreSQL installed and running (e.g., via pgAdmin).

### Step 1: Database Setup
1. Open pgAdmin or your PostgreSQL terminal.
2. Create a new database named `zut_maintenance`.
3. Run the following SQL commands to create the required tables:
   ```sql
   CREATE TABLE users (
       id SERIAL PRIMARY KEY,
       name VARCHAR(100) NOT NULL,
       email VARCHAR(100) UNIQUE NOT NULL,
       password VARCHAR(255) NOT NULL,
       role VARCHAR(20) DEFAULT 'student',
       created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );

   CREATE TABLE reports (
       id SERIAL PRIMARY KEY,
       title VARCHAR(150) NOT NULL,
       description TEXT NOT NULL,
       location VARCHAR(150) NOT NULL,
       image_url VARCHAR(255),
       status VARCHAR(50) DEFAULT 'Pending',
       user_id INT REFERENCES users(id) ON DELETE CASCADE,
       created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );
