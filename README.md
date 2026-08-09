# FitHub AI — AI Fitness Coach & Admin Panel

A complete, production-ready **Next.js frontend** for an AI-powered fitness coaching platform. It includes a full end-user experience (AI onboarding, diet & workout plans, habit tracking, AI chatbot, progress tracking) and a comprehensive **admin panel** (user management, analytics, AI output monitoring, image moderation, plan overrides, chat moderation, logs, settings).

> This is the **frontend only**. All data is served from a mock data layer (`src/lib/data.ts`) that simulates the MongoDB backend described in the product spec. The UI is fully interactive with simulated AI responses and state management.

---

## Tech Stack

| Layer        | Technology                                            |
| ------------ | ----------------------------------------------------- |
| Framework    | Next.js 16 (App Router, Turbopack)                     |
| Language     | TypeScript                                            |
| Styling      | Tailwind CSS v4 (`@theme` + CSS custom properties)    |
| UI Patterns  | shadcn-style custom components (no runtime dependency) |
| Charts       | Recharts (Area, Line, Bar, Pie, RadialBar)            |
| Icons        | lucide-react                                          |
| Theming      | next-themes (light / dark, class-based)               |
| Animation    | framer-motion + custom CSS keyframes                  |

---

## Getting Started

```bash
# 1. Install dependencies
npm install

# 2. Run the dev server
npm run dev
# → http://localhost:3000

# 3. Build for production
npm run build && npm start
```

Requires Node.js 18.18+ (Node 20 recommended).

---

## Project Structure

```
src/
├── app/
│   ├── page.tsx                 # Landing page
│   ├── login/                   # Login (User + Admin demo)
│   ├── signup/                  # Signup
│   ├── layout.tsx               # Root layout (ThemeProvider, fonts)
│   ├── globals.css              # Design system + Tailwind v4 theme
│   ├── dashboard/page.tsx       # User dashboard
│   ├── onboarding/page.tsx      # AI body analysis (MediaPipe simulation)
│   ├── goals/page.tsx           # Goal selection
│   ├── diet/page.tsx            # AI diet plan
│   ├── workout/page.tsx         # AI workout plan
│   ├── habits/page.tsx          # Daily habit tracker
│   ├── chat/page.tsx            # AI coach chat (RAG)
│   ├── progress/page.tsx        # Weekly progress + insights
│   └── admin/
│       ├── page.tsx             # Analytics dashboard
│       ├── users/               # User management
│       ├── ai-outputs/          # AI output monitoring + prompt templates
│       ├── images/              # Image moderation
│       ├── plans/               # Plan management (override system)
│       ├── chats/               # Chat moderation
│       ├── logs/                # Reports & logs
│       └── settings/            # Admin settings
├── components/
│   ├── ui/                      # Button, Card, Badge, Input, Table,
│   │                            #   Progress, Avatar, Modal, StatCard
│   ├── dashboard-shell.tsx      # Sidebar layout (user/admin roles)
│   ├── charts.tsx               # Reusable Recharts components
│   ├── theme-provider.tsx
│   └── theme-toggle.tsx
└── lib/
    ├── data.ts                  # Centralized mock data (all collections)
    └── utils.ts                 # cn(), date helpers
```

---

## Routes

### User Side (`/dashboard/*`)
| Route          | Description                                              |
| -------------- | -------------------------------------------------------- |
| `/dashboard`   | Overview: weight, calories, streak, fitness score, charts|
| `/onboarding`  | 4-angle photo upload + simulated MediaPipe pose analysis |
| `/goals`       | Goal selection (loss/gain/muscle/maintenance) + details  |
| `/diet`        | AI-generated diet plan with macros & 5 meals             |
| `/workout`     | 7-day workout split (Gym/Home) with exercise detail      |
| `/habits`      | Daily habit tracker with streak + weekly chart           |
| `/chat`        | AI coach chat (RAG context banner, suggestions)          |
| `/progress`    | Weekly progress charts, before/after, AI insights        |

### Admin Panel (`/admin/*`)
| Route              | Description                                                |
| ------------------ | ---------------------------------------------------------- |
| `/admin`           | Analytics: users, DAU/WAU, AI usage, token budget          |
| `/admin/users`     | User management table, ban/deactivate, detail modal        |
| `/admin/ai-outputs`| AI output monitoring + prompt template editor              |
| `/admin/images`    | Image moderation grid, approve/flag/delete                 |
| `/admin/plans`     | Plan templates + override/assign system                    |
| `/admin/chats`     | Chat moderation, conversation viewer, block user           |
| `/admin/logs`      | System logs table, token usage chart, health metrics       |
| `/admin/settings`  | AI config, moderation toggles, API keys, danger zone       |

---

## Design System

- **Brand color:** Purple `#7c3aed` with gradient `from-violet-600 to-fuchsia-600`
- **Light/Dark theme:** Full CSS custom property system, toggle in sidebar
- **Components:** Glassmorphism cards, gradient buttons, animated modals
- **Responsive:** Mobile sidebar drawer, adaptive grids

---

## Notes

- The AI body analysis uses **SVG skeleton overlays** to simulate MediaPipe pose landmarks since real computer vision runs server-side.
- All admin and user data comes from `src/lib/data.ts` — swap this for real API calls to a Node/Express + MongoDB backend to go live.
- Login page offers a **"Continue as Admin (demo)"** button to jump straight to the admin panel.
