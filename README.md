UTISHTA | Emergency Response Platform
=====================================

Status: Prototype
Tech Stack: React 19, Vite, Tailwind CSS

"Rise to the occasion."
A next-generation emergency response coordination prototype designed to reduce ambulance response times through real-time tracking and efficient dispatching.

--------------------------------------------------------------------------------
OVERVIEW
--------------------------------------------------------------------------------
Utishtha is a high-fidelity frontend prototype that simulates a complete emergency response ecosystem. It demonstrates a unified platform connecting three critical stakeholders:
1. Patients in distress
2. Ambulance Drivers
3. Central Dispatchers

Built with a modern "Mission Control" aesthetic, the application features glassmorphism UI, fluid animations, and interactive state management to showcase the intended user experience of a life-saving application.

--------------------------------------------------------------------------------
KEY FEATURES
--------------------------------------------------------------------------------

1. Dispatcher Console (Admin)
   A "Mission Control" style dashboard for managing fleet operations.
   - Real-time Visualization: Interactive map area simulating driver locations and active incidents.
   - Live Metrics: Heads-up display for Active Trips, Average Response Time, and Fleet Availability.
   - Incident Feed: Live list of incoming emergency requests classified by severity (Critical, High, Medium).
   - System Architecture: Built-in modal visualizing the intended FastAPI/PostgreSQL/Redis backend infrastructure.

2. Driver Application (Mobile Simulation)
   A focused interface designed for rapid response.
   - Job Offer System: Interactive incoming request modal with a countdown timer (auto-decline logic).
   - Status Management: Toggle between "Idle" and "Busy/Navigating" states.
   - Navigation UI: Simulated turn-by-turn navigation screen with patient details and "Arrived" actions.

3. Patient Application (Mobile Simulation)
   A simplified, panic-proof interface for users.
   - One-Tap SOS: Prominent emergency button with pulse animations.
   - Live Status: Progress tracking from "Finding nearest ambulance" to "Driver Found".
   - Driver Tracking: Simulated driver details, ETA, and vehicle information.

--------------------------------------------------------------------------------
TECH STACK & DESIGN
--------------------------------------------------------------------------------

Core Framework:
- Runtime: React 19 + Vite (for fast HMR)
- Routing: Custom state-based view switching for seamless role transitions

UI & UX:
- Styling: Tailwind CSS with custom colors (Medical Blue, Neon Cyan, Emergency Red)
- Glassmorphism: Custom utility classes (.glass-panel, .glass-card) for translucent aesthetics
- Typography: 'Inter' for UI elements and 'JetBrains Mono' for data
- Animations: Framer Motion for complex transitions and modal popups
- Icons: Lucide React

--------------------------------------------------------------------------------
GETTING STARTED
--------------------------------------------------------------------------------

Prerequisites:
- Node.js (v16+)
- npm

Installation:

1. Clone the repository
   git clone https://github.com/vishnunambiar0602/utishtha.git
   cd utishtha

2. Install dependencies
   npm install

3. Run the development server
   npm run dev

4. Launch
   Open your browser and navigate to the local URL provided (usually http://localhost:5173).

--------------------------------------------------------------------------------
PROJECT STRUCTURE
--------------------------------------------------------------------------------

src/
├── assets/            # Static assets
├── components/
│   ├── admin/         # Dispatcher Console components (Map, Stats, Sidebar)
│   ├── common/        # Shared modals and UI elements
│   ├── layout/        # Landing page and wrappers
│   └── mobile/        # Mobile app simulations
│       └── driver/    # Driver specific screens (Job Offer, Nav)
├── lib/
│   └── mockData.js    # Simulation data for drivers and requests
├── App.jsx            # Main view controller
├── index.css          # Global styles & Tailwind directives
└── main.jsx           # Entry point

--------------------------------------------------------------------------------
COLOR PALETTE
--------------------------------------------------------------------------------

Primary:    #3A8DFF (Medical Blue)
Accent:     #5AF2FF (Neon Cyan)
Danger:     #E74C3C (Emergency Red)
Success:    #2ECC71
Background: #020617 (Slate 950)

--------------------------------------------------------------------------------
FUTURE ROADMAP
--------------------------------------------------------------------------------

- Backend Integration: Connect Client Apps to the Python (FastAPI) backend via WebSockets.
- Live Maps: Replace SVG mock maps with Mapbox GL JS integration.
- Auth: Implement JWT authentication for Drivers and Admins.
- AI Routing: Integrate pathfinding algorithms for optimal ambulance dispatch.

--------------------------------------------------------------------------------
LICENSE
--------------------------------------------------------------------------------

Distributed under the MIT License.
