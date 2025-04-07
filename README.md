# CreditSea Backend

A Node.js + TypeScript backend for managing loan applications with role-based access control (User, Verifier, Admin). Built using Express.js, Sequelize ORM, and PostgreSQL.

## 🚀 Features

- JWT-based authentication with cookies  
- Role-based access control (RBAC)  
- Secure PostgreSQL connection (Aiven-compatible)  
- Sequelize ORM with migrations and models  
- Loan application submission, verification, approval, and rejection  

## 🛠 Tech Stack

- Node.js  
- TypeScript  
- Express.js  
- PostgreSQL (hosted on Aiven)  
- Sequelize ORM  
- dotenv  
- bcrypt  
- JSON Web Tokens (JWT)  

## 📁 Project Structure

```
src/
├── config/
├── controllers/
├── middleware/
├── models/
├── routes/
├── utils/
└── server.ts
```

## 🔐 Environment Variables

Create a `.env` file in the root directory with the following content:

```env
DB_NAME=loan_db
DB_USER=avnadmin
DB_PASSWORD=your_password
DB_HOST=your_host_url
DB_PORT=14720
JWT_SECRET=your_jwt_secret
```

## 🧪 Setup Instructions

1. **Clone the repository:**

```bash
git clone https://github.com/your-username/CreditSea_Backend.git
cd CreditSea_Backend
```

2. **Install dependencies:**

```bash
npm install
```

3. **Configure the environment variables** in a `.env` file as shown above.

4. **Run the development server:**

```bash
npm run dev
```

## 🗄 Database

To import data from a SQL dump:

```bash
psql "postgres://avnadmin:your_password@your_host:14720/loan_db?sslmode=require" --file=cleaned-data.sql
```

> Ensure that the database schema (tables) exists before running the SQL inserts.

## 📡 API Routes

### 🧑 Public Routes

| Method | Endpoint   | Description         |
|--------|------------|---------------------|
| POST   | /register  | Register a new user |
| POST   | /login     | Log in a user       |
| GET    | /logout    | Log out the session |

### 👤 User Routes

| Method | Endpoint     | Description                  |
|--------|--------------|------------------------------|
| GET    | /user        | Get user dashboard           |
| POST   | /user/form   | Submit loan application      |

### ✅ Verifier Routes

| Method | Endpoint                | Description                     |
|--------|-------------------------|---------------------------------|
| GET    | /verifier               | Get verifier dashboard          |
| PUT    | /verifier/update-status | Approve/Reject loan application |

> 🔸 Note: Admins can also use `/verifier/update-status` to approve or reject applications.

### 🛡️ Admin Routes

| Method | Endpoint            | Description           |
|--------|---------------------|-----------------------|
| GET    | /admin              | Get admin dashboard   |
| GET    | /admin/users        | View all users        |
| PUT    | /admin/users/update | Update a user's role  |
