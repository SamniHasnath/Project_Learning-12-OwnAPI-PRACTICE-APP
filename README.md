# 🏥 Elder Management System

A full-stack CRUD application for managing elder care records, built with **React**, **Express (Node.js)**, and **PostgreSQL**.

---

## 🚀 Features

- ➕ Add elder records (name, age, condition)
- 📄 View all elders
- ✏️ Update elder details (full and partial update)
- ❌ Delete records
- 🔄 REST API backed by PostgreSQL
- 🎨 Single-page React UI

---

## 🧱 Tech Stack

| Layer    | Technology                     |
| -------- | ------------------------------- |
| Frontend | React (Create React App), fetch |
| Backend  | Node.js, Express 5              |
| Database | PostgreSQL (via `pg`)           |

---

## 📁 Project Structure

```
elders-api/
├── server.js              # Express API server
├── .env                    # Backend environment variables (not committed)
├── package.json
└── elders-frontend/         # React app
    ├── src/
    │   ├── App.js           # UI + API calls
    │   ├── App.css
    │   └── index.js
    └── package.json
```

---

## ✅ Prerequisites

- [Node.js](https://nodejs.org/) v18+
- [PostgreSQL](https://www.postgresql.org/) running locally (or accessible remotely)

---

## 🗄️ Database Setup

Create the database and table:

```sql
CREATE DATABASE caresync;

\c caresync;

CREATE TABLE elders (
  id SERIAL PRIMARY KEY,
  name VARCHAR(100),
  age INT,
  condition VARCHAR(100)
);
```

---

## ⚙️ Backend Setup

From the repo root (`elders-api/`):

1. Install dependencies:

   ```bash
   npm install
   ```

2. Create a `.env` file in the repo root with your database credentials:

   ```env
   DB_HOST=localhost
   DB_USER=postgres
   DB_PASSWORD=your_password
   DB_NAME=caresync
   DB_PORT=5432
   PORT=5000
   ```

3. Start the server:

   ```bash
   node server.js
   ```

The API runs at:

```
http://localhost:5000
```

---

## 🌐 API Endpoints

Base URL: `http://localhost:5000/api/elders`

| Method | Endpoint          | Description        |
| ------ | ----------------- | ------------------- |
| GET    | `/api/elders`     | Get all elders      |
| GET    | `/api/elders/:id` | Get a single elder  |
| POST   | `/api/elders`     | Add a new elder     |
| PUT    | `/api/elders/:id` | Fully update elder  |
| PATCH  | `/api/elders/:id` | Partially update elder |
| DELETE | `/api/elders/:id` | Delete elder        |

**POST/PUT body example:**

```json
{
  "name": "John Doe",
  "age": 78,
  "condition": "Stable"
}
```

---

## 💻 Frontend Setup

From `elders-frontend/`:

```bash
cd elders-frontend
npm install
npm start
```

The app runs at:

```
http://localhost:3000
```

> The frontend calls the API at `http://localhost:5000/api/elders` (hardcoded in `src/App.js`), so make sure the backend is running first.

---

## 🔄 How It Works

```
React UI  →  fetch()  →  Express API  →  PostgreSQL  →  JSON response  →  UI update
```

---

## 📌 Notes

- Start the database and backend **before** the frontend.
- CORS is enabled on the backend, so the React dev server (port 3000) can call the API (port 5000) directly.
- The `.env` file is required for the backend to connect to PostgreSQL — do not commit it.

---

## 👨‍💻 Author

Built by [Samni Hasnath](mailto:samnihasnath@gmail.com.com) as a learning project for full-stack CRUD + REST API practice.
