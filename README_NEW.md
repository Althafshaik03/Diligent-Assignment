# 🤖 Jarvis - Personal AI Assistant

A self-hosted AI assistant powered by LLaMA, featuring a React chatbot UI, FastAPI backend, and Pinecone vector database for knowledge management.

## 🚀 Quick Start

### Windows Users
1. Install Ollama: https://ollama.ai
2. Right-click `scripts/setup-admin.bat` → **"Run as Administrator"**
3. Follow the on-screen instructions

See [docs/WINDOWS_SETUP.md](docs/WINDOWS_SETUP.md) for detailed guide.

### Linux/Mac Users
```bash
bash setup.sh
```

See [docs/QUICKSTART.md](docs/QUICKSTART.md) for detailed guide.

---

## 📚 Documentation

All documentation is in the **`docs/`** folder:

| File | Purpose |
|------|---------|
| [WINDOWS_SETUP.md](docs/WINDOWS_SETUP.md) | 🪟 Windows installation & quick start |
| [QUICKSTART.md](docs/QUICKSTART.md) | 🚀 Quick start guide (all platforms) |
| [PINECONE_SETUP.md](docs/PINECONE_SETUP.md) | 📚 Vector database setup & configuration |
| [README.md](docs/README.md) | 📖 Full technical documentation |

---

## 🏗️ Architecture

```
┌─────────────────────┐
│  React + TypeScript │  (Frontend - Port 5173)
└──────────┬──────────┘
           │ HTTP/WebSocket
           ↓
┌─────────────────────┐
│   FastAPI Backend   │  (Port 8000)
│  ┌───────────────┐  │
│  │  Chat Routes  │  │
│  │ Knowledge API │  │
│  └───────────────┘  │
└──────────┬──────────┘
           │
      ┌────┴────┐
      ↓         ↓
   ┌─────┐   ┌──────────┐
   │ Ollama  │ Pinecone │  (Cloud Vector DB)
   │ (LLM)   │ (Premium)│
   └─────┘   └──────────┘
```

---

## ✨ Features

✅ **Real-time chat** with LLaMA  
✅ **Knowledge base** management with Pinecone  
✅ **Semantic search** for context-aware responses  
✅ **Conversation history** tracking  
✅ **Persistent storage** (cloud-native)  
✅ **Beautiful React UI** with Tailwind CSS  
✅ **Health monitoring** & status indicators  
✅ **Scalable** to millions of documents  

---

## 📂 Project Structure

```
Diligent/
├── 📖 docs/                 All documentation
│   ├── README.md
│   ├── WINDOWS_SETUP.md
│   ├── QUICKSTART.md
│   └── PINECONE_SETUP.md
│
├── 🔧 scripts/              Setup & run scripts
│   ├── setup-admin.bat      ← Run this first (Windows)
│   ├── start-ollama.bat
│   ├── start-backend.bat
│   └── start-frontend.bat
│
├── 🐍 backend/              FastAPI + Python
│   ├── app/
│   │   ├── routes/          API endpoints
│   │   ├── services/        LLM & Vector DB
│   │   ├── models/          Data models
│   │   └── main.py          App entry point
│   ├── requirements.txt     Python dependencies
│   └── .env                 Configuration
│
└── ⚛️ frontend/              React + TypeScript
    ├── src/
    │   ├── components/      UI components
    │   ├── api/             API client
    │   ├── App.tsx          Main component
    │   └── main.tsx         Entry point
    ├── package.json         Node dependencies
    └── vite.config.ts       Build config
```

---

## 🛠️ Requirements

- **Python** 3.9+
- **Node.js** 16+
- **Ollama** (from https://ollama.ai)
- **Pinecone API key** (included in `.env`)

---

## 🎯 Getting Started

### Step 1: Install Prerequisites
- Download & install [Ollama](https://ollama.ai)
- Install [Python 3.9+](https://www.python.org)
- Install [Node.js 16+](https://nodejs.org)

### Step 2: Run Setup
**Windows:**
```bash
Right-click scripts/setup-admin.bat → Run as Administrator
```

**Linux/Mac:**
```bash
bash setup.sh
```

### Step 3: Start Services
After setup completes, open 3 separate terminals:

**Terminal 1 - Ollama:**
```bash
scripts\start-ollama.bat          # Windows
./scripts/start-ollama.sh         # Linux/Mac
```

**Terminal 2 - Backend:**
```bash
scripts\start-backend.bat         # Windows
./scripts/start-backend.sh        # Linux/Mac
```

**Terminal 3 - Frontend:**
```bash
scripts\start-frontend.bat        # Windows
./scripts/start-frontend.sh       # Linux/Mac
```

### Step 4: Open in Browser
```
http://localhost:5173
```

---

## 🎮 Using Jarvis

1. **Chat** - Type messages and press Send
2. **Add Knowledge** - Click "📚 Knowledge" to add documents
3. **Get Answers** - AI uses your knowledge for context-aware responses

---

## ⚙️ Configuration

Key files to customize:
- `backend/.env` - LLM, Pinecone, CORS settings
- `frontend/vite.config.ts` - Frontend build & dev settings
- `backend/app/main.py` - FastAPI configuration

See [docs/README.md](docs/README.md) for full configuration options.

---

## 📖 Learn More

- [Windows Setup Guide](docs/WINDOWS_SETUP.md) - Detailed Windows instructions
- [Quick Start Guide](docs/QUICKSTART.md) - All platforms setup
- [Pinecone Guide](docs/PINECONE_SETUP.md) - Vector database details
- [Technical Docs](docs/README.md) - Full API & architecture reference

---

## 🐛 Troubleshooting

| Issue | Solution |
|-------|----------|
| "ollama not found" | Install from https://ollama.ai |
| "Port in use" | Change port in config files or kill process |
| "Dependencies fail" | Run setup script with admin/sudo privileges |
| "Connection refused" | Ensure all 3 services are running |

See respective docs for more troubleshooting help.

---

## 📄 License

MIT

---

## 🤝 Support

Questions? Check the documentation in the `docs/` folder or create an issue.

---

**Ready to build your AI assistant? Start with [docs/WINDOWS_SETUP.md](docs/WINDOWS_SETUP.md) (Windows) or [docs/QUICKSTART.md](docs/QUICKSTART.md) (Linux/Mac)** 🚀
