# **Development Plan: Personal Finance App**

This document outlines a structured development plan, broken down into milestones and tasks, suitable for tracking in a system like GitHub Issues.

### **Milestone 1: Project Setup & Foundation**

This milestone focuses on getting the basic structure of both the frontend and backend applications in place.

* **Task: Initialize .NET 8 Web API Project**  
  * **Description:** Create a new ASP.NET Core Web API project. Set up the basic folder structure (Controllers, Models, Data, Services).  
* **Task: Initialize Angular 18 Project**  
  * **Description:** Use the Angular CLI to create a new project. Set up the basic folder structure (components, services, models).  
* **Task: Configure EF Core with SQLite**  
  * **Description:** Add the necessary NuGet packages (Microsoft.EntityFrameworkCore.Sqlite, Microsoft.EntityFrameworkCore.Design). Configure the DbContext and connection string in appsettings.json.  
* **Task: Create Initial Database Models & Migration**  
  * **Description:** Create the C\# models for Account, Category, and Transaction based on the spec. Generate the initial database migration using EF Core tools.  
* **Task: Configure Backend to Serve Angular App**  
  * **Description:** Configure the .NET project to serve the static files from the compiled Angular application's dist folder.

### **Milestone 2: Backend API Development**

This milestone is about building all the required API endpoints.

* **Task: \[API\] Implement CRUD for Accounts**  
  * **Description:** Create the AccountsController with endpoints for GET, POST, PUT, and DELETE operations on accounts.  
* **Task: \[API\] Implement CRUD for Categories**  
  * **Description:** Create the CategoriesController with endpoints for GET, POST, PUT, and DELETE operations on categories.  
* **Task: \[API\] Implement CRUD for Transactions**  
  * **Description:** Create the TransactionsController with endpoints for GET, POST, PUT, and DELETE operations on transactions.  
* **Task: \[API\] Implement Endpoint for Transfers**  
  * **Description:** Create a POST endpoint in a TransfersController that creates two corresponding Transaction entries to represent a transfer.  
* **Task: \[API\] Implement Endpoint for Dashboard Summary**  
  * **Description:** Create a GET endpoint in a DashboardController that calculates and returns the financial summary for the current month.

### **Milestone 3: Frontend UI & Services**

This milestone covers setting up the frontend's core structure and connecting it to the backend.

* **Task: \[UI\] Create Core App Layout**  
  * **Description:** Design the main app shell with a navigation bar (for Dashboard, Transactions, Accounts, etc.) and a main content area using Bootstrap.  
* **Task: \[UI\] Integrate ng-bootstrap**  
  * **Description:** Add and configure @ng-bootstrap/ng-bootstrap to be used for UI components like modals and forms.  
* **Task: \[Services\] Create API Services**  
  * **Description:** Create Angular services (account.service.ts, transaction.service.ts, etc.) with methods that use HttpClient to call the backend API endpoints.

### **Milestone 4: Feature Development (Frontend)**

This is where you'll build the user-facing features.

* **Task: \[Feature\] Accounts Management Page**  
  * **Description:** Create an Angular component to display a list of accounts. Implement functionality to open modals for adding, editing, and deleting accounts.  
* **Task: \[Feature\] Categories Management Page**  
  * **Description:** Create a component to list all categories. Implement functionality for adding, editing, and deleting categories via modals.  
* **Task: \[Feature\] Transactions Management Page**  
  * **Description:** Create a component to display a table of all transactions. Implement a modal form for adding/editing transactions (both income and expense).  
* **Task: \[Feature\] Create Transfer Modal**  
  * **Description:** Create a dedicated modal form for creating a transfer, allowing the user to select the 'from' and 'to' accounts and enter the amount.  
* **Task: \[Feature\] Build Dashboard Page**  
  * **Description:** Create the dashboard component. Fetch the monthly summary data and display it in cards. Add a simple chart (e.g., using ngx-charts) to show expenses by category.

### **Milestone 5: Finalization**

The final steps to polish the application.

* **Task: Implement Responsive Design**  
  * **Description:** Review all pages and ensure they are usable and look good on mobile devices.  
* **Task: End-to-End Testing**  
  * **Description:** Manually test all user stories from the spec to ensure the application works as expected.  
* **Task: Create Production Build**  
  * **Description:** Run the build scripts for both the frontend and backend to generate the final production-ready artifacts.