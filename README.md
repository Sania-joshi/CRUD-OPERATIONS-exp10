# Experiment 10: CRUD Operations on Database using Node.js + Express.js Backend

## 🎯 Objective
Build REST APIs using Node.js and Express.js to perform Create, Read, Update, Delete (CRUD) operations on a MongoDB database.

## 🧪 Features Implemented
✅ Create Record - Add new student/user data into database  
✅ Read Records - Fetch all records & Fetch single record using ID  
✅ Update Record - Modify existing data using ID  
✅ Delete Record - Remove record using ID  

## 💻 Tech Stack
- **Node.js** - JavaScript runtime
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB ODM
- **CORS** - Cross-Origin Resource Sharing
- **Nodemon** - Auto-restart on file changes
- **Postman** - API testing tool

## 📁 Project Structure
```
experiment10/
├── server.js                 # Main Express server
├── models/
│   └── Student.js           # MongoDB Student schema
├── routes/
│   └── studentRoutes.js      # CRUD route handlers
├── package.json             # Dependencies
├── package-lock.json
├── node_modules/
└── README.md
```

## ⚙️ Installation & Setup

### 1. Initialize Project
```bash
npm init -y
```

### 2. Install Dependencies
```bash
npm install express mongoose cors nodemon
```

### 3. Configure MongoDB
Ensure MongoDB is running on `localhost:27017` and the database `collegeDB` exists.

### 4. Start Server
**Development mode (with auto-reload):**
```bash
npm run dev
# or
nodemon server.js
```

**Production mode:**
```bash
npm start
```

Server runs on: **http://localhost:5000**

## 🧱 Backend Implementation

### 📄 server.js
Main Express application that:
- Initializes Express and middleware
- Connects to MongoDB using Mongoose
- Sets up routes for student CRUD operations
- Listens on port 5000

### 📄 models/Student.js
Defines MongoDB schema with fields:
- `name` - Student name
- `email` - Student email
- `course` - Course enrolled

### 📄 routes/studentRoutes.js
Implements 5 CRUD endpoints:
- `POST /api/students` - Create new student
- `GET /api/students` - Fetch all students
- `GET /api/students/:id` - Fetch student by ID
- `PUT /api/students/:id` - Update student by ID
- `DELETE /api/students/:id` - Delete student by ID

## 🧪 API Testing with Postman

### 1. Create Record (POST)
**Endpoint:** `POST http://localhost:5000/api/students`

**Headers:**
```
Content-Type: application/json
```

**Body (JSON):**
```json
{
  "name": "Rahul",
  "email": "rahul@gmail.com",
  "course": "BCA"
}
```

**Expected Response:**
```json
{
  "_id": "507f1f77bcf86cd799439011",
  "name": "Rahul",
  "email": "rahul@gmail.com",
  "course": "BCA",
  "__v": 0
}
```

### 2. Get All Records (GET)
**Endpoint:** `GET http://localhost:5000/api/students`

**Expected Response:**
```json
[
  {
    "_id": "507f1f77bcf86cd799439011",
    "name": "Rahul",
    "email": "rahul@gmail.com",
    "course": "BCA",
    "__v": 0
  }
]
```

### 3. Get Single Record (GET)
**Endpoint:** `GET http://localhost:5000/api/students/:id`

Replace `:id` with actual MongoDB ID from create response.

**Expected Response:**
```json
{
  "_id": "507f1f77bcf86cd799439011",
  "name": "Rahul",
  "email": "rahul@gmail.com",
  "course": "BCA",
  "__v": 0
}
```

### 4. Update Record (PUT)
**Endpoint:** `PUT http://localhost:5000/api/students/:id`

**Headers:**
```
Content-Type: application/json
```

**Body (JSON):**
```json
{
  "name": "Rahul Updated",
  "email": "rahul.updated@gmail.com",
  "course": "B.Tech"
}
```

**Expected Response:**
```json
{
  "_id": "507f1f77bcf86cd799439011",
  "name": "Rahul Updated",
  "email": "rahul.updated@gmail.com",
  "course": "B.Tech",
  "__v": 0
}
```

### 5. Delete Record (DELETE)
**Endpoint:** `DELETE http://localhost:5000/api/students/:id`

**Expected Response:**
```json
{
  "message": "Record Deleted Successfully"
}
```

## 📸 Required Screenshots Checklist
- [ ] MongoDB Connected Message (terminal output)
- [ ] Create Record API Success (Postman response)
- [ ] Read All Records Output (Postman response)
- [ ] Single Record Output (Postman response)
- [ ] Update Record Success (Postman response)
- [ ] Delete Record Success (Postman response)
- [ ] Database Collection View (MongoDB Compass)

## 📘 Implementation Summary

### How It Works:
1. **Client** sends HTTP request to Express server
2. **Express** routes request to appropriate handler in `studentRoutes.js`
3. **Mongoose** interacts with MongoDB using Student schema
4. **Database** stores/retrieves/updates/deletes student records
5. **Server** responds with JSON data back to client

### CRUD Operations Mapping:
- **CREATE** - HTTP POST, DB Insert
- **READ** - HTTP GET, DB Find
- **UPDATE** - HTTP PUT, DB Update
- **DELETE** - HTTP DELETE, DB Remove

## 🚀 Quick Start Command
```bash
# Install and start in one command
npm install && npm run dev
```

## 🐛 Troubleshooting

**"Database Connected" message not appearing?**
- Ensure MongoDB is running: `mongod`
- Check connection string in server.js
- Verify MongoDB is listening on port 27017

**Port 5000 already in use?**
- Change port in server.js: `app.listen(3000, ...)`
- Or kill existing process using port 5000

**CORS errors when testing from frontend?**
- CORS is already enabled in server.js
- Ensure frontend sends proper headers

---

**Deadline:** 24 April  
**Status:** ✅ Complete & Ready for Testing
