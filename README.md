# MERN Stack Application

A full-stack web application built with the MERN stack:
- **M**ongoDB – NoSQL database
- **E**xpress – Node.js web framework
- **R**eact – Frontend JavaScript library
- **N**ode.js – JavaScript runtime

## Project Structure

```
Mern-Stack/
├── backend/               # Node.js + Express API server
│   ├── models/            # Mongoose data models
│   │   └── Item.js
│   ├── routes/            # Express route handlers
│   │   └── items.js
│   ├── .env.example       # Environment variable template
│   ├── package.json
│   └── server.js          # Entry point
│
└── frontend/              # React application
    ├── public/
    │   └── index.html
    ├── src/
    │   ├── App.css
    │   ├── App.js         # Main React component
    │   ├── index.css
    │   └── index.js       # Entry point
    └── package.json
```

## Prerequisites

- [Node.js](https://nodejs.org/) (v14 or higher)
- [MongoDB](https://www.mongodb.com/) (local or [Atlas](https://www.mongodb.com/cloud/atlas))

## Getting Started

### Backend Setup

```bash
cd backend
npm install
cp .env.example .env
# Edit .env and set your MONGO_URI
npm run dev
```

The API server will start on `http://localhost:5000`.

### Frontend Setup

```bash
cd frontend
npm install
npm start
```

The React app will start on `http://localhost:3000`.

## API Endpoints

| Method | Endpoint         | Description        |
|--------|------------------|--------------------|
| GET    | /api/items       | Get all items      |
| GET    | /api/items/:id   | Get item by ID     |
| POST   | /api/items       | Create a new item  |
| PUT    | /api/items/:id   | Update an item     |
| DELETE | /api/items/:id   | Delete an item     |

## Environment Variables

Create a `.env` file in the `backend/` directory (use `.env.example` as a template):

```
PORT=5000
MONGO_URI=mongodb://localhost:27017/merndb
```
