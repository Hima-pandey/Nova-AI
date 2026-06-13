# ◈ NOVA AI — Full-Stack Setup Guide

A Claude-powered AI assistant with an Express backend and React frontend.

---

## 🗂️ Project Structure

```
nova-ai/
├── backend/          ← Express API server (port 3001)
│   ├── server.js
│   ├── .env          ← YOU CREATE THIS (see step 2)
│   └── package.json
├── frontend/         ← React app (port 3000)
│   ├── src/
│   │   ├── App.jsx
│   │   └── index.js
│   ├── public/
│   │   └── index.html
│   └── package.json
└── package.json      ← Root scripts
```

---

## 🚀 Quick Start

### Step 1 — Install dependencies

Open a terminal in the `nova-ai` folder and run:

```bash
# Install backend deps
cd backend && npm install

# Install frontend deps
cd ../frontend && npm install
```

### Step 2 — Add your Anthropic API key

In the `backend/` folder, create a file named **`.env`**:

```
ANTHROPIC_API_KEY=sk-ant-your-key-here
PORT=3001
```

Get your key at: https://console.anthropic.com

### Step 3 — Start the backend (Terminal 1)

```bash
cd backend
npm run dev
```

You should see:
```
◈  NOVA AI Backend running on http://localhost:3001
```

### Step 4 — Start the frontend (Terminal 2)

```bash
cd frontend
npm start
```

Browser opens at **http://localhost:3000** 🎉

---

## 💡 VS Code Tips

- Use the **Split Terminal** (Ctrl+Shift+5) to run both servers side-by-side.
- Install the **ESLint** and **Prettier** extensions for best experience.
- The frontend proxies all `/api/*` calls to the backend automatically.

---

## 🔧 How It Works

| Layer    | Tech            | Port  | Role                          |
|----------|-----------------|-------|-------------------------------|
| Frontend | React (CRA)     | 3000  | UI, chat, markdown rendering  |
| Backend  | Express + Node  | 3001  | Anthropic API proxy, sessions |
| AI       | Claude Sonnet   | —     | Language model responses      |

The backend keeps your API key server-side and stores chat sessions in memory.
Swap the in-memory store in `server.js` for SQLite/MongoDB to persist across restarts.

---

## ✨ Features

- 5 AI personality modes (NOVA, DEVX, SHIELD, SAGE, MUSE)
- Streaming-style typewriter animation
- Markdown + code block rendering with copy button
- Voice input (Web Speech API) and voice output (TTS)
- Session history (stored in Express backend)
- Backend health indicator in the sidebar
