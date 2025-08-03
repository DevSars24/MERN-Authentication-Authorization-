# MERN Authentication & Authorization Portfolio App 🔑

A full-featured **MERN Stack** (MongoDB, Express, React, Node.js) project with secure **authentication**, **authorization**, and role-based access control. Users can signup/login to explore your portfolio. Protected backend APIs and frontend routes ensure only authorized access.

---

## 👁‍🗨️ Overview

* **JWT Auth System** with secure token storage
* **Login / Signup** routes with validation using `Joi`
* **Protected APIs** with JWT Middleware
* **MongoDB** for storing user data securely
* **Frontend in React** with routing and `react-toastify`
* **Form validation**, redirect, and localStorage handling

---

## 📁 Project Structure

```
MERN5/
├── backend/
│   ├── Controllers/
│   ├── Middlewares/
│   ├── Models/
│   ├── Routes/
│   ├── db.js
│   ├── .env
│   └── index.js
├── frontend/
│   ├── public/
│   └── src/
│       ├── pages/
│       ├── login.css
│       └── utils.js
```

---

## 🚀 Backend Breakdown (`/backend`)

### 🔨 `index.js`

* Initializes Express
* Sets up CORS, JSON parsing
* Connects to MongoDB
* Loads `auth` and `product` routes

### 🌎 `db.js`

* MongoDB connection using `mongoose`
* Uses `.env` variable `MONGO_CONN`

### ✏️ `.env`

```
PORT=8080
MONGO_CONN=your_mongo_url
JWT_SECRET=your_secret
```

---

## 🔒 Authentication Logic

### 🔐 `Controllers/AuthController.js`

* `signup()`

  * Hashes password with `bcrypt`
  * Checks duplicate user
  * Saves user to MongoDB
* `login()`

  * Validates credentials
  * Sends back `jwtToken`, `name`, `email`

### 🌐 `Models/User.js`

```js
name: String,
email: String (unique),
password: String
```

### 🔎 `Middlewares/Auth.js`

* Verifies JWT from `Authorization` header
* Attaches decoded user to `req.user`

### 📊 `Middlewares/AuthValidation.js`

* Validates inputs using Joi schema
* Blocks bad requests with status `400`

---

## 🏢 Routes

### 🌐 `/auth`

```js
POST /auth/signup   // Validates + Creates user
POST /auth/login    // Validates + Authenticates user
```

### 💼 `/products`

```js
GET /products       // Protected route
```

Returns an array of product items only when a valid JWT is provided.

---

## 🛍️ Frontend Logic (`/frontend/src/pages`)

### 🌟 `Signup.jsx`

* Form to collect name, email, password
* On submit, makes `POST /auth/signup`
* Stores `jwtToken` in localStorage
* Redirects to `/home`

### 🔑 `Login.jsx`

* Collects email & password
* Makes `POST /auth/login`
* On success, saves token and username to localStorage
* Redirects to protected page

### 🎨 `login.css`

* Reusable, clean UI for signup & login forms

### 🔧 `utils.js`

```js
handleSuccess(msg);  // shows green toast
handleError(msg);    // shows red toast
```

---

## 🚧 How to Run Locally

### ▶️ Backend

```bash
cd backend
npm install
echo PORT=8080 > .env
echo MONGO_CONN=your_mongo_url >> .env
echo JWT_SECRET=your_secret_key >> .env
node index.js
```

### ▶️ Frontend

```bash
cd frontend
npm install
npm start
```

---

## 🔍 API Preview

| Method | Endpoint     | Description      | Auth Required |
| ------ | ------------ | ---------------- | ------------- |
| POST   | /auth/signup | Create user      | No            |
| POST   | /auth/login  | Get JWT Token    | No            |
| GET    | /products    | Get product list | Yes           |

---

## 🏆 Author

**Saurabh Singh Rajput**
2nd Year CSE @ IIIT Bhagalpur
Self-Taught MERN Stack Developer 🤝

[GitHub](https://github.com/DevSars24) • [LinkedIn](https://linkedin.com/in/devsars24)

---

## 🚀 Next Goals

* [ ] Add user profile route
* [ ] Build admin dashboard
* [ ] Integrate Google OAuth
* [ ] Password reset via email

---

> If you liked this project, consider giving a ⭐ on GitHub!
