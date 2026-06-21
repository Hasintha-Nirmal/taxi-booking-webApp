# 🚖 Taxi Booking Web Application

A full-stack real-time taxi booking application built with **React**, **Node.js**, **Express**, **MongoDB**, and **Socket.IO**. This application allows users to book rides and captains (drivers) to accept and manage ride requests in real-time.

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Environment Variables](#-environment-variables)
- [Running the Application](#-running-the-application)
- [API Documentation](#-api-documentation)
- [Frontend Routes](#-frontend-routes)
- [Real-Time Features](#-real-time-features)
- [Database Schema](#-database-schema)
- [Security Features](#-security-features)
- [Contributing](#-contributing)
- [License](#-license)

## ✨ Features

### For Users
- 👤 User registration and authentication
- 📍 Location-based pickup and destination selection
- 🚗 Multiple vehicle types (Auto, Car, Motorcycle)
- 💰 Real-time fare calculation
- 🔍 Google Maps integration for location search
- 🎯 Live tracking of assigned captain
- 🔐 Secure OTP-based ride verification
- 📱 Real-time ride status updates

### For Captains (Drivers)
- 👨‍✈️ Captain registration with vehicle details
- 🚦 Accept or reject ride requests
- 📲 Real-time ride notifications
- 🗺️ Live location sharing
- ✅ OTP verification for ride start
- 💼 Ride history and management
- 🟢 Online/offline status toggle

### Admin/System Features
- 🔒 JWT-based authentication
- 🚫 Token blacklisting for logout
- 🌍 Google Maps API integration
- 💬 Real-time Socket.IO communication
- 📊 Distance and duration calculation
- 🔄 Automatic ride matching within radius

## 🛠️ Tech Stack

### Frontend
- **React 18** - UI library
- **Vite** - Build tool and dev server
- **React Router DOM** - Client-side routing
- **Axios** - HTTP client
- **Socket.IO Client** - Real-time communication
- **Tailwind CSS** - Utility-first CSS framework
- **GSAP** - Animation library
- **@react-google-maps/api** - Google Maps integration
- **Remix Icon** - Icon library

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB ODM
- **Socket.IO** - Real-time bidirectional communication
- **JWT (jsonwebtoken)** - Authentication
- **bcrypt** - Password hashing
- **express-validator** - Request validation
- **cookie-parser** - Cookie parsing
- **cors** - Cross-origin resource sharing
- **axios** - HTTP client for external APIs
- **dotenv** - Environment variable management

### External Services
- **Google Maps API** - Geocoding, Distance Matrix, Places, Maps JavaScript API

## 📁 Project Structure

```
taxi-booking-webApp/
├── Backend/
│   ├── controllers/         # Request handlers
│   │   ├── captain.controller.js
│   │   ├── map.controller.js
│   │   ├── ride.controller.js
│   │   └── user.controller.js
│   ├── db/                  # Database configuration
│   │   └── db.js
│   ├── middlewares/         # Custom middleware
│   │   └── auth.middleware.js
│   ├── models/              # Mongoose schemas
│   │   ├── blacklistToken.model.js
│   │   ├── captain.model.js
│   │   ├── ride.model.js
│   │   └── user.model.js
│   ├── routes/              # API routes
│   │   ├── captain.routes.js
│   │   ├── maps.routes.js
│   │   ├── ride.routes.js
│   │   └── user.routes.js
│   ├── services/            # Business logic
│   │   ├── captain.service.js
│   │   ├── maps.service.js
│   │   ├── ride.service.js
│   │   └── user.service.js
│   ├── app.js               # Express app configuration
│   ├── server.js            # Server entry point
│   ├── socket.js            # Socket.IO configuration
│   ├── package.json
│   ├── .env                 # Environment variables (not in git)
│   └── README.md            # API documentation
├── frontend/
│   ├── src/
│   │   ├── components/      # React components
│   │   │   ├── CaptainDetails.jsx
│   │   │   ├── ConfirmRide.jsx
│   │   │   ├── ConfirmRidePopUp.jsx
│   │   │   ├── FinishRide.jsx
│   │   │   ├── LiveTracking.jsx
│   │   │   ├── LocationSearchPanel.jsx
│   │   │   ├── LookingForDriver.jsx
│   │   │   ├── RidePopUp.jsx
│   │   │   ├── VehiclePanel.jsx
│   │   │   └── WaitingForDriver.jsx
│   │   ├── context/         # React context providers
│   │   │   ├── CapatainContext.jsx
│   │   │   ├── SocketContext.jsx
│   │   │   └── UserContext.jsx
│   │   ├── pages/           # Page components
│   │   │   ├── CaptainHome.jsx
│   │   │   ├── Captainlogin.jsx
│   │   │   ├── CaptainLogout.jsx
│   │   │   ├── CaptainProtectWrapper.jsx
│   │   │   ├── CaptainRiding.jsx
│   │   │   ├── CaptainSignup.jsx
│   │   │   ├── Home.jsx
│   │   │   ├── Riding.jsx
│   │   │   ├── Start.jsx
│   │   │   ├── UserLogin.jsx
│   │   │   ├── UserLogout.jsx
│   │   │   ├── UserProtectWrapper.jsx
│   │   │   └── UserSignup.jsx
│   │   ├── App.jsx          # Main app component
│   │   ├── main.jsx         # Entry point
│   │   └── index.css        # Global styles
│   ├── public/              # Static assets
│   ├── package.json
│   ├── vite.config.js       # Vite configuration
│   ├── tailwind.config.js   # Tailwind configuration
│   ├── .env                 # Environment variables (not in git)
│   └── README.md
├── .gitignore
├── .env.sample              # Sample environment variables
└── README.md                # This file
```

## 📦 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v16.x or higher) - [Download](https://nodejs.org/)
- **npm** (v8.x or higher) or **yarn** (v1.22.x or higher)
- **MongoDB** (v5.x or higher) - [Download](https://www.mongodb.com/try/download/community) or use [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
- **Google Cloud Platform Account** - For Maps API keys
- **Git** - For cloning the repository

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone <repository-url>
cd taxi-booking-webApp
```

### 2. Backend Setup

```bash
# Navigate to backend directory
cd Backend

# Install dependencies
npm install

# Create .env file from sample
copy .env.sample .env    # Windows
# OR
cp .env.sample .env      # Linux/Mac

# Edit .env file and add your credentials
# See Environment Variables section below
```

### 3. Frontend Setup

```bash
# Navigate to frontend directory (from project root)
cd frontend

# Install dependencies
npm install

# Create .env file from sample
copy .env.sample .env    # Windows
# OR
cp .env.sample .env      # Linux/Mac

# Edit .env file and add your backend URL and Google Maps API key
```

## 🔐 Environment Variables

### Backend (.env)

Create a `Backend/.env` file with the following variables:

```env
# Server Configuration
PORT=3000

# Database Configuration
DB_CONNECT=mongodb://localhost:27017/taxi-booking-app
# For MongoDB Atlas:
# DB_CONNECT=mongodb+srv://username:password@cluster.mongodb.net/taxi-booking-app

# JWT Configuration
JWT_SECRET=your-super-secret-jwt-key-change-this-in-production

# Google Maps API
GOOGLE_MAPS_API=your-google-maps-api-key-here
```

### Frontend (.env)

Create a `frontend/.env` file with the following variables:

```env
# Backend API URL
VITE_BASE_URL=http://localhost:3000
VITE_API_URL=http://localhost:3000

# Google Maps API
VITE_GOOGLE_MAPS_API_KEY=your-google-maps-api-key-here
```

### Setting Up Google Maps API

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select an existing one
3. Enable the following APIs:
   - **Geocoding API**
   - **Distance Matrix API**
   - **Places API**
   - **Maps JavaScript API**
4. Create credentials (API Key)
5. (Optional but recommended) Add API key restrictions:
   - For backend: Restrict to your server IP
   - For frontend: Restrict to your domain/localhost

### Setting Up MongoDB

**Option A: Local MongoDB**
```bash
# Install MongoDB Community Edition
# Start MongoDB service
mongod

# MongoDB will run on mongodb://localhost:27017
```

**Option B: MongoDB Atlas (Cloud)**
1. Create account at [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a free cluster
3. Create a database user
4. Whitelist your IP address (or 0.0.0.0/0 for all IPs in development)
5. Get connection string and update `DB_CONNECT` in `.env`

## 🏃 Running the Application

### Development Mode

**Terminal 1 - Backend:**
```bash
cd Backend
npm run dev
# Server runs on http://localhost:3000
```

**Terminal 2 - Frontend:**
```bash
cd frontend
npm run dev
# App runs on http://localhost:5173
```

### Production Mode

**Backend:**
```bash
cd Backend
npm start
```

**Frontend:**
```bash
cd frontend
npm run build
npm run preview
```

## 📚 API Documentation

### Base URL
```
http://localhost:3000
```

### Authentication
Most endpoints require JWT authentication. Include the token in the Authorization header:
```
Authorization: Bearer <your-jwt-token>
```

---

### User Endpoints

#### 1. Register User
**POST** `/users/register`

**Request Body:**
```json
{
  "fullname": {
    "firstname": "John",
    "lastname": "Doe"
  },
  "email": "john@example.com",
  "password": "password123"
}
```

**Response:**
```json
{
  "token": "jwt-token-here",
  "user": {
    "_id": "user-id",
    "fullname": {
      "firstname": "John",
      "lastname": "Doe"
    },
    "email": "john@example.com"
  }
}
```

**Validation:**
- `firstname`: minimum 3 characters
- `lastname`: minimum 3 characters (optional)
- `email`: valid email format
- `password`: minimum 6 characters

---

#### 2. Login User
**POST** `/users/login`

**Request Body:**
```json
{
  "email": "john@example.com",
  "password": "password123"
}
```

**Response:** Same as register

---

#### 3. Get User Profile
**GET** `/users/profile`

**Headers:**
```
Authorization: Bearer <token>
```

**Response:**
```json
{
  "_id": "user-id",
  "fullname": {
    "firstname": "John",
    "lastname": "Doe"
  },
  "email": "john@example.com"
}
```

---

#### 4. Logout User
**GET** `/users/logout`

**Headers:**
```
Authorization: Bearer <token>
```

**Response:**
```json
{
  "message": "Logged out"
}
```

---

### Captain Endpoints

#### 1. Register Captain
**POST** `/captains/register`

**Request Body:**
```json
{
  "fullname": {
    "firstname": "Jane",
    "lastname": "Smith"
  },
  "email": "jane@example.com",
  "password": "password123",
  "vehicle": {
    "color": "Black",
    "plate": "ABC-1234",
    "capacity": 4,
    "vehicleType": "car"
  }
}
```

**Validation:**
- `vehicleType`: must be 'car', 'motorcycle', or 'auto'
- `capacity`: minimum 1
- `color`, `plate`: minimum 3 characters


**Response:**
```json
{
  "token": "jwt-token-here",
  "captain": {
    "_id": "captain-id",
    "fullname": {
      "firstname": "Jane",
      "lastname": "Smith"
    },
    "email": "jane@example.com",
    "vehicle": {
      "color": "Black",
      "plate": "ABC-1234",
      "capacity": 4,
      "vehicleType": "car"
    },
    "status": "inactive"
  }
}
```

---

#### 2. Login Captain
**POST** `/captains/login`

**Request Body:**
```json
{
  "email": "jane@example.com",
  "password": "password123"
}
```

**Response:** Same as register

---

#### 3. Get Captain Profile
**GET** `/captains/profile`

**Headers:**
```
Authorization: Bearer <token>
```

**Response:**
```json
{
  "captain": {
    "_id": "captain-id",
    "fullname": {
      "firstname": "Jane",
      "lastname": "Smith"
    },
    "email": "jane@example.com",
    "vehicle": {
      "color": "Black",
      "plate": "ABC-1234",
      "capacity": 4,
      "vehicleType": "car"
    },
    "status": "active"
  }
}
```

---

#### 4. Logout Captain
**GET** `/captains/logout`

**Headers:**
```
Authorization: Bearer <token>
```

**Response:**
```json
{
  "message": "Logout successfully"
}
```

---

### Maps Endpoints

#### 1. Get Coordinates
**GET** `/maps/get-coordinates?address=<address>`

**Query Parameters:**
- `address`: Address string (minimum 3 characters)

**Headers:**
```
Authorization: Bearer <user-token>
```

**Response:**
```json
{
  "ltd": 37.4224764,
  "lng": -122.0842499
}
```

---

#### 2. Get Distance and Time
**GET** `/maps/get-distance-time?origin=<origin>&destination=<destination>`

**Query Parameters:**
- `origin`: Starting address (minimum 3 characters)
- `destination`: Destination address (minimum 3 characters)

**Headers:**
```
Authorization: Bearer <user-token>
```

**Response:**
```json
{
  "distance": {
    "text": "10.5 km",
    "value": 10500
  },
  "duration": {
    "text": "25 mins",
    "value": 1500
  }
}
```

---

#### 3. Get Autocomplete Suggestions
**GET** `/maps/get-suggestions?input=<input>`

**Query Parameters:**
- `input`: Search string (minimum 3 characters)

**Headers:**
```
Authorization: Bearer <user-token>
```

**Response:**
```json
[
  "123 Main Street, New York, NY, USA",
  "123 Main Avenue, Brooklyn, NY, USA",
  "123 Main Road, Queens, NY, USA"
]
```

---

### Ride Endpoints

#### 1. Create Ride
**POST** `/rides/create`

**Headers:**
```
Authorization: Bearer <user-token>
```

**Request Body:**
```json
{
  "pickup": "123 Main Street, New York",
  "destination": "456 Park Avenue, New York",
  "vehicleType": "car"
}
```

**Validation:**
- `pickup`: minimum 3 characters
- `destination`: minimum 3 characters
- `vehicleType`: must be 'auto', 'car', or 'moto'

**Response:**
```json
{
  "_id": "ride-id",
  "user": "user-id",
  "pickup": "123 Main Street, New York",
  "destination": "456 Park Avenue, New York",
  "fare": 150,
  "status": "pending",
  "otp": "123456"
}
```

---

#### 2. Get Fare Estimate
**GET** `/rides/get-fare?pickup=<pickup>&destination=<destination>`

**Query Parameters:**
- `pickup`: Pickup address (minimum 3 characters)
- `destination`: Destination address (minimum 3 characters)

**Headers:**
```
Authorization: Bearer <user-token>
```

**Response:**
```json
{
  "auto": 50,
  "car": 75,
  "moto": 40
}
```

---

#### 3. Confirm Ride (Captain)
**POST** `/rides/confirm`

**Headers:**
```
Authorization: Bearer <captain-token>
```

**Request Body:**
```json
{
  "rideId": "ride-id"
}
```

**Response:**
```json
{
  "_id": "ride-id",
  "user": { /* user details */ },
  "captain": { /* captain details */ },
  "pickup": "123 Main Street, New York",
  "destination": "456 Park Avenue, New York",
  "fare": 150,
  "status": "accepted",
  "otp": "123456"
}
```

---

#### 4. Start Ride (Captain)
**GET** `/rides/start-ride?rideId=<rideId>&otp=<otp>`

**Query Parameters:**
- `rideId`: MongoDB ObjectId
- `otp`: 6-digit OTP

**Headers:**
```
Authorization: Bearer <captain-token>
```

**Response:**
```json
{
  "_id": "ride-id",
  "user": { /* user details */ },
  "captain": { /* captain details */ },
  "pickup": "123 Main Street, New York",
  "destination": "456 Park Avenue, New York",
  "fare": 150,
  "status": "ongoing",
  "otp": "123456"
}
```

---

#### 5. End Ride (Captain)
**POST** `/rides/end-ride`

**Headers:**
```
Authorization: Bearer <captain-token>
```

**Request Body:**
```json
{
  "rideId": "ride-id"
}
```

**Response:**
```json
{
  "_id": "ride-id",
  "user": { /* user details */ },
  "captain": { /* captain details */ },
  "pickup": "123 Main Street, New York",
  "destination": "456 Park Avenue, New York",
  "fare": 150,
  "status": "completed"
}
```

---

## 🗺️ Frontend Routes

| Route | Component | Access | Description |
|-------|-----------|--------|-------------|
| `/` | Start | Public | Landing page |
| `/login` | UserLogin | Public | User login page |
| `/signup` | UserSignup | Public | User registration page |
| `/captain-login` | Captainlogin | Public | Captain login page |
| `/captain-signup` | CaptainSignup | Public | Captain registration page |
| `/home` | Home | Protected (User) | User dashboard for booking rides |
| `/riding` | Riding | Public | User's active ride page |
| `/user/logout` | UserLogout | Protected (User) | User logout handler |
| `/captain-home` | CaptainHome | Protected (Captain) | Captain dashboard |
| `/captain-riding` | CaptainRiding | Public | Captain's active ride page |
| `/captain/logout` | CaptainLogout | Protected (Captain) | Captain logout handler |

### Protected Routes

Routes wrapped in `UserProtectWrapper` or `CaptainProtectWrapper` require authentication:
- Check for valid JWT token in localStorage
- Verify token with backend
- Redirect to login if unauthorized

---

## ⚡ Real-Time Features

The application uses Socket.IO for real-time communication between users and captains.

### Socket Events

#### Client to Server

**1. join**
```javascript
socket.emit('join', {
  userId: 'user-id',
  userType: 'user' // or 'captain'
});
```
Joins the socket room and updates user/captain's socketId in database.

**2. update-location-captain**
```javascript
socket.emit('update-location-captain', {
  userId: 'captain-id',
  location: {
    ltd: 37.4224764,
    lng: -122.0842499
  }
});
```
Updates captain's real-time location in the database.

**3. disconnect**
Automatically triggered when client disconnects.

#### Server to Client

The backend uses `sendMessageToSocketId()` function to emit events to specific users:

```javascript
sendMessageToSocketId(socketId, {
  event: 'ride-confirmed',
  data: { ride: rideDetails }
});
```

Common events:
- `ride-confirmed` - When captain accepts a ride
- `ride-started` - When captain starts the ride
- `ride-ended` - When ride is completed
- `new-ride` - When a new ride request is available

---

## 💾 Database Schema

### User Model
```javascript
{
  fullname: {
    firstname: String (required, min: 3),
    lastname: String (min: 3)
  },
  email: String (required, unique, min: 5),
  password: String (required, hashed),
  socketId: String
}
```

### Captain Model
```javascript
{
  fullname: {
    firstname: String (required, min: 3),
    lastname: String (min: 3)
  },
  email: String (required, unique, valid email),
  password: String (required, hashed),
  socketId: String,
  status: String (enum: ['active', 'inactive'], default: 'inactive'),
  vehicle: {
    color: String (required, min: 3),
    plate: String (required, min: 3),
    capacity: Number (required, min: 1),
    vehicleType: String (required, enum: ['car', 'motorcycle', 'auto'])
  },
  location: {
    ltd: Number,
    lng: Number
  }
}
```

### Ride Model
```javascript
{
  user: ObjectId (ref: 'user', required),
  captain: ObjectId (ref: 'captain'),
  pickup: String (required),
  destination: String (required),
  fare: Number (required),
  status: String (enum: ['pending', 'accepted', 'ongoing', 'completed', 'cancelled'], default: 'pending'),
  duration: Number (seconds),
  distance: Number (meters),
  paymentID: String,
  orderId: String,
  signature: String,
  otp: String (required, 6 digits, not selected by default)
}
```

### BlacklistToken Model
```javascript
{
  token: String (required, unique),
  createdAt: Date (default: Date.now, expires: 86400) // Auto-deletes after 24 hours
}
```

---

## 🔒 Security Features

### Authentication & Authorization
- **JWT Tokens**: Stateless authentication with 24-hour expiration
- **Password Hashing**: bcrypt with salt rounds of 10
- **Token Blacklisting**: Invalidated tokens stored in database
- **Protected Routes**: Middleware checks for valid, non-blacklisted tokens
- **Role-based Access**: Separate authentication for users and captains

### Data Validation
- **express-validator**: Server-side validation for all inputs
- **Mongoose Schema Validation**: Database-level validation
- **Email Validation**: Regex pattern matching
- **Minimum Length Requirements**: Enforced for names, passwords, etc.

### Best Practices
- Environment variables for sensitive data
- CORS configuration
- Cookie parsing with security options
- Password fields excluded from query results by default
- OTP-based ride verification

---

## 🎨 Frontend Components

### User Components
- **LocationSearchPanel** - Search and select pickup/destination
- **VehiclePanel** - Select vehicle type (auto/car/moto)
- **ConfirmRide** - Review ride details before booking
- **LookingForDriver** - Waiting state while searching for captain
- **WaitingForDriver** - Display assigned captain details
- **LiveTracking** - Google Maps integration for real-time tracking

### Captain Components
- **CaptainDetails** - Display captain's earnings and stats
- **RidePopUp** - New ride request notification
- **ConfirmRidePopUp** - Accept ride and enter OTP
- **FinishRide** - Complete ride and navigate to next

### Context Providers
- **UserContext** - Global user state management
- **CaptainContext** - Global captain state management
- **SocketContext** - Socket.IO connection management

---

## 🔧 Configuration Files

### Vite Configuration (frontend/vite.config.js)
```javascript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
  server: {
    port: 5173,
    proxy: {
      '/api': 'http://localhost:3000'
    }
  }
})
```

### Tailwind Configuration (frontend/tailwind.config.js)
```javascript
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

---

## 🧪 Testing the Application

### Manual Testing Flow

**1. User Registration & Login**
```bash
# Register a new user
POST http://localhost:3000/users/register
# Login
POST http://localhost:3000/users/login
```

**2. Captain Registration & Login**
```bash
# Register a new captain
POST http://localhost:3000/captains/register
# Login
POST http://localhost:3000/captains/login
```

**3. Create a Ride (User)**
- Login as user in frontend
- Enter pickup location
- Enter destination
- Select vehicle type
- Confirm ride

**4. Accept Ride (Captain)**
- Login as captain in another browser/incognito
- View incoming ride request
- Accept the ride
- Enter OTP to start
- Complete the ride

---

## 🐛 Troubleshooting

### Common Issues

**1. MongoDB Connection Error**
```
Error: connect ECONNREFUSED 127.0.0.1:27017
```
**Solution:** 
- Ensure MongoDB is running: `mongod` or check MongoDB service
- Verify `DB_CONNECT` URL in `.env`
- Check if port 27017 is not blocked

**2. Google Maps API Error**
```
Error: Google Maps API key is invalid
```
**Solution:**
- Verify API key is correct in both backend and frontend `.env` files
- Ensure required APIs are enabled in Google Cloud Console
- Check API key restrictions and quotas

**3. CORS Error**
```
Access to XMLHttpRequest blocked by CORS policy
```
**Solution:**
- Verify CORS is enabled in `Backend/app.js`
- Check if `VITE_BASE_URL` in frontend matches backend URL
- Clear browser cache

**4. JWT Token Error**
```
Error: Unauthorized
```
**Solution:**
- Check if JWT_SECRET is set in backend `.env`
- Verify token is being sent in Authorization header
- Check if token is blacklisted (after logout)
- Token expires after 24 hours - login again

**5. Socket Connection Failed**
```
WebSocket connection failed
```
**Solution:**
- Ensure backend server is running
- Check `VITE_BASE_URL` in frontend `.env`
- Verify Socket.IO version compatibility
- Check firewall settings

**6. Environment Variable Not Loading**
```
undefined when accessing process.env.VARIABLE
```
**Solution:**
- Restart the development server after changing `.env`
- Ensure `.env` file is in the correct directory
- For frontend, variables must start with `VITE_`

---

## 📊 Fare Calculation Logic

The fare is calculated based on:

```javascript
// Base fare (per vehicle type)
baseFare = {
  auto: 30,
  car: 50,
  moto: 20
}

// Per kilometer rate
perKmRate = {
  auto: 10,
  car: 15,
  moto: 8
}

// Per minute rate
perMinuteRate = {
  auto: 2,
  car: 3,
  moto: 1.5
}

// Final calculation
fare = baseFare + (distance_in_km * perKmRate) + (duration_in_minutes * perMinuteRate)
```

---

## 🚀 Deployment

### Backend Deployment (Heroku/Railway/Render)

**1. Prepare for deployment:**
```bash
# Ensure package.json has start script
"scripts": {
  "start": "node server.js"
}
```

**2. Set environment variables on hosting platform:**
- `PORT` (usually auto-assigned)
- `DB_CONNECT` (MongoDB Atlas connection string)
- `JWT_SECRET`
- `GOOGLE_MAPS_API`
- `NODE_ENV=production`

**3. Deploy:**
```bash
git push heroku main
# OR use platform-specific deployment
```

### Frontend Deployment (Vercel/Netlify)

**1. Build the frontend:**
```bash
cd frontend
npm run build
```

**2. Set environment variables:**
- `VITE_BASE_URL` (your backend URL)
- `VITE_API_URL` (your backend URL)
- `VITE_GOOGLE_MAPS_API_KEY`

**3. Deploy:**
```bash
# Vercel
vercel --prod

# Netlify
netlify deploy --prod
```

### MongoDB Atlas Setup for Production

1. Create production cluster
2. Add IP whitelist: `0.0.0.0/0` (or specific IPs)
3. Create database user with strong password
4. Get connection string and update `DB_CONNECT`
5. Enable MongoDB Atlas network access controls

---

## 🔄 Development Workflow

### Adding New Features

1. **Backend Route:**
   - Add route in `routes/` directory
   - Create controller in `controllers/`
   - Add business logic in `services/`
   - Update model if needed in `models/`

2. **Frontend Page:**
   - Create page component in `src/pages/`
   - Add route in `App.jsx`
   - Create reusable components in `src/components/`
   - Update context if needed in `src/context/`

### Code Style
- Use ES6+ features
- Async/await for promises
- Error handling with try-catch
- Consistent naming conventions
- Comments for complex logic

---

## 📝 To-Do / Future Enhancements

- [ ] Payment integration (Stripe/Razorpay)
- [ ] Ride history for users and captains
- [ ] Rating and review system
- [ ] Push notifications
- [ ] Admin dashboard
- [ ] Ride cancellation with penalties
- [ ] Multiple stops in a single ride
- [ ] Scheduled rides
- [ ] Promo codes and discounts
- [ ] Email verification
- [ ] Phone number verification (OTP)
- [ ] Ride sharing option
- [ ] Driver background verification
- [ ] Insurance information
- [ ] Emergency SOS button
- [ ] Ride receipts via email
- [ ] Multi-language support
- [ ] Dark mode
- [ ] PWA support
- [ ] Unit and integration tests

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Contribution Guidelines
- Follow existing code style
- Write clear commit messages
- Add comments for complex logic
- Test your changes thoroughly
- Update documentation if needed

---

## 📄 License

This project is licensed under the ISC License - see the LICENSE file for details.

---

## 👥 Authors

- **Your Name** - Initial work

---

## 🙏 Acknowledgments

- Google Maps Platform for location services
- MongoDB for database
- Socket.IO for real-time communication
- React and Vite communities
- Express.js framework
- All open-source contributors

---

## 📞 Support

For support, email [your-email@example.com] or open an issue in the repository.

---

## 📸 Screenshots

### User Interface
- Landing Page
- User Login/Signup
- Ride Booking Interface
- Live Tracking
- Ride Completion

### Captain Interface
- Captain Dashboard
- Ride Requests
- Active Ride
- Navigation

*(Add screenshots of your application here)*

---

## 🔗 Links

- [Backend API Documentation](./Backend/README.md)
- [Google Maps Platform](https://console.cloud.google.com/)
- [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
- [Socket.IO Documentation](https://socket.io/docs/)
- [React Documentation](https://react.dev/)
- [Express Documentation](https://expressjs.com/)

---

**Made with ❤️ using React, Node.js, MongoDB, and Socket.IO**
