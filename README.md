# Smart Personal Finance & Investment Tracker

A full-stack Personal Finance and Investment Management platform built with Spring Boot 3, PostgreSQL, React, and Vite. FinTrack provides financial health scoring, expense tracking, categorized budgets, savings goals, investment portfolio monitoring, and rule-based financial advisory recommendations.

---

## 🛠️ Tech Stack

- **Frontend:** React 19, Vite 8, React Router v7, Vanilla CSS
- **Backend:** Java 21, Spring Boot 3.2.0, Spring Data JPA, Spring Security 6
- **Database:** PostgreSQL (with HikariCP connection pooling)
- **Authentication & Security:** JSON Web Token (JWT) + BCrypt password hashing + stateless session management
- **Documentation:** SpringDoc OpenAPI 3 / Swagger UI

---

## 🌟 Key Features

1. **Authentication & User Management:**
   - Registration and Login with BCrypt encryption.
   - Stateless JWT tokens stored securely on the frontend and validated with Spring Security filters.
   - Profile management and password updates.

2. **Dashboard & Financial Health Score:**
   - Real-time income, expense, and portfolio balance aggregation.
   - Automated financial health scoring algorithm (0-100) based on savings rate, emergency surplus, and budget adherence.
   - 6-month comparative cash flow breakdown.

3. **Transactions Management:**
   - Full CRUD support with categorization (`FOOD`, `SHOPPING`, `TRANSPORT`, `BILLS`, `ENTERTAINMENT`, `SALARY`, etc.).
   - Support for payment methods (`UPI`, `CASH`, `CREDIT_CARD`, `DEBIT_CARD`, `NET_BANKING`).
   - Dynamic filtering by search keyword, transaction type, and category.

4. **Budgets & Alerts:**
   - Monthly category spending targets.
   - Automated calculation of spent amounts and remaining balances.
   - Visual alerts when categories approach 80% or exceed 100% of the allocated budget.

5. **Savings Goals:**
   - Goal definition with target amount, current savings, and target deadline.
   - Percentage progress tracking and real-time top-up updates.
   - Rule-based savings recommendations derived from income-to-spending ratios.

6. **Investment Portfolio & Advisory:**
   - Investment tracking across Stocks, Mutual Funds, Fixed Deposits, Gold, Crypto, and Bonds.
   - Real-time profit/loss and return percentage metrics.
   - Built-in Investment Advisor delivering risk-adjusted asset allocation advice.

7. **Analytics & Reports:**
   - Monthly income vs. expenses trend curves.
   - Category spending percentage distribution.
   - Monthly savings trajectory.

---

## 📋 Prerequisites

- **Java Development Kit (JDK):** Version 21 or later
- **Node.js:** Version 18+ (Node 20+ recommended) & npm
- **PostgreSQL:** Version 14 or later running on port 5432
- **Maven:** Bundled via `mvnw.cmd` / `mvnw` wrapper

---

## ⚙️ Configuration & Environment Variables

### Backend Configuration (`backend/src/main/resources/application.yml`)
The backend is pre-configured with sensible defaults and environment variable overrides:

| Variable | Default Value | Description |
|---|---|---|
| `DB_URL` / `DATABASE_URL` | `jdbc:postgresql://localhost:5432/finance_tracker` | PostgreSQL JDBC connection URL |
| `DB_USERNAME` / `DATABASE_USERNAME` | `postgres` | Database username |
| `DB_PASSWORD` / `DATABASE_PASSWORD` | `zoya8440` (or your local password) | Database user password |
| `JWT_SECRET` | *Pre-configured secure 256-bit key* | Secret key for JWT signing |
| `PORT` / `server.port` | `8080` | Spring Boot server port |

To customize credentials without modifying code, set environment variables prior to launch:
```powershell
$env:DB_PASSWORD = "your_postgres_password"
$env:JWT_SECRET = "your_custom_base64_secret_key"
```

### PostgreSQL Setup
Ensure your local PostgreSQL instance is running and the database exists:
```sql
CREATE DATABASE finance_tracker;
```

---

## 🚀 Running the Application

### 1. Start the Backend
Open a PowerShell terminal in the `backend` directory:
```powershell
cd backend
$env:JAVA_HOME = "C:\Program Files\Java\jdk-21.0.11" # (adjust if your JDK path differs)
.\mvnw.cmd spring-boot:run
```
*Backend will start on: [http://localhost:8080](http://localhost:8080)*  
*Swagger Documentation: [http://localhost:8080/swagger-ui.html](http://localhost:8080/swagger-ui.html)*

### 2. Start the Frontend
Open a separate terminal in the `frontend` directory:
```powershell
cd frontend
npm install
npm run dev
```
*Frontend will start on: [http://localhost:5173](http://localhost:5173)*

### 3. Production Frontend Build
To verify or compile the frontend for production:
```powershell
cd frontend
npm run build
```

---

## 📡 Key REST API Endpoints

### Authentication (`/api/auth`)
- `POST /api/auth/register` - Create a new user account
- `POST /api/auth/login` - Authenticate and obtain JWT token

### User & Dashboard (`/api/user`)
- `GET /api/user/dashboard` - Financial overview, recent transactions, and suggestions
- `GET /api/user/profile` - Current user details
- `PUT /api/user/profile` - Update display name
- `PUT /api/user/change-password` - Update password

### Transactions (`/api/transactions`)
- `GET /api/transactions` - Filtered list of transactions
- `POST /api/transactions` - Create transaction
- `GET /api/transactions/{id}` - Retrieve transaction
- `PUT /api/transactions/{id}` - Update transaction
- `DELETE /api/transactions/{id}` - Delete transaction

### Budgets (`/api/budgets`)
- `GET /api/budgets?month={m}&year={y}` - Get monthly budgets with progress
- `POST /api/budgets` - Create budget limit
- `PUT /api/budgets/{id}` - Update budget
- `DELETE /api/budgets/{id}` - Remove budget

### Savings Goals (`/api/savings`)
- `GET /api/savings` - Get all savings goals
- `POST /api/savings` - Create a savings goal
- `PATCH /api/savings/{id}/amount` - Update current saved balance
- `DELETE /api/savings/{id}` - Delete goal
- `GET /api/savings/suggestions` - Dynamic financial recommendations

### Investments (`/api/investments`)
- `GET /api/investments` - Retrieve investment portfolio
- `POST /api/investments` - Add investment
- `PUT /api/investments/{id}` - Update investment entry
- `DELETE /api/investments/{id}` - Delete investment entry
- `GET /api/investments/suggestions` - Personalized investment recommendations

---

## 🧪 Testing

### Backend Unit & Integration Tests:
```powershell
cd backend
$env:JAVA_HOME = "C:\Program Files\Java\jdk-21.0.11"
.\mvnw.cmd test
```

### Frontend Linting & Build Verification:
```powershell
cd frontend
npm run lint
npm run build
```
