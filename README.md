# 🚛 Ashtavinayak Roadlines — Fleet Management Portal

<div align="center">

![Ashtavinayak Roadlines](https://img.shields.io/badge/Ashtavinayak-Roadlines-E8600C?style=for-the-badge&logo=truck&logoColor=white)
![Version](https://img.shields.io/badge/Version-1.0.0-0F1C3F?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Live-16a34a?style=for-the-badge)
![GPS](https://img.shields.io/badge/GPS-Wheels_Eye-2563eb?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-c8922a?style=for-the-badge)

**A full-stack fleet management web portal for real-time truck tracking, trip management, driver communication, and expense logging — powered by Wheels Eye GPS.**

[🚀 Live Demo](#) · [📋 Features](#-features) · [⚙️ Installation](#️-installation) · [📡 GPS Integration](#-wheels-eye-gps-integration) · [🗄️ Database](#️-database-schema)

</div>

---

## 📸 Screenshots

| Login | Admin Dashboard | Live GPS Tracking |
|---|---|---|
| 3-role login (Admin / Driver / Member) | Stats, trips, fleet fuel status | Wheels Eye map with animated truck pins |

| Trip Management | Messaging | Reports |
|---|---|---|
| Add/edit trips with progress | Admin ↔ Driver real-time chat | Revenue, profit per truck |

---

## ✨ Features

### 🛡️ Admin (Owner) — Full Access
| Feature | Description |
|---|---|
| 📊 Dashboard | Active trips, trucks running, revenue (₹), pending balance, fuel status of all trucks |
| 📍 Live GPS Tracking | Wheels Eye map — all trucks pinned with real-time lat/long, speed, fuel %, last location |
| 🚚 Trip Management | Create/edit trips: truck, driver, cargo, client, freight, advance. Progress bar per trip |
| 🚛 Fleet Panel | All trucks — Wheels Eye Device ID, model, insurance/permit expiry, fuel level |
| 👨‍✈️ Driver Management | Driver profiles with license, phone, total trips. Message/call actions |
| 👥 Member Management | Team members with roles. Invite new staff |
| 💬 Messaging | 1-to-1 and group chat with all drivers. Real-time message send |
| 📊 Reports | Revenue & profit per truck, monthly analytics. Export PDF/Excel |
| 🧾 Expenses | Fuel, toll, repair expenses logged per trip with receipt photo |
| 📁 Documents | RC, Insurance, Permits, DL, Lorry Receipts — upload, view, download |

### 🚛 Driver — My Trip & Communication
| Feature | Description |
|---|---|
| 🗺️ My Trip | Active trip overview — cargo, client, freight, advance, balance due, progress bar |
| 📍 Share Location | One-tap GPS location share to admin via Wheels Eye |
| 💬 Message Admin | Chat directly with admin from phone |
| 🧾 Log Expense | Log fuel, toll, repair with photo receipt — syncs to admin dashboard |
| ✅ Mark Delivered | Mark trip as delivered; triggers POD upload prompt |
| 📁 Documents | View own RC, license, and trip documents |

### 👥 Member (Staff) — View & Track
| Feature | Description |
|---|---|
| 📊 Dashboard | Overview of running trips, fleet stats, recent activity |
| 🚚 Trip Records | View all trips — status, progress, freight details |
| 🚛 Fleet View | All trucks with GPS status, fuel, Wheels Eye ID |
| 📍 Live Tracking | View all trucks on GPS map (read-only) |
| 💬 Messages | Communicate with admin and drivers |

---

## 🛠️ Tech Stack

| Layer | Technology | Tool / Library | Purpose |
|---|---|---|---|
| **Frontend** | React.js 18 | Tailwind CSS, Recharts | SPA — role-based UI |
| **Frontend** | Leaflet.js | react-leaflet | Live GPS map display |
| **Frontend** | Socket.IO Client | socket.io-client | Real-time messaging |
| **Backend** | Node.js + Express | express, cors, helmet | REST API + WebSocket server |
| **Backend** | Wheels Eye API | axios (polling 30s) | Live GPS data & webhooks |
| **Backend** | Socket.IO Server | socket.io | Driver–Admin chat |
| **Database** | PostgreSQL | Prisma ORM | All persistent data |
| **Cache** | Redis | ioredis | GPS cache, sessions, queues |
| **Auth** | JWT | jsonwebtoken, bcrypt | Role-based access control |
| **Auth** | Firebase OTP | firebase-admin | Driver phone login |
| **Hosting** | Vercel | — | Frontend deployment |
| **Hosting** | Railway / DigitalOcean | — | Backend deployment |
| **Storage** | Supabase | PostgreSQL managed | Production database |
| **Storage** | Cloudinary | cloudinary SDK | Document & image uploads |

---

## ⚙️ Installation

### Prerequisites
- Node.js 18+
- PostgreSQL 14+ (or [Supabase](https://supabase.com) account)
- Redis 7+ (local or [Redis Cloud](https://redis.io/cloud/))
- [Wheels Eye](https://wheelseyeapp.com) API credentials
- Git

### 1. Clone & Install

```bash
# Clone the repository
git clone https://github.com/yourusername/ashtavinayak-roadlines.git
cd ashtavinayak-roadlines

# Install backend dependencies
cd backend && npm install

# Install frontend dependencies
cd ../frontend && npm install
```

### 2. Environment Variables

Create a `.env` file inside the `backend/` folder:

```env
# Database
DATABASE_URL=postgresql://user:password@localhost:5432/ashtavinayak_db

# Redis
REDIS_URL=redis://localhost:6379

# JWT
JWT_SECRET=your_very_strong_random_secret_here
JWT_REFRESH_SECRET=another_strong_secret

# Wheels Eye GPS
WHEELS_EYE_API_KEY=your_wheels_eye_api_key
WHEELS_EYE_BASE_URL=https://api.wheelseyeapp.com/v1

# Cloudinary (Document uploads)
CLOUDINARY_URL=cloudinary://api_key:api_secret@cloud_name

# Firebase (Driver OTP login)
FIREBASE_PROJECT_ID=your-firebase-project-id
FIREBASE_PRIVATE_KEY=your-private-key

# Server
PORT=5000
NODE_ENV=development
```

Create a `.env` file inside `frontend/`:

```env
REACT_APP_API_URL=http://localhost:5000/api
REACT_APP_SOCKET_URL=http://localhost:5000
```

### 3. Database Setup

```bash
cd backend

# Run Prisma migrations
npx prisma migrate dev --name init

# Seed demo data
npx prisma db seed
```

### 4. Run Locally

```bash
# Terminal 1 — Backend (port 5000)
cd backend && npm run dev

# Terminal 2 — Frontend (port 3000)
cd frontend && npm start
```

Open: **http://localhost:3000**

---

## 🔑 Demo Login Credentials

| Role | Email / Username | Password |
|---|---|---|
| 🛡️ **Admin (Owner)** | `admin@ashtavinayak` | `admin123` |
| 🚛 **Driver** | `driver@ashtavinayak` | `driver123` |
| 👥 **Member (Staff)** | `member@ashtavinayak` | `member123` |

> ⚠️ Change all credentials before deploying to production.

---

## 📡 Wheels Eye GPS Integration

The portal integrates with **[Wheels Eye](https://wheelseyeapp.com)** as the GPS tracking provider.  
Each truck must have a Wheels Eye device physically installed and registered in the portal.

### How It Works

```
Wheels Eye Device (in truck)
        │
        ▼
Wheels Eye Cloud API ──── REST Poll (every 30s) ──▶ Backend (Node.js)
        │                                                   │
        └── Webhooks (alerts) ─────────────────────────────┤
                                                            │
                                                     Redis Cache (60s TTL)
                                                            │
                                                     Frontend (React)
                                                     Leaflet.js Map
                                                     (auto-refresh 30s)
```

### API Endpoints Used

| Method | Endpoint | Purpose |
|---|---|---|
| `GET` | `/vehicles` | List all registered vehicles |
| `GET` | `/vehicles/{id}/location` | Get single vehicle live location |
| `GET` | `/vehicles/{id}/history` | Trip route history / playback |
| `POST` | `/webhooks/register` | Register alert webhooks |
| `GET` | `/vehicles/{id}/reports/fuel` | Fuel consumption reports |
| `GET` | `/vehicles/{id}/reports/distance` | Distance & mileage reports |

### Webhook Alerts Supported
- 🔴 **Ignition ON / OFF**
- ⚡ **Geofence breach** (entry/exit)
- 🚨 **Overspeeding** (threshold configurable)
- 🔋 **Low battery** on GPS device
- 📍 **Trip start / end** detection

---

## 🗄️ Database Schema

```
users          → Admin, Driver, Member accounts (RBAC)
trucks         → Fleet — model, Wheels Eye Device ID, documents, fuel
trips          → Trip records — origin, destination, cargo, client, freight
drivers        → Driver profiles linked to users + trucks
expenses       → Fuel, toll, repair per trip with receipt photos
messages       → Chat messages between users
documents      → RC, Insurance, Permits, DL, Lorry Receipts (Cloudinary)
activity_log   → All actions logged for audit trail
```

Full schema with migrations available in `backend/prisma/schema.prisma`.

---

## 🔌 REST API Reference

| Method | Endpoint | Role | Description |
|---|---|---|---|
| `POST` | `/api/auth/login` | All | Login — returns JWT tokens |
| `POST` | `/api/auth/register` | All | Register new user |
| `GET` | `/api/trips` | Admin / Member | List all trips |
| `POST` | `/api/trips` | Admin | Create new trip |
| `PUT` | `/api/trips/:id` | Admin | Update trip details |
| `GET` | `/api/trips/active` | Driver | Get driver's active trip |
| `GET` | `/api/fleet` | All | All trucks with GPS status |
| `POST` | `/api/fleet` | Admin | Add new truck |
| `GET` | `/api/gps/live` | All | Live positions of all trucks |
| `GET` | `/api/gps/:id/history` | Admin | Route history for a truck |
| `GET` | `/api/drivers` | Admin | All driver profiles |
| `GET` | `/api/messages/:chatId` | All | Chat messages |
| `POST` | `/api/messages` | All | Send message |
| `POST` | `/api/expenses` | Driver / Admin | Log expense |
| `GET` | `/api/reports/revenue` | Admin | Revenue report |
| `POST` | `/api/upload` | All | Upload document / receipt |

---

## 📁 Folder Structure

```
ashtavinayak-roadlines/
│
├── frontend/                        # React.js SPA
│   ├── public/
│   └── src/
│       ├── components/              # Reusable UI components
│       │   ├── Navbar.jsx
│       │   ├── Sidebar.jsx
│       │   ├── TruckPinMap.jsx      # Leaflet GPS map
│       │   └── ChatWindow.jsx
│       ├── pages/
│       │   ├── Login.jsx
│       │   ├── Dashboard.jsx
│       │   ├── Tracking.jsx         # Live GPS page
│       │   ├── Trips.jsx
│       │   ├── Fleet.jsx
│       │   ├── Drivers.jsx
│       │   ├── Messages.jsx
│       │   ├── Reports.jsx
│       │   ├── Expenses.jsx
│       │   └── Documents.jsx
│       ├── context/
│       │   ├── AuthContext.js
│       │   └── SocketContext.js
│       └── api/
│           └── index.js             # Axios API wrappers
│
├── backend/                         # Node.js + Express API
│   ├── routes/
│   │   ├── auth.js
│   │   ├── trips.js
│   │   ├── fleet.js
│   │   ├── gps.js                   # Wheels Eye integration
│   │   ├── messages.js
│   │   ├── expenses.js
│   │   ├── reports.js
│   │   └── upload.js
│   ├── controllers/                 # Business logic per route
│   ├── middleware/
│   │   ├── auth.js                  # JWT verify
│   │   ├── rbac.js                  # Role-based access control
│   │   └── rateLimiter.js
│   ├── services/
│   │   ├── wheelsEye.js             # GPS API poller + webhook handler
│   │   ├── cloudinary.js            # File upload service
│   │   └── redis.js                 # Cache service
│   ├── socket/
│   │   └── chat.js                  # Socket.IO chat server
│   ├── prisma/
│   │   ├── schema.prisma
│   │   ├── migrations/
│   │   └── seed.js
│   └── server.js
│
├── ashtavinayak_roadlines.html      # Standalone HTML demo
├── .env.example                     # Environment variable template
├── .gitignore
└── README.md                        # This file
```

---

## 🔒 Security

- ✅ Passwords hashed with **bcrypt** (salt rounds: 12) — never stored in plain text
- ✅ **JWT tokens** — 15-min access token + 7-day refresh token rotation
- ✅ **RBAC middleware** on every protected API route
- ✅ **Prisma ORM** parameterized queries — SQL injection proof
- ✅ **Rate limiting** — 100 requests/minute per IP (`express-rate-limit`)
- ✅ **Helmet.js** HTTP security headers on all responses
- ✅ **CORS** configured to allow only the production frontend domain
- ✅ Wheels Eye API key stored **server-side only** — never exposed to client
- ✅ File uploads validated — type whitelist (PDF, JPG, PNG) + max 10MB
- ✅ Driver **OTP login via Firebase** — no password needed on mobile

---

## 🚀 Deployment

### Frontend → Vercel

```bash
cd frontend
npm run build
# Push to GitHub → connect repo to Vercel → auto-deploy
```

### Backend → Railway

```bash
# Add Railway CLI
npm install -g @railway/cli
railway login
railway init
railway up
```

### Database → Supabase

```bash
# Get connection string from Supabase dashboard
# Update DATABASE_URL in Railway environment variables
npx prisma migrate deploy
```

---

## 📋 Known Issues (v1.0)

- [ ] GPS map uses simulated grid in HTML demo — requires actual Wheels Eye credentials for live tracking
- [ ] Messaging is session-based in demo — requires Socket.IO server in production
- [ ] File uploads show toast in demo — actual Cloudinary upload needs backend wired
- [ ] Report charts use static data — need backend API wiring for live data

---

## 🗺️ Roadmap (v2.0)

- [ ] 📱 Mobile app for drivers (React Native) with push notifications
- [ ] 💬 Automated WhatsApp alerts for delivery, POD, and payment reminders
- [ ] 🤖 AI-based route optimization to reduce fuel costs
- [ ] 📄 E-Way Bill generation integration
- [ ] 🌐 Customer portal for tracking their own consignments
- [ ] ⛽ Automated fuel log from Wheels Eye fuel sensor data
- [ ] 📊 Bulk trip import via Excel upload

---

## 🤝 Contributing

```bash
# Fork the repo, then:
git checkout -b feature/your-feature-name
git commit -m "feat: add your feature"
git push origin feature/your-feature-name
# Open a Pull Request
```

---

## 📞 Contact & Support

| | |
|---|---|
| 🏢 **Company** | Ashtavinayak Roadlines |
| 🌐 **Portal** | https://portal.ashtavinayak.in |
| 📧 **Admin Email** | admin@ashtavinayak.in |
| 📡 **GPS Provider** | [Wheels Eye](https://wheelseyeapp.com) |
| 🛠️ **Tech Support** | support@ashtavinayak.in |

---

## 📄 License

```
MIT License — © 2026 Ashtavinayak Roadlines
```

---

<div align="center">

**Made with ❤️ for Ashtavinayak Roadlines**

🚛 *Keep the wheels turning.*

</div>
