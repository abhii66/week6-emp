# Employee Management System

A full-stack web application for managing employee information with a modern React frontend and Express.js backend with MongoDB database.

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [API Documentation](#api-documentation)
- [Features](#features)
- [File Structure Details](#file-structure-details)

---

## 🎯 Project Overview

This is a MERN-style (MongoDB, Express, React, Node.js) employee management application that allows users to:
- Create new employee records
- View all employees in a responsive grid layout
- View detailed information for each employee
- Edit employee information
- Delete employee records

All operations are performed with real-time database synchronization and error handling.

---

## 🛠 Technology Stack

### Frontend
- **React** 19.2.4 - UI library
- **Vite** 8.0.1 - Build tool and dev server
- **React Router** 7.13.2 - Client-side routing
- **Tailwind CSS** 4.2.2 - Utility-first CSS framework
- **React Hook Form** 7.72.0 - Form state management
- **Zustand** 5.0.12 - Lightweight state management
- **Axios** 1.14.0 - HTTP client for API calls

### Backend
- **Node.js** - JavaScript runtime
- **Express** 5.2.1 - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** 9.3.3 - MongoDB object modeling
- **CORS** 2.8.6 - Cross-Origin Resource Sharing
- **dotenv** 17.3.1 - Environment variables

---

## 📁 Project Structure

```
Employee-management-project/
├── backend/
│   ├── APIs/
│   │   └── EmployeeAPI.js          # REST API routes
│   ├── Models/
│   │   └── EmployeeModel.js         # MongoDB employee schema
│   ├── node_modules/                # Backend dependencies
│   ├── .env                         # Environment variables
│   ├── .gitignore                   # Git ignore rules
│   ├── package.json                 # Backend dependencies config
│   ├── package-lock.json            # Dependency lock file
│   ├── req.http                     # HTTP request examples
│   └── server.js                    # Express server entry point
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── CreateEmp.jsx        # Create employee form
│   │   │   ├── EditEmployee.jsx     # Edit employee form
│   │   │   ├── Employee.jsx         # Employee detail view
│   │   │   ├── Header.jsx           # Navigation header
│   │   │   ├── Home.jsx             # Home page with counters
│   │   │   ├── ListOfEmps.jsx       # Employee list grid
│   │   │   ├── RootLayout.jsx       # Root layout wrapper
│   │   │   └── Test.jsx             # Test component
│   │   ├── contexts/
│   │   │   └── ContextProvider.jsx  # React Context setup
│   │   ├── store/
│   │   │   └── CounterStore.js      # Zustand store
│   │   ├── assets/                  # Static assets
│   │   ├── App.jsx                  # Main app component
│   │   ├── index.css                # Global styles
│   │   └── main.jsx                 # React entry point
│   │
│   ├── public/                      # Public assets
│   ├── node_modules/                # Frontend dependencies
│   ├── .gitignore                   # Git ignore rules
│   ├── eslint.config.js             # ESLint configuration
│   ├── index.html                   # HTML template
│   ├── package.json                 # Frontend dependencies config
│   ├── package-lock.json            # Dependency lock file
│   ├── vite.config.js               # Vite configuration
│   └── README.md                    # Frontend documentation
│
├── README.md                        # Project documentation (this file)
└── .git/                           # Git repository
```

---

## 🚀 Installation

### Prerequisites
- Node.js (v14 or higher)
- npm (v6 or higher)
- MongoDB (running on localhost:27017)

### Backend Installation

```bash
cd backend
npm install
```

Installs:
- express, mongoose, cors, dotenv

### Frontend Installation

```bash
cd frontend
npm install
```

Installs:
- react, vite, tailwindcss, react-router, react-hook-form, zustand, axios

---

## ⚙️ Configuration

### Backend Environment Variables (.env)

Create a `.env` file in the backend directory:

```env
PORT=4000
DB_URL=mongodb://localhost:27017/demobackend
```

**Variables Explanation:**
- `PORT`: Port number for Express server (default: 4000)
- `DB_URL`: MongoDB connection string

### Frontend Configuration

The frontend is configured to:
- Run on `http://localhost:5173` (Vite default)
- Connect to backend at `http://localhost:4000`
- CORS is enabled on backend for frontend origin

---

## ▶️ Running the Application

### Start Backend Server

```bash
cd backend
npm start
```

Expected output:
```
[dotenv] injecting env (2) from .env
DB connection successful
server listening to port 4000...
```

### Start Frontend Development Server

Open a new terminal:

```bash
cd frontend
npm run dev
```

Expected output:
```
VITE v8.0.1  ready in XXX ms

➜  Local:   http://localhost:5173/
```

### Access the Application

Open your browser and navigate to:
```
http://localhost:5173
```

---

## 📡 API Documentation

### Base URL
```
http://localhost:4000/employee-api
```

### Endpoints

#### 1. Get All Employees
```http
GET /employees
```

**Response (200 OK):**
```json
{
  "message": "Employees:",
  "payload": [
    {
      "_id": "507f1f77bcf86cd799439011",
      "name": "John Doe",
      "email": "john@example.com",
      "mobile": 9876543210,
      "designation": "Software Engineer",
      "companyName": "TechCorp",
      "createdAt": "2026-05-14T10:30:00.000Z",
      "updatedAt": "2026-05-14T10:30:00.000Z"
    }
  ]
}
```

#### 2. Create Employee
```http
POST /employees
Content-Type: application/json

{
  "name": "Jane Smith",
  "email": "jane@example.com",
  "mobile": 9876543211,
  "designation": "Project Manager",
  "companyName": "TechCorp"
}
```

**Response (201 Created):**
```json
{
  "message": "Employee created"
}
```

#### 3. Update Employee
```http
PUT /employees/:id
Content-Type: application/json

{
  "name": "Jane Smith",
  "email": "jane.smith@example.com",
  "mobile": 9876543211,
  "designation": "Senior Project Manager",
  "companyName": "TechCorp"
}
```

**Response (200 OK):**
```json
{
  "message": "Employee updated",
  "payload": {
    "_id": "507f1f77bcf86cd799439011",
    "name": "Jane Smith",
    "email": "jane.smith@example.com",
    "mobile": 9876543211,
    "designation": "Senior Project Manager",
    "companyName": "TechCorp",
    "updatedAt": "2026-05-14T11:45:00.000Z"
  }
}
```

#### 4. Delete Employee
```http
DELETE /employees/:id
```

**Response (200 OK):**
```json
{
  "message": "Employee Deleted",
  "payload": {
    "_id": "507f1f77bcf86cd799439011",
    "name": "Jane Smith",
    "email": "jane.smith@example.com",
    "mobile": 9876543211,
    "designation": "Senior Project Manager",
    "companyName": "TechCorp"
  }
}
```

### Error Responses

#### Validation Error (400)
```json
{
  "message": "error occured",
  "error": "ValidationError"
}
```

#### Not Found (404)
```json
{
  "message": "Employee not found"
}
```

#### Server Error (500)
```json
{
  "message": "error occured",
  "error": "Server side error"
}
```

---

## ✨ Features

### Frontend Features

1. **Home Page**
   - Counter state management using React Context
   - Counter state management using Zustand
   - Interactive buttons to test state management

2. **Create Employee**
   - Form validation using React Hook Form
   - Real-time form input handling
   - Success/error notifications
   - Automatic redirect on successful creation

3. **Employee List**
   - Responsive grid layout (1-4 columns based on screen size)
   - Hover effects and animations
   - Quick action buttons (View, Edit, Delete)
   - Real-time list updates

4. **Employee Detail View**
   - Display complete employee information
   - Navigation-based state passing

5. **Edit Employee**
   - Pre-populated form with existing data
   - Form validation
   - Success feedback and redirection

6. **Navigation**
   - React Router for client-side routing
   - Active link highlighting
   - Responsive navbar

### Backend Features

1. **Database Operations**
   - Create employees with validation
   - Read all employees
   - Update employee information
   - Delete employees

2. **Data Validation**
   - Required field validation
   - Email uniqueness check
   - Proper error messages

3. **Error Handling**
   - ValidationError handling
   - CastError handling
   - Generic server error handling

4. **CORS Support**
   - Frontend origin allowed
   - Cross-origin requests enabled

---

## 📝 File Structure Details

### Backend Files

#### `server.js`
Main Express server file that:
- Initializes Express app
- Configures CORS middleware
- Loads environment variables
- Connects to MongoDB
- Sets up routes
- Implements error handling middleware

#### `APIs/EmployeeAPI.js`
Express Router defining all employee endpoints:
- POST /employees - Create
- GET /employees - Read all
- PUT /employees/:id - Update
- DELETE /employees/:id - Delete

#### `Models/EmployeeModel.js`
Mongoose schema defining employee data structure:
- name (String, required)
- email (String, required, unique)
- mobile (Number, required)
- designation (String, required)
- companyName (String, required)
- timestamps (auto-generated)

### Frontend Files

#### `main.jsx`
React entry point that:
- Initializes React with ReactDOM
- Wraps app with ContextProvider
- Mounts app to DOM

#### `App.jsx`
Main React component that:
- Configures React Router with routes
- Defines route structure and components
- Provides client-side navigation

#### `contexts/ContextProvider.jsx`
Context API setup for:
- Global counter state
- Counter update functions
- Context value distribution

#### `store/CounterStore.js`
Zustand store providing:
- Counter state management
- User object management
- Actions to modify state

#### `components/Header.jsx`
Navigation component with:
- NavLinks for routing
- Active link styling
- Responsive design

#### `components/Home.jsx`
Home page component demonstrating:
- useContext hook usage
- Zustand store consumption
- Interactive counters

#### `components/CreateEmp.jsx`
Employee creation component with:
- React Hook Form integration
- Form validation
- HTTP POST request
- Loading and error states

#### `components/ListOfEmps.jsx`
Employee list component featuring:
- useEffect for data fetching
- Grid layout with responsive columns
- Axios GET request
- Delete functionality
- Navigation to detail/edit views

#### `components/Employee.jsx`
Employee detail view component:
- useLocation for state access
- Display employee information
- Hover animations

#### `components/EditEmployee.jsx`
Employee edit component with:
- useForm setValue for pre-population
- Form submission for update
- HTTP PUT request
- Navigation after save

---

## 🔄 Application Flow

1. **User navigates to home page** → Home component renders
2. **User clicks "CreateEmp"** → Navigates to CreateEmp component
3. **User fills form and submits** → POST request to `/employee-api/employees`
4. **On success** → Redirects to ListOfEmps component
5. **ListOfEmps fetches data** → GET request loads all employees
6. **User clicks "View"** → Navigates to Employee component with state
7. **User clicks "Edit"** → Navigates to EditEmployee with pre-filled form
8. **User submits edit** → PUT request updates employee
9. **On success** → Returns to ListOfEmps
10. **User clicks "Delete"** → DELETE request removes employee
11. **List refreshes** → Shows updated employee list

---

## 🐛 Troubleshooting

### MongoDB Connection Error
- Ensure MongoDB is running: `mongod`
- Check connection string in `.env`
- Verify port 27017 is accessible

### Port Already in Use
- Change PORT in `.env` for backend
- Change port in `npm run dev` script for frontend
- Or kill process using the port

### CORS Error
- Verify frontend URL in backend CORS config
- Default: `http://localhost:5173`

### Module Not Found
- Run `npm install` in both backend and frontend directories
- Clear node_modules and reinstall if issues persist

---

## 📦 Build & Deployment

### Build Frontend for Production
```bash
cd frontend
npm run build
```

Creates optimized build in `dist/` folder.

### Preview Production Build
```bash
cd frontend
npm run preview
```

---

## 📄 License

This project is open source and available under the ISC License.

---

## 👤 Author

Employee Management System - Capstone Mini Project

---

## 📞 Support

For issues or questions, refer to the API documentation above or check the component files for implementation details.
