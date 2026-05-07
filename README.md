# 🚀 TaskFlow — Project Management Web App

A full-stack project management application with role-based access control (Admin/Member), built with Node.js, Express, and Vanilla JS.

**Live URL:** _[Add your Railway URL here after deployment]_

---

## ✨ Features

### 🔐 Authentication
- User Signup & Login with JWT tokens
- Secure password hashing with bcrypt
- Protected API routes via Bearer token auth

### 📁 Project Management
- Create, edit, and delete projects
- Role-based access: **Owner**, **Admin**, **Member**
- Invite team members by email
- Manage member roles (promote/demote Admin ↔ Member)
- Remove members from projects

### ✅ Task Management
- Create, edit, delete tasks per project
- Task fields: Title, Description, Status, Priority, Assignee, Due Date
- Status tracking: `To Do` → `In Progress` → `Done`
- Priority levels: `Low`, `Medium`, `High`
- Assign tasks to project members

### 📊 Dashboard
- Overview stats: Total projects, My Tasks, Completed, Overdue
- Recent tasks assigned to the user
- Project progress bars
- Overdue tasks alert table (across all projects)

### 🎯 Kanban Board
- Visual kanban view per project
- Tasks grouped by status columns
- Quick click to edit tasks

### 👥 Team Management
- View all project members
- Add members by email
- Change roles (owner only)
- Leave or remove members

---

## 🛠 Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | Node.js + Express 5 |
| Database | JSON files (no native deps — works everywhere) |
| Auth | JWT (jsonwebtoken) + bcrypt |
| Validation | express-validator |
| Frontend | Vanilla HTML/CSS/JS (single file) |
| Fonts | Syne + DM Sans (Google Fonts) |
| Deployment | Railway |

---

## 🚀 Local Setup

```bash
# 1. Clone the repo
git clone https://github.com/YOUR_USERNAME/taskflow.git
cd taskflow

# 2. Install backend dependencies
cd backend
npm install

# 3. Configure environment
cp ../.env.example .env
# Edit .env and set a strong JWT_SECRET

# 4. Start the server
npm start
# Server runs on http://localhost:3000
```

Open `http://localhost:3000` in your browser — signup and start using TaskFlow!

---

## 🌐 Deploy on Railway

### Option 1: GitHub → Railway (Recommended)

1. Push this repo to GitHub
2. Go to [railway.app](https://railway.app) and click **New Project**
3. Select **Deploy from GitHub repo**
4. Choose your `taskflow` repo
5. Railway auto-detects the `package.json` and deploys

**Set environment variables in Railway:**
```
JWT_SECRET=your_super_secret_key_here
PORT=3000
```

6. Click **Deploy** — your app will be live in ~2 minutes!

### Option 2: Railway CLI

```bash
npm install -g @railway/cli
railway login
railway init
railway up
```

---

## 📡 API Reference

### Auth
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/signup` | Register new user |
| POST | `/api/auth/login` | Login & get JWT |
| GET | `/api/auth/me` | Get current user |

### Projects
| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| GET | `/api/projects` | List user's projects | Any member |
| POST | `/api/projects` | Create project | Authenticated |
| GET | `/api/projects/:id` | Get project details | Member+ |
| PUT | `/api/projects/:id` | Update project | Admin+ |
| DELETE | `/api/projects/:id` | Delete project | Owner only |

### Members
| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| GET | `/api/projects/:id/members` | List members | Member+ |
| POST | `/api/projects/:id/members` | Add member by email | Admin+ |
| PUT | `/api/projects/:id/members/:userId` | Change role | Owner only |
| DELETE | `/api/projects/:id/members/:userId` | Remove member | Admin+ / Self |

### Tasks
| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| GET | `/api/projects/:id/tasks` | List project tasks | Member+ |
| POST | `/api/projects/:id/tasks` | Create task | Member+ |
| PUT | `/api/projects/:id/tasks/:taskId` | Update task | Member+ |
| DELETE | `/api/projects/:id/tasks/:taskId` | Delete task | Admin+ / Creator |

### Dashboard
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/dashboard` | Stats, recent/overdue tasks, projects |

---

## 🔒 Role-Based Access Control

| Action | Member | Admin | Owner |
|--------|--------|-------|-------|
| View project | ✅ | ✅ | ✅ |
| Create tasks | ✅ | ✅ | ✅ |
| Edit/delete own tasks | ✅ | ✅ | ✅ |
| Edit/delete any tasks | ❌ | ✅ | ✅ |
| Edit project details | ❌ | ✅ | ✅ |
| Add/remove members | ❌ | ✅ | ✅ |
| Change member roles | ❌ | ❌ | ✅ |
| Delete project | ❌ | ❌ | ✅ |

---

## 📁 Project Structure

```
taskflow/
├── backend/
│   ├── routes/
│   │   ├── auth.js        # Auth routes (signup/login)
│   │   ├── projects.js    # Projects + Members routes
│   │   ├── tasks.js       # Tasks CRUD routes
│   │   └── dashboard.js   # Dashboard stats route
│   ├── db.js              # JSON file database layer
│   ├── auth.js            # JWT middleware
│   ├── server.js          # Express app entry point
│   └── package.json
├── frontend/
│   └── index.html         # Complete SPA frontend
├── railway.toml           # Railway deployment config
├── package.json           # Root package for Railway
├── .env.example
└── README.md
```

---

## 📸 Screenshots



---

## 📄 License

MIT
