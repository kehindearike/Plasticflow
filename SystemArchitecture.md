#  Plasticflow Mobile App System Architecture

Plasticflow is a mobile app designed to connect users, collectors, and recycling centers in real time through a central backend API. The architecture ensures scalability, responsiveness, and a smooth user experience.

---

##  Overview
The system follows a **three-tier architecture**:

1. **Frontend (Client-side)** – React Native mobile app  
2. **Backend (Server-side)** – Node.js + Express REST API  
3. **Database (Data Layer)** – MongoDB hosted on MongoDB Atlas  

---

##  Frontend (Mobile App)
- **Framework:** React Native (can also use Flutter or native iOS/Android)  
- **Purpose:** Provides a responsive and intuitive interface for all user types — individuals, collectors, and recycling centers.  
- **Key Components:**
  - Login & Registration screens  
  - User dashboard (pickup scheduling, tracking)  
  - Collector dashboard (available requests, accepted pickups)  
  - Waste guide and recycling center listings  
  - Notifications for pickup updates  
- **Communication:** Makes API calls (Axios or Fetch) to the backend via HTTPS.  
- **Data Handling:** Stores JWT tokens securely on the device (SecureStore, Keychain, or SharedPreferences).  

---

##  Backend
- **Framework:** Node.js with Express  
- **Purpose:** Handles all business logic, authentication, scheduling, and communication between mobile app and database.  
- **Key Modules:**
  - **Auth Controller:** Signup/login with JWT-based authentication  
  - **Pickup Controller:** Manage pickup requests, assignments, and tracking  
  - **Collector Controller:** Handle collectors and accepted requests  
  - **Recycling Center Controller:** Manage centers and plastic delivery logs  

**API Endpoints Example:**
- `POST /auth/signup` → Register a new user  
- `POST /auth/login` → Login user and return JWT  
- `GET /pickups` → List pickups for a user  
- `POST /pickups` → Create a new pickup request  
- `PATCH /pickups/:id/assign` → Assign pickup to collector  

---

##  Database (MongoDB)
- **Collections and Sample Fields:**
  - **Users:** `{ id, name, email, role, passwordHash, createdAt }`  
  - **Pickups:** `{ id, userId, collectorId, status, scheduledAt }`  
  - **Collectors:** `{ id, name, vehicle, location }`  
  - **RecyclingCenters:** `{ id, name, address, acceptedMaterials }`  

---

##  How Components Communicate
1. Mobile app sends requests to backend API (HTTPS).  
2. Backend processes requests and interacts with the database.  
3. Backend responds with data to the mobile app.  
4. Mobile app updates UI and triggers notifications as needed.  

---

## ##  Technical Feasibility
This architecture is technically feasible because:
- It supports scalability for a growing user base.
- It provides secure authentication (JWT) and device-level encryption.
- The API-based backend allows both web and mobile clients to use the same infrastructure.
- It is easy to maintain and extend as new features are added.
  

---
