# ScriptForge AI — Multi-Agent Install Script Generator

> AI-powered installation script generation using multi-agent collaboration. Describe your environment, 7 AI agents collaborate to generate secure, OS-specific installation scripts automatically.

![ScriptForge AI](https://img.shields.io/badge/ScriptForge-AI-12b7e8?style=for-the-badge&logo=terminal)
![Next.js](https://img.shields.io/badge/Next.js-14-black?style=for-the-badge&logo=next.js)
![FastAPI](https://img.shields.io/badge/FastAPI-0.111-009688?style=for-the-badge&logo=fastapi)
![CrewAI](https://img.shields.io/badge/CrewAI-Multi--Agent-purple?style=for-the-badge)
![Gemini](https://img.shields.io/badge/Gemini-1.5%20Flash-4285F4?style=for-the-badge&logo=google)

---

## 🚀 Features

- **7 AI Agents** — Coordinator, OS Detection, Dependency, Security, Compatibility, Script Generator, Reporter
- **Multi-OS Support** — Ubuntu/Debian, Windows, macOS
- **Multi-Stack** — MERN, Python ML, DevOps, Java, Docker, Kubernetes, Custom
- **Output Formats** — Bash (.sh), PowerShell (.ps1), Docker Compose (.yml)
- **Security Validation** — Automatic detection of unsafe commands
- **JWT Authentication** — Secure login/signup with session management
- **Script History** — All scripts stored and searchable
- **Futuristic Dark UI** — Glassmorphism, animations, Framer Motion
- **Real-time Terminal** — Animated agent execution logs
- **Download Options** — Script file + Markdown documentation

---

## 🏗 Architecture

```
User → Frontend (Next.js 14)
         ↓
      FastAPI Backend
         ↓
    CrewAI Orchestrator
    ┌────────────────────────────────┐
    │ Coordinator Agent              │
    │   ↓                           │
    │ Dependency Analysis Agent     │
    │   ↓                           │
    │ OS Detection Agent            │
    │   ↓                           │
    │ Security Validation Agent     │
    │   ↓                           │
    │ Compatibility Agent           │
    │   ↓                           │
    │ Script Generator Agent        │
    │   ↓                           │
    │ Report Generation Agent       │
    └────────────────────────────────┘
         ↓
    Final Script Package → SQLite
```

---

## 📁 Project Structure

```
infi/
├── frontend/                 # Next.js 14 App
│   ├── app/
│   │   ├── page.tsx          # Landing page
│   │   ├── login/            # Login page
│   │   ├── signup/           # Signup page
│   │   ├── dashboard/        # Main dashboard
│   │   ├── generate/         # Script generator
│   │   ├── history/          # Script history
│   │   ├── profile/          # User profile
│   │   └── admin/            # Admin panel
│   ├── components/
│   │   ├── ui/               # Button, Input, Card, Badge, Select
│   │   ├── layout/           # Sidebar, DashboardLayout
│   │   ├── dashboard/        # StatsCard, RecentScripts
│   │   └── script/           # AgentTerminal, ScriptViewer
│   ├── services/api.ts        # Axios API client
│   ├── hooks/useAuth.ts       # Auth state (Zustand)
│   └── utils/time.ts          # Date formatting
│
└── backend/                   # FastAPI App
    ├── main.py                 # App entry point
    ├── config.py               # Settings
    ├── database.py             # Async SQLAlchemy
    ├── agents/                 # 7 CrewAI agents
    ├── tasks/                  # CrewAI task definitions
    ├── api/                    # Route handlers
    ├── models/                 # SQLAlchemy models
    ├── services/               # Business logic
    └── utils/                  # Utilities
```

---

## ⚙️ Setup

### Prerequisites
- Node.js 18+
- Python 3.11+
- Gemini API key

### Backend

```bash
cd backend
python -m venv venv
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

pip install -r requirements.txt
cp .env.example .env
# Edit .env — add your GEMINI_API_KEY

python main.py
# API available at http://localhost:8000
# Docs at http://localhost:8000/docs
```

### Frontend

```bash
cd frontend
npm install
cp .env.local.example .env.local
# Edit .env.local if backend is not on localhost:8000

npm run dev
# App available at http://localhost:3000
```

---

## 🔑 Environment Variables

### Backend (`backend/.env`)
```env
SECRET_KEY=your-secret-key
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=60
DATABASE_URL=sqlite+aiosqlite:///./app.db
GEMINI_API_KEY=your-gemini-api-key
```

### Frontend (`frontend/.env.local`)
```env
NEXT_PUBLIC_API_URL=http://localhost:8000
```

---

## 🌐 API Reference

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/signup` | Create account |
| POST | `/api/auth/login` | Login (returns JWT) |
| GET | `/api/auth/me` | Current user |
| POST | `/api/generate-script` | Generate script (AI) |
| POST | `/api/analyze-request` | Quick analysis |
| POST | `/api/validate-script` | Security validate |
| GET | `/api/history` | Script history |
| GET | `/api/history/{id}` | Script detail |
| DELETE | `/api/history/{id}` | Delete script |
| GET | `/api/download-script/{id}` | Download script |
| GET | `/api/admin/stats` | Admin stats |
| GET | `/api/admin/users` | User list |

Interactive docs: `http://localhost:8000/docs`

---

## 🤖 Sample Prompts

1. "Set up a MERN stack development environment on Ubuntu 22.04 with MongoDB, Redis, and Nginx"
2. "Install Python ML environment with TensorFlow 2.x, PyTorch, Jupyter, and MLflow on macOS"
3. "Configure a full DevOps toolchain with Docker, Kubernetes, Terraform, Ansible, and Jenkins"
4. "Set up Java Spring Boot development with Maven, Gradle, PostgreSQL, and IntelliJ IDEA on Windows"
5. "Create a microservices development environment with Docker Compose, Kong API Gateway on Ubuntu"

---

## 🚢 Deployment

### Frontend → Vercel
```bash
cd frontend
npx vercel --prod
# Set NEXT_PUBLIC_API_URL to your backend URL
```

### Backend → Render
1. Create new Web Service on render.com
2. Connect your GitHub repo
3. Set build command: `pip install -r requirements.txt`
4. Set start command: `uvicorn main:app --host 0.0.0.0 --port $PORT`
5. Add environment variables in Render dashboard

---

## 🛡 Security

- JWT authentication with bcrypt password hashing
- Input sanitization on all endpoints
- Rate limiting via slowapi
- Dangerous command detection in generated scripts
- CORS configured for specific origins

---

## 📄 License

MIT License — Built for hackathons and demos.
