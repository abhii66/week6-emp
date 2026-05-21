# Employee Management System — Frontend

A React + Vite single-page application for managing employee records, connected to the Express backend.

---

## Technology Stack

- **React** 19.2.4 — UI library
- **Vite** 8.0.1 — Build tool and dev server
- **React Router** 7.13.2 — Client-side routing
- **Tailwind CSS** 4.2.2 — Utility-first CSS framework
- **React Hook Form** 7.72.0 — Form state management and validation
- **Zustand** 5.0.12 — Lightweight global state management
- **Axios** 1.14.0 — HTTP client for API requests

---

## Project Structure

```
frontend/
├── src/
│   ├── components/
│   │   ├── CreateEmp.jsx        # Create employee form
│   │   ├── EditEmployee.jsx     # Edit employee form (pre-populated)
│   │   ├── Employee.jsx         # Employee detail view
│   │   ├── Header.jsx           # Navigation header
│   │   ├── Home.jsx             # Home page with state management demos
│   │   ├── ListOfEmps.jsx       # Employee grid with actions
│   │   ├── RootLayout.jsx       # Root layout wrapper
│   │   └── Test.jsx             # Test component
│   ├── contexts/
│   │   └── ContextProvider.jsx  # React Context setup
│   ├── store/
│   │   └── CounterStore.js      # Zustand store
│   ├── assets/                  # Static assets
│   ├── App.jsx                  # Route configuration
│   ├── index.css                # Global styles
│   └── main.jsx                 # React entry point
├── public/
├── .gitignore
├── eslint.config.js
├── index.html
├── package.json
├── package-lock.json
└── vite.config.js
```

### Key File Details

**`main.jsx`** — Mounts React, wraps the app in `ContextProvider`, and renders to the DOM.

**`App.jsx`** — Defines all React Router routes and maps them to their components.

**`contexts/ContextProvider.jsx`** — Provides a global counter state and updater functions via React Context.

**`store/CounterStore.js`** — Zustand store for counter state and a user object, demonstrating an alternative to Context.

**`components/Header.jsx`** — Navbar with `NavLink` components, active link highlighting, and responsive design.

**`components/Home.jsx`** — Demonstrates both `useContext` and Zustand consumption with interactive counters.

**`components/CreateEmp.jsx`** — Employee creation form using React Hook Form, with validation, loading state, and POST request to the API.

**`components/ListOfEmps.jsx`** — Fetches and displays all employees in a responsive grid. Supports View, Edit, and Delete actions with real-time list updates.

**`components/Employee.jsx`** — Detail view that reads employee data from React Router's `useLocation` state.

**`components/EditEmployee.jsx`** — Edit form pre-populated via `setValue`, submits a PUT request, and redirects on success.

---

## Installation

### Prerequisites

- Node.js v14 or higher
- npm v6 or higher
- Backend server running at `http://localhost:4000`

### Install Dependencies

```bash
cd frontend
npm install
```

---

## Configuration

The frontend connects to the backend at `http://localhost:4000` by default. No additional configuration is needed for local development.

- **Frontend dev server:** `http://localhost:5173`
- **Backend API base URL:** `http://localhost:4000/employee-api`

---

## Running the App

```bash
npm run dev
```

Expected output:

```
VITE v8.0.1  ready in XXX ms

➜  Local:   http://localhost:5173/
```

Open `http://localhost:5173` in your browser.

---

## Features

### Home Page
- Interactive counters demonstrating two state management approaches side by side: React Context and Zustand.

### Create Employee
- Validated form via React Hook Form
- Displays loading and error states
- Redirects to the employee list on success

### Employee List
- Responsive grid layout (1–4 columns based on screen size)
- Hover effects and card animations
- Per-card View, Edit, and Delete actions
- List updates immediately after any change

### Employee Detail
- Full employee info displayed from navigation state

### Edit Employee
- Form pre-filled with existing data
- PUT request on submit with success feedback and redirect

### Navigation
- Client-side routing with active link highlighting via React Router

---

## Application Flow

1. User visits the home page → `Home` component renders
2. User navigates to **Create Employee** → fills and submits the form → POST to API
3. On success → redirected to **Employee List** → GET fetches all employees
4. User clicks **View** → navigates to employee detail page
5. User clicks **Edit** → navigates to pre-filled edit form → PUT on submit
6. User clicks **Delete** → DELETE request sent → list refreshes automatically

---

## Building for Production

```bash
npm run build
```

Outputs an optimized build to `dist/`.

### Preview the Production Build

```bash
npm run preview
```

---

## Troubleshooting

**API requests failing** — Ensure the backend is running at `http://localhost:4000`. Check for CORS errors in the browser console.

**Port already in use** — Vite will automatically suggest an alternate port, or you can configure it in `vite.config.js`.

**Module not found** — Run `npm install` in the `frontend/` directory. If issues persist, delete `node_modules` and reinstall.

**Blank page after navigation** — Verify React Router routes in `App.jsx` match the component imports.
