# CreditSea Backend

A Node.js + TypeScript backend for managing loan applications with role-based access (User, Verifier, Admin). Built using Express.js, Sequelize ORM, and PostgreSQL.

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
- Dotenv
- Bcrypt
- JSON Web Tokens (JWT)

## 📁 Project Structure

CreditSea_Backend/ ├── src/ │ ├── config/ # Sequelize setup │ ├── controllers/ # Route handlers │ ├── middleware/ # Auth, role guards │ ├── models/ # Sequelize models │ ├── routes/ # API endpoints │ ├── types/ # Custom TypeScript types │ └── index.ts # Entry point ├── .env ├── package.json └── tsconfig.json

makefile
Copy
Edit

## 🔐 Environment Variables

Create a `.env` file at the root with:

```env
DB_NAME=loan_db
DB_USER=avnadmin
DB_PASSWORD=your_password
DB_HOST=your_host_url
DB_PORT=14720
JWT_SECRET=your_jwt_secret
🧪 Setup Instructions
Clone the repository:

bash
Copy
Edit
git clone https://github.com/your-username/CreditSea_Backend.git
cd CreditSea_Backend
Install dependencies:

bash
Copy
Edit
npm install
Configure environment variables in .env as shown above.

Run the development server:

bash
Copy
Edit
npm run dev
🗄 Database
To import data from a SQL dump:

bash
Copy
Edit
psql "postgres://avnadmin:your_password@your_host:14720/loan_db?sslmode=require" --file=cleaned-data.sql
Make sure the tables are created before running the SQL inserts.

🧑‍💻 API Overview
POST /api/register – Register new users

POST /api/login – Login and receive cookie JWT

GET /api/me – Get current logged-in user

POST /api/loan/apply – Apply for a loan (User)

GET /api/loan/all – View all loan applications (Admin/Verifier)

POST /api/loan/:id/verify – Verify a loan (Verifier)

POST /api/loan/:id/approve – Approve a loan (Admin)

POST /api/loan/:id/reject – Reject a loan (Admin)