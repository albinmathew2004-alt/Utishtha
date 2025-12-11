# Backend Implementation Plan - Utishta Emergency Platform

## 1. Architecture Overview

The backend will be built using the **MERN Stack** (MongoDB, Express.js, React, Node.js) with **Socket.io** for real-time communication. This ensures low-latency updates for tracking ambulances and dispatching requests.

### Tech Stack
-   **Runtime**: Node.js
-   **Framework**: Express.js
-   **Database**: MongoDB (via Mongoose)
-   **Real-time Engine**: Socket.io (crucial for live tracking)
-   **Authentication**: JSON Web Tokens (JWT)

---

## 2. Directory Structure

We will create a new `server` directory at the root of the project to keep the backend separate from the frontend (`src`).

```text
utishta-emergency-platform/
├── server/                 <-- NEW DIRECTORY
│   ├── config/
│   │   └── db.js           # Database connection logic
│   ├── controllers/        # Business logic for routes
│   │   ├── authController.js
│   │   ├── driverController.js
│   │   └── requestController.js
│   ├── middleware/
│   │   └── auth.js         # JWT verification middleware
│   ├── models/             # Mongoose Schemas
│   │   ├── User.js         # Admin/Patient users
│   │   ├── Driver.js       # Ambulance drivers (with current location)
│   │   └── Request.js      # Emergency requests
│   ├── routes/             # API Endpoints
│   │   ├── authRoutes.js
│   │   ├── driverRoutes.js
│   │   └── requestRoutes.js
│   ├── sockets/            # Socket.io handlers
│   │   └── socketManager.js # Manages real-time events
│   ├── .env                # Environment variables (MONGO_URI, JWT_SECRET)
│   ├── server.js           # Entry point
│   └── package.json        # Backend dependencies
├── src/                    # Existing Frontend
└── package.json            # Root (Frontend) dependencies
```

---

## 3. Key Components & Implementation Details

### A. Database Models (`server/models`)

1.  **Driver.js**
    -   `name`, `phone`, `licensePlate`
    -   `status` (enum: 'available', 'busy', 'offline')
    -   `location`: { `lat`: Number, `lng`: Number } (GeoJSON structure recommended)
    -   `fcmToken` (for push notifications, optional but good for future)

2.  **Request.js**
    -   `patientId` (or anonymous details if guest)
    -   `location`: { `lat`, `lng` }
    -   `status` (enum: 'pending', 'assigned', 'picked_up', 'completed')
    -   `assignedDriverId` (Reference to Driver)

### B. Real-time Communication (`server/sockets`)

We will use **Socket.io** to handle:
1.  **Driver Location Updates**:
    -   Driver app emits `driverLocationUpdate` every 3-5 seconds.
    -   Server broadcasts this to the **Admin Dispatch Console** room.
2.  **Dispatch Alerts**:
    -   Admin triggers dispatch.
    -   Server emits `newRequestAssignment` to the specific Driver's socket ID.
3.  **Request Status**:
    -   Patient tracks status via `requestStatusUpdate` events (e.g., "Ambulance on the way").

### C. API Endpoints (`server/routes`)

-   **Auth**:
    -   `POST /api/auth/driver/login`
    -   `POST /api/auth/admin/login`
-   **Drivers**:
    -   `GET /api/drivers/available` (Get nearest available drivers)
    -   `PUT /api/drivers/status` (Toggle duty status)
-   **Requests**:
    -   `POST /api/requests` (Create new emergency request)
    -   `PUT /api/requests/:id/assign` (Admin assigns driver)

---

## 4. Implementation Steps

### Phase 1: Setup
1.  Create `server` folder.
2.  Run `npm init -y` inside `server`.
3.  Install dependencies:
    ```bash
    npm install express mongoose socket.io cors dotenv jsonwebtoken bcryptjs
    npm install --save-dev nodemon
    ```

### Phase 2: Database & Server Core
1.  Setup MongoDB Atlas (free tier) or local instance.
2.  Create `server.js` and connect to DB.
3.  Initialize Socket.io server instance attached to the HTTP server.

### Phase 3: Driver Logic
1.  Create `Driver` model.
2.  Implement Socket events for `joinDriverRoom` and `updateLocation`.
3.  Test location stream from a mock client.

### Phase 4: Integration
1.  Update Frontend **Admin Console** to listen to `driverLocationUpdate` and render markers.
2.  Update Frontend **Driver View** to emit location and listen for `newRequestAssignment`.

---

## 5. Frontend Integration Changes

You will need to install `socket.io-client` in the main project:
```bash
npm install socket.io-client
```

**New Helper File**: `src/services/socket.js`
This will manage the single socket connection to ensure we don't open multiple connections.
