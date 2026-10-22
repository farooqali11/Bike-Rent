# ::: {align="center"}
# 🚲 RideEasy --- Bike Rental System

### Find your ride. Book with ease. Ride with confidence.

A full-stack bike rental web application with bike discovery, online
booking management, user accounts, and an admin dashboard.

![React](https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-Frontend-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-Backend-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-API-000000?style=for-the-badge&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-Database-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
:::

------------------------------------------------------------------------

## ✨ About the Project

**RideEasy** makes it simple for customers to explore available bikes,
view bike details, create an account, and manage their bookings.
Administrators can manage bikes, bookings, users, and view platform
analytics through a dedicated dashboard.

The project is built with a **React + Vite frontend** and a **Node.js +
Express backend**, using **MongoDB** for data storage.

## 🚀 Features

### 👤 Customer Experience

-   Browse available bikes and view individual bike details.
-   Create an account and sign in.
-   Recover a forgotten password and reset it using a token link.
-   Manage account information.
-   Create and view bike bookings.
-   Access booking receipts.
-   Read the "How It Works" page and contact the service.
-   View customer reviews and ratings where available.
-   Receive booking-related emails when email settings are configured.

### 🛠️ Admin Dashboard

-   View an overview of the rental platform.
-   Add, edit, and manage bike listings.
-   Manage customer bookings.
-   View and manage users.
-   Review analytics and booking statistics.
-   Access admin-only routes protected by authentication and role
    checks.

### ⚙️ Technical Highlights

-   REST API built with Express.
-   MongoDB data models for users, bikes, bookings, and reviews.
-   Password hashing with `bcryptjs`.
-   JWT-based authentication.
-   Image upload support with `multer`.
-   Client-side routing with React Router.
-   Zustand stores for shared application state.
-   Charts with Recharts.
-   Responsive frontend components and loading skeletons.

## 🧰 Tech Stack

  Area               Technologies
  ------------------ --------------------------------
  Frontend           React, Vite, React Router
  Styling            CSS, Tailwind CSS tooling
  State Management   Zustand
  Icons              Lucide React
  Charts             Recharts
  Backend            Node.js, Express
  Database           MongoDB, Mongoose
  Authentication     JSON Web Token (JWT), bcryptjs
  File Uploads       Multer
  Email              Nodemailer
  Development        Git, npm, ESLint

## 📁 Project Structure

``` text
rent bike/
├── backend/
│   ├── config/          # Database connection
│   ├── controllers/     # Request handlers and application logic
│   ├── middleware/      # Authentication and upload middleware
│   ├── models/          # MongoDB models
│   ├── routes/          # API route definitions
│   ├── uploads/         # Uploaded bike images
│   ├── utils/           # Email helpers and templates
│   ├── server.js        # Express server entry point
│   └── package.json
│
└── client/
    ├── public/
    └── src/
        ├── api/         # API request helper
        ├── assets/      # Images and static assets
        ├── components/  # Shared UI components
        ├── data/        # Local sample data
        ├── pages/       # Customer-facing pages
        ├── pages/admin/ # Admin dashboard pages
        ├── store/       # Zustand state stores
        ├── utils/       # Frontend utilities
        ├── App.jsx
        └── main.jsx
```

## 🖥️ Getting Started

### 1. Prerequisites

Install the following before running the project:

-   [Node.js](https://nodejs.org/) (LTS recommended)
-   npm (included with Node.js)
-   A MongoDB database, either local or [MongoDB
    Atlas](https://www.mongodb.com/atlas)

### 2. Get the project

Clone your repository or extract the project ZIP, then open a terminal
in the project folder.

### 3. Configure the backend

``` bash
cd backend
npm install
```

Create a file named `.env` inside the `backend/` directory. Add your own
values:

``` env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=replace_with_a_long_random_secret

EMAIL_HOST=your_smtp_host
EMAIL_PORT=587
EMAIL_USER=your_email_username
EMAIL_PASS=your_email_app_password
EMAIL_FROM=RideEasy <no-reply@example.com>
```

**Important:** Replace every example value with your own credentials.
Keep `.env` private and never commit database passwords, email
credentials, or JWT secrets to GitHub. Email settings are optional for
local development; email notifications will be skipped if they are not
configured.

Start the backend:

``` bash
npm run dev
```

The API runs on `http://localhost:5000` by default. Open that URL to
check that the server responds.

### 4. Configure the frontend

Open a **second terminal** from the project root:

``` bash
cd client
npm install
npm run dev
```

Vite will print the local development URL in the terminal (commonly
`http://localhost:5173`). Open that URL in your browser.

### 5. Run both parts

Keep both terminals running while using the app:

-   **Backend:** `http://localhost:5000`
-   **Frontend:** the Vite URL shown in your terminal

The frontend API helper may need to be configured if your backend runs
on a different host or port. Check `client/src/api/api.js` before
deploying.

## 🔌 API Route Groups

The backend currently mounts these API route groups:

  -----------------------------------------------------------------------
  Base path                           Purpose
  ----------------------------------- -----------------------------------
  `/api/auth`                         Registration, login, and
                                      authentication-related actions

  `/api/bikes`                        Bike listings and bike-related
                                      operations

  `/api/bookings`                     Booking operations

  `/api/upload`                       Image/file uploads

  `/api/reviews`                      Reviews and ratings

  `/api/users`                        User management

  `/api/contact`                      Contact form submissions

  `/api/analytics`                    Admin analytics
  -----------------------------------------------------------------------

The exact endpoints and required request bodies are defined in the route
files under `backend/routes/`.

## 🔐 Security Notes

-   Use a strong, unique `JWT_SECRET`.
-   Never upload `.env` or real credentials to a public repository.
-   Use a production MongoDB user with only the permissions it needs.
-   Validate and authorize all sensitive actions on the backend;
    frontend route protection alone is not sufficient.
-   Before deploying, review CORS settings, upload validation, error
    handling, and password-reset flows.
-   Avoid committing `node_modules/`; install dependencies with
    `npm install` instead.

## 🚢 Deployment

You can deploy the frontend and backend separately:

-   **Frontend:** a static hosting provider such as Vercel or Netlify.
-   **Backend:** a Node.js hosting provider that supports Express
    applications.
-   **Database:** MongoDB Atlas or another securely configured MongoDB
    instance.

When deploying, set the environment variables in the hosting provider's
dashboard, configure the frontend to call the deployed backend URL, and
update backend CORS settings to allow your frontend domain. Uploaded
files stored on a local server may not persist on hosts with ephemeral
filesystems; use persistent storage or a suitable object-storage service
for production.

## 🧪 Available Scripts

### Frontend (`client/`)

  Command             Description
  ------------------- --------------------------------------
  `npm run dev`       Start the Vite development server
  `npm run build`     Build the production frontend
  `npm run preview`   Preview the production build locally
  `npm run lint`      Run ESLint

### Backend (`backend/`)

  Command         Description
  --------------- ---------------------------------------
  `npm run dev`   Start the Express server with Nodemon

## 🤝 Contributing

1.  Fork the repository.
2.  Create a feature branch: `git checkout -b feature/your-feature`.
3.  Make your changes and test them locally.
4.  Commit your work: `git commit -m "Add your feature"`.
5.  Push the branch and open a pull request.

## 📌 Project Status

This README describes the project structure and features found in the
current codebase. Test the complete booking, authentication, upload,
email, and admin flows before using the app in production.

## 👨‍💻 Author

**Your Name**\
Add your GitHub profile, portfolio, and contact links here.

------------------------------------------------------------------------

::: {align="center"}
**Built with 💙 for a smoother bike-rental experience.**
:::
