# US Life

A full stack MERN practice project: a React storefront with a shopping cart, user registration backed by an Express + MongoDB API, and a registered-users directory.

![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-8-646CFF?logo=vite&logoColor=white)
![React Router](https://img.shields.io/badge/React%20Router-7-CA4245?logo=reactrouter&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-Express%205-339933?logo=nodedotjs&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose-47A248?logo=mongodb&logoColor=white)
[![Live Demo](https://img.shields.io/badge/Live%20Demo-Vercel-000000?logo=vercel&logoColor=white)](https://intenship-training.vercel.app/)

## Live Demo

**[intenship-training.vercel.app](https://intenship-training.vercel.app/)**

The frontend is hosted on Vercel and talks to the backend API hosted on Render.

## Overview

US Life was built during internship training to practise the complete MERN workflow: building a React UI with client-side routing, managing shared state, calling REST APIs with `fetch` and Axios, and persisting data in MongoDB through an Express server.

The app has two parts:

- **`frontend/`**: a React + Vite single-page app with a product catalogue, cart and checkout summary, registration form, users list, and an API demo page.
- **`backend/`**: an Express server that registers users and serves them from MongoDB via Mongoose.

## Features

- **Home / store**: featured products grid with "Add to cart"; adding an item already in the cart increases its quantity
- **Shopping cart**: increase / decrease quantity, remove items, live bill with subtotal, 18% GST and a flat delivery charge, plus billing details (name, address, payment method: COD, UPI, credit or debit card) and an order confirmation
- **Cart badge**: item count shown in the header on every page
- **Registration**: sign-up form that posts to the backend and shows the server's response (for example, duplicate email errors)
- **Users page**: table of registered users (avatar initial, name, email) fetched from the backend
- **API demo page**: product cards loaded from the public [DummyJSON](https://dummyjson.com/) products API
- **About and Contact pages**, shared header navigation and footer
- Responsive layout built with plain CSS

## Tech Stack

| Layer | Technology |
| --- | --- |
| Frontend | React 19, Vite 8, React Router 7, Axios, CSS |
| Backend | Node.js, Express 5, CORS |
| Database | MongoDB with Mongoose |
| Tooling | ESLint, nodemon |
| Hosting | Vercel (frontend), Render (backend) |

## Project Structure

```
us-life/
├── frontend/                 # React + Vite app
│   ├── index.html
│   ├── vite.config.js
│   ├── public/
│   └── src/
│       ├── main.jsx          # Entry point
│       ├── App.jsx           # Routes, About and Contact pages, cart state
│       ├── Header.jsx        # Navigation + cart badge
│       ├── Footer.jsx
│       ├── home.jsx          # Featured products
│       ├── Cart.jsx          # Cart, bill and checkout
│       ├── Register.jsx      # Registration form (POST /register)
│       ├── Users.jsx         # Registered users (GET /users)
│       └── ApiCalling.jsx    # DummyJSON products demo
└── backend/                  # Express + MongoDB API
    ├── index.js              # Main server (npm start)
    ├── model/user.js         # Mongoose User schema
    ├── db/config.js          # Alternative local MongoDB connection helper
    ├── server.js             # Earlier version of the server without a database
    └── backend/public/       # Early static HTML/CSS/JS practice pages
```

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) 18 or newer
- A MongoDB database (local install or a free [MongoDB Atlas](https://www.mongodb.com/atlas) cluster)

### Installation

```bash
git clone https://github.com/panchalnikhil6531/us-life.git
cd us-life

# Backend
cd backend
npm install

# Frontend
cd ../frontend
npm install
```

### Configuration

The project does not read any environment variables yet. To run it against your own services:

| Setting | Where | Description |
| --- | --- | --- |
| MongoDB connection string | `backend/index.js` (`mongoose.connect(...)`) | Point it at your own local or Atlas database |
| Backend port | `backend/index.js` (`PORT`) | Fixed at `5000` |
| API base URL | `frontend/src/Register.jsx`, `frontend/src/Users.jsx` | Currently the deployed Render backend; change to `http://localhost:5000` to use a local server |

### Run

**Backend** (from `backend/`):

| Command | Description |
| --- | --- |
| `npm start` | Start the API on [http://localhost:5000](http://localhost:5000) |
| `npx nodemon index.js` | Start with auto-restart on file changes |

**Frontend** (from `frontend/`):

| Command | Description |
| --- | --- |
| `npm run dev` | Start the Vite dev server |
| `npm run build` | Build for production into `dist/` |
| `npm run preview` | Preview the production build |
| `npm run lint` | Run ESLint |

## API Endpoints

Served by `backend/index.js`.

| Method | Endpoint | Description |
| --- | --- | --- |
| `GET` | `/` | Health check ("Server is running...") |
| `POST` | `/register` | Register a user (`name`, `email`, `password`); rejects missing fields and duplicate emails |
| `GET` | `/users` | List all users |
| `GET` | `/users/:id` | Get one user by ID |
| `DELETE` | `/users/:id` | Delete a user by ID |

## Deployment

- **Frontend**: deployed on Vercel from the `frontend/` directory (build command `npm run build`, output directory `dist`).
- **Backend**: deployed on Render as a Node web service from the `backend/` directory (start command `npm start`).

## Roadmap

- Load the MongoDB connection string, port and API base URL from environment variables
- Hash passwords before storing them and exclude them from API responses
- Add login and protect the user management endpoints

## Author

**Panchal Nikhil S**

- GitHub: [@panchalnikhil6531](https://github.com/panchalnikhil6531)
- LinkedIn: [Nikhil S Panchal](https://www.linkedin.com/in/nikhil-s-panchal-463a78319/)
- Portfolio: [potfolio-beta-two.vercel.app](https://potfolio-beta-two.vercel.app/)
