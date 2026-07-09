<div align="center">
  <img width="120px" src="main/static/images/hrs-logo-blue.png" alt="HR System Logo"/>
  <h1>HR System</h1>
  <p><i>A comprehensive Human Resources management application built with Python and Flask.</i></p>
</div>

---

## 📖 Overview
The **HR System** is a robust demonstration of a modern human resources web application. It is designed to manage users, job postings, payroll, and infrastructure tracking while strictly enforcing Role-Based Access Control (RBAC).

The application's architecture leverages:
- **Frontend**: Crafted using `Jinja` templates and `Bootstrap` to provide a dynamic, responsive, and seamless user experience.
- **Backend**: Developed with `Python` and the `Flask` framework.
- **Database**: Uses `PostgreSQL` with `SQLAlchemy` ORM for structured and secure CRUD operations defined in `/main/models`.

---

## ⚡ Key Features

* **Role-Based Access Control (RBAC)**: Create and assign custom roles (e.g., Admin, HR, Manager, Employee) to strictly control access to different modules.
* **Job Portal**: Publicly accessible job postings where candidates can register, apply, and track their application status.
* **Project & Employee Management**: Admins can onboard employees, create projects, and assign employees to specific projects.
* **Managerial Tools**: Managers can view project allocations, approve or reject vacation requests, and reassign employees.
* **Payroll Processing**: The HR department can manage individual payrolls and automatically generate month-end payouts.
* **Infrastructure Tracking**: Admins can reliably track and manage company assets and infrastructure assigned to employees.

---

## 🛠️ Language & Tools

<p align="center">
  <img width="45px" style="padding:10px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" title="Python"/>
  <img width="45px" style="padding:10px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/flask/flask-original.svg" title="Flask"/>
  <img width="45px" style="padding:10px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/postgresql/postgresql-original.svg" title="PostgreSQL"/>
  <img width="45px" style="padding:10px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/bootstrap/bootstrap-original.svg" title="Bootstrap"/>
  <img width="45px" style="padding:10px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/sqlalchemy/sqlalchemy-original.svg" title="SQLAlchemy"/>
</p>

---

## 🐳 Running with Podman

This project is fully containerized for a smooth, reproducible deployment using **Podman** and `podman-compose`.

### Prerequisites
- Install [Podman](https://podman.io/) and `podman-compose`.

### Setup Instructions

1. **Clone the repository** and navigate to the project root directory.
2. **Build and start the containers** using the following command. This will pull the PostgreSQL database and build the Flask application running on Python 3.11:
   ```bash
   podman-compose up -d --build
   ```
3. **Initialize the Database**: 
   Once the containers are running (`hr-app` and `postgres-db`), open your browser and navigate to the initialization endpoint. This automatically creates the required database schemas and populates the default user profiles:
   👉 **[http://localhost:5000/createDatabase](http://localhost:5000/createDatabase)**
4. **Log into the Application**:
   Go to the application homepage at [http://localhost:5000/](http://localhost:5000/) and log in with the default administrator credentials:
   - **Username**: `admin`
   - **Password**: `admin`

<details>
<summary><b>Recent Deployment Updates (Click to Expand)</b></summary>
<br>

- **Python Version**: The container base image was downgraded to `python:3.11-slim` to ensure C-extension compilation compatibility for older dependencies like `psycopg2` and `greenlet`.
- **Package execution**: The Flask application correctly initializes as a module package, executed via Gunicorn using `main.app:app` to prevent relative import errors.
- **Registry Configuration**: The PostgreSQL database uses the fully qualified registry address (`docker.io/library/postgres:15-alpine`) to prevent Podman short-name resolution errors.
</details>

---

## 📸 Screenshots

<details open>
<summary><b>Application Previews</b></summary>
<br>

*Login Page*
<img align="center" style="padding-top:5px; padding-bottom:15px;" src="images/loginPage.png"/>

*Admin Dashboard*
<img align="center" style="padding-top:5px; padding-bottom:15px;" src="images/adminPage.png"/>

*Job Listings*
<img align="center" style="padding-top:5px; padding-bottom:15px;" src="images/jobListingPage.png"/>

*Candidate Registration*
<img align="center" style="padding-top:5px; padding-bottom:15px;" src="images/candidateSignUpPage.png"/>

*Project Management*
<img align="center" style="padding-top:5px; padding-bottom:15px;" src="images/projectsPage.png"/>

*Employee Daily Status*
<img align="center" style="padding-top:5px; padding-bottom:15px;" src="images/employeeDailyStatusPage.png"/>

</details>