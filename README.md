# UTISHTA | Emergency Response Platform

**Status:** Prototype  
**Tech Stack:** React 19, Vite, Tailwind CSS  

> **"Rise to the occasion."**  
> A next-generation emergency response coordination prototype designed to reduce ambulance response times through real-time tracking and ultra-efficient dispatching.

## ⭐ OVERVIEW
Utishtha is a high-fidelity frontend prototype that simulates a complete emergency response ecosystem. It connects:
1. Patients in distress
2. Ambulance Drivers
3. Central Dispatchers

Built with a Mission Control aesthetic featuring glassmorphism UI, fluid animations, and smooth state transitions.

## 🚨 KEY FEATURES

### 1. Dispatcher Console (Admin)
- Real-time map visualization  
- Live metrics (Active Trips, Response Time, Fleet Availability)  
- Incident Feed with severity levels  
- System Architecture modal (FastAPI/PostgreSQL/Redis plan)

### 2. Driver Application (Mobile Simulation)
- Job Offer modal with countdown & auto-decline  
- Status control (Idle, Busy, Navigating)  
- Simulated navigation + arrival flow  

### 3. Patient Application (Mobile Simulation)
- One-tap SOS  
- Live progress tracking  
- Driver ETA + details  

## 🛠️ TECH STACK & DESIGN
- React 19 + Vite  
- Tailwind CSS  
- Framer Motion  
- Inter + JetBrains Mono  
- Lucide Icons  
- Custom glassmorphism utilities

## 🚀 GETTING STARTED
```bash
git clone https://github.com/vishnunambiar0602/utishtha.git
cd utishtha
npm install
npm run dev
```

Visit http://localhost:5173

## 📁 PROJECT STRUCTURE
```
src/
├── assets/
├── components/
│   ├── admin/
│   ├── common/
│   ├── layout/
│   └── mobile/
│       └── driver/
├── lib/
│   └── mockData.js
├── App.jsx
├── index.css
└── main.jsx
```

## 🎨 COLOR PALETTE
Primary: #3A8DFF  
Accent: #5AF2FF  
Danger: #E74C3C  
Success: #2ECC71  
Background: #020617  

## 🧭 FUTURE ROADMAP
- FastAPI WebSockets backend  
- Mapbox GL JS real maps  
- JWT auth  
- AI routing for dispatch  

## 📄 LICENSE
MIT License
