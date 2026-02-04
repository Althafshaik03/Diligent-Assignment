# 🚀 Jarvis - Windows Quick Start

## Files in Your Diligent Folder

| File | Purpose |
|------|---------|
| `setup-admin.bat` | **Run this first!** Sets up everything |
| `start-ollama.bat` | Start Ollama LLM server |
| `start-backend.bat` | Start FastAPI backend |
| `start-frontend.bat` | Start React frontend |

## 🎯 Getting Started (Fastest Way)

### 1. Install Ollama
- Download: https://ollama.ai
- Run installer
- Restart your terminal
- Run: `ollama pull llama2`

### 2. Run Setup Script
- **Right-click** `setup-admin.bat` 
- Click **"Run as Administrator"**
- Wait for it to complete
- Close the window when done

### 3. Start Services
- Double-click `start-ollama.bat`
- Double-click `start-backend.bat` (in a new window)
- Double-click `start-frontend.bat` (in a new window)

### 4. Open Browser
```
http://localhost:5173
```

That's it! 🎉

---

## 🛠️ If You Have Issues

### PowerShell Execution Error?
Run in PowerShell as Administrator:
```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser -Force
```

### Port Already in Use?
- Change backend port in `backend/app/main.py` (line with `uvicorn.run`)
- Change frontend port in `frontend/vite.config.ts` (line with `port:`)

### Dependencies Won't Install?
```powershell
cd backend
python -m venv venv
venv\Scripts\activate.bat
pip install -r requirements.txt
```

---

## 📊 Services Running

| Service | Port | Purpose |
|---------|------|---------|
| Ollama | 11434 | LLM inference |
| Backend (FastAPI) | 8000 | Chat & Knowledge APIs |
| Frontend (Vite) | 5173 | React UI |

---

## 🔌 Your Pinecone is Already Connected!

Your Pinecone API key is configured in `backend/.env`

**Important:** Before using Jarvis, create a Pinecone index:
1. Go to https://app.pinecone.io
2. Create index named: `jarvis-knowledge`
3. Set dimension: `384`
4. Set metric: `cosine`

See `PINECONE_SETUP.md` for details.

---

## 📝 Need Help?

Check these files:
- `QUICKSTART.md` - Detailed setup guide
- `PINECONE_SETUP.md` - Vector database setup
- `README.md` - Full documentation

---

**Questions?** Your Jarvis is ready to help! 🤖
