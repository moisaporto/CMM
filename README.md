# **Technical Specifications: Personal Finance Application**

## **1\. Introduction**

This document outlines the technical specifications for a personal finance management application. The goal is to create a simple, user-friendly application that allows users to track their income, expenses, and account balances. The application will be built using modern, open-source technologies. The application name is CMM.

## **2\. Functional Requirements**

The application will provide the following core functionalities:

### **2.1. User Stories**

* **Accounts Management:**  
  * As a user, I want to add, view, edit, and delete my financial accounts (e.g., Checking, Savings, Credit Card).  
  * Each account should have a name and an initial balance.  
* **Transaction Management:**  
  * As a user, I want to add an expense or income transaction.  
  * Each transaction must be associated with an account.  
  * Each transaction must have a date, an amount, a description, and be assigned to a category.  
* **Transfers:**  
  * As a user, I want to record money transfers between my accounts.  
  * A transfer will decrease the balance of the source account and increase the balance of the destination account.  
* **Category Management:**  
  * As a user, I want to add, view, edit, and delete spending/income categories (e.g., "Rent," "Groceries," "Salary").  
* **Dashboard:**  
  * As a user, I want to see a dashboard that summarizes my financial activity for the current month.  
  * The dashboard should display:  
    * Total income for the current month.  
    * Total expenses for the current month.  
    * A breakdown of expenses by category for the current month.  
    * Current balances of all my accounts.

## **3\. Technical Architecture**

The application will be developed as a single-page application (SPA) with a backend API.

* **Frontend:**  
  * **Framework:** Angular 18  
  * **Styling:** Bootstrap 5 (via ng-bootstrap or similar library)  
  * **Language:** TypeScript  
* **Backend:**  
  * **Framework:** .NET 8 (using ASP.NET Core Web API)  
  * **Language:** C\#  
* **Database:**  
  * **Engine:** SQLite  
  * **ORM:** Entity Framework Core 8  
* **Hosting:**  
  * The application will be designed to be self-hosted. The backend will serve the compiled Angular frontend.

## **4\. API Endpoints (RESTful)**

The backend will expose a RESTful API. All data will be exchanged in JSON format.

| Feature | Method | Endpoint | Description |
| :---- | :---- | :---- | :---- |
| **Accounts** | GET | /api/accounts | Get all accounts. |
|  | POST | /api/accounts | Create a new account. |
|  | PUT | /api/accounts/{id} | Update an existing account. |
|  | DELETE | /api/accounts/{id} | Delete an account. |
| **Transactions** | GET | /api/transactions | Get all transactions (with filtering options). |
|  | POST | /api/transactions | Create a new transaction (income/expense). |
|  | PUT | /api/transactions/{id} | Update a transaction. |
|  | DELETE | /api/transactions/{id} | Delete a transaction. |
| **Transfers** | POST | /api/transfers | Create a new transfer between accounts. |
| **Categories** | GET | /api/categories | Get all categories. |
|  | POST | /api/categories | Create a new category. |
|  | PUT | /api/categories/{id} | Update a category. |
|  | DELETE | /api/categories/{id} | Delete a category. |
| **Dashboard** | GET | /api/dashboard/monthly-summary | Get the summary for the current month. |

## **5\. Database Schema**

The SQLite database will consist of the following tables:

### **Accounts**

| Column | Type | Constraints | Description |
| :---- | :---- | :---- | :---- |
| Id | INTEGER | PRIMARY KEY, AUTOINCREMENT | Unique identifier for the account. |
| Name | TEXT | NOT NULL | Name of the account. |
| InitialBalance | REAL | NOT NULL | The starting balance. |

### **Categories**

| Column | Type | Constraints | Description |
| :---- | :---- | :---- | :---- |
| Id | INTEGER | PRIMARY KEY, AUTOINCREMENT | Unique identifier for the category. |
| Name | TEXT | NOT NULL, UNIQUE | Name of the category. |

### **Transactions**

| Column | Type | Constraints | Description |
| :---- | :---- | :---- | :---- |
| Id | INTEGER | PRIMARY KEY, AUTOINCREMENT | Unique identifier for the transaction. |
| AccountId | INTEGER | FOREIGN KEY (Accounts.Id) | The account this transaction belongs to. |
| CategoryId | INTEGER | FOREIGN KEY (Categories.Id) | The category of the transaction. |
| Amount | REAL | NOT NULL | Transaction amount (positive for income, negative for expense). |
| Date | TEXT | NOT NULL | Date of the transaction (ISO 8601 format). |
| Description | TEXT | NULL | A brief description of the transaction. |
| IsTransfer | INTEGER | NOT NULL, DEFAULT 0 | Flag to indicate if it's part of a transfer (0 or 1). |

## **6\. Recommended Open Source Libraries**

* **Frontend (Angular):**  
  * @ng-bootstrap/ng-bootstrap: For integrating Bootstrap components seamlessly with Angular.  
  * date-fns or moment.js: For reliable date and time manipulation.  
  * chart.js or ngx-charts: For displaying charts on the dashboard.  
* **Backend (.NET):**  
  * Microsoft.EntityFrameworkCore.Sqlite: The EF Core provider for SQLite.  
  * Microsoft.EntityFrameworkCore.Design: For database migrations.  
  * Swashbuckle.AspNetCore: For generating Swagger/OpenAPI documentation for the API.

## **7\. Styling and UI/UX**

* **Styling:** The application will use standard Bootstrap 5 classes for layout, components (buttons, forms, tables, modals), and responsiveness. No custom CSS framework is required. The theme will be light and clean.  
* **User Experience:**  
  * The interface should be intuitive and require minimal instruction.  
  * Forms for adding/editing data will be presented in modals to avoid page reloads.  
  * Data tables will be used to display lists of accounts, transactions, and categories.  
  * The application must be fully responsive and usable on both desktop and mobile devices.