# 🚀 Quick Start Guide - Windows Edition

## ⚡ Super Quick Setup (5 minutes)

### Step 1: Install Ollama
1. Download from https://ollama.ai
2. Run the installer
3. Restart terminal
4. Run: `ollama pull llama2` (this downloads the model)

### Step 2: Run Setup Script

**Double-click** `setup-admin.bat` in your Diligent folder

This will:
- ✅ Create Python virtual environment
- ✅ Install backend dependencies (FastAPI, Pinecone, etc.)
- ✅ Install frontend dependencies (React, Vite, etc.)

### Step 3: Start Three Services

Open 3 Command Prompts and run each script:

**Terminal 1** (Ollama):
```bash
start-ollama.bat
```

**Terminal 2** (Backend):
```bash
start-backend.bat
```

**Terminal 3** (Frontend):
```bash
start-frontend.bat
```

### Step 4: Open Browser
```
http://localhost:5173
```

Done! 🎉

---

## 📋 Manual Setup (If Scripts Don't Work)

### Terminal 1: Start Ollama
```powershell
ollama serve
```

### Terminal 2: Start Backend
```powershell
cd backend
venv\Scripts\activate.bat
python -m uvicorn app.main:app --reload
```

### Terminal 3: Start Frontend
```powershell
cd frontend
npm run dev
```

Then open http://localhost:5173

---

## 🔧 Initial Setup (One Time)

If you need to run setup manually:

```powershell
# As Administrator
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser -Force

cd C:\Users\shaik\Desktop\Diligent\backend
python -m venv venv
.\venv\Scripts\Activate.ps1
pip install -r requirements.txt

cd ..\frontend
npm install
```

---

## 🆘 Troubleshooting

| Error | Solution |
|-------|----------|
| "ollama is not recognized" | Install Ollama from https://ollama.ai |
| "Port 8000 already in use" | Change port in backend/app/main.py or kill existing process |
| "Port 5173 already in use" | Change port in frontend/vite.config.ts or kill existing process |
| "npm: The term is not recognized" | Restart terminal after installing Node.js, or use setup-admin.bat |
| "venv\Scripts\activate: cannot be loaded" | Run setup-admin.bat which handles execution policies |
| "Cannot find module" | Make sure npm install and pip install completed successfully |
| "Connection refused" | Make sure all 3 services are running (Ollama, Backend, Frontend) |

---

## 📁 What's Running Where

**Backend** (`/backend`)
- FastAPI server handling chat and knowledge management
- LLM integration via Ollama
- **Vector database**: Pinecone (cloud-native, scalable)
- REST API at port 8000

**Frontend** (`/frontend`)
- React + TypeScript chatbot UI
- Real-time message handling
- Knowledge management panel
- Service status indicator

**Key Features**
- ✅ Self-hosted LLM (Ollama + LLaMA)
- ✅ Cloud-native vector database (Pinecone)
- ✅ Semantic knowledge retrieval
- ✅ Persistent storage across sessions
- ✅ Scalable to millions of documents

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| "Ollama not found" | Install from https://ollama.ai and run `ollama serve` |
| "Connection refused" | Make sure both backend and frontend are running |
| "Model not found" | Run `ollama pull llama2` |
| "Slow first response" | Normal - LLM loads on first query |
| "Port already in use" | Change port in vite.config.ts or main.py |

---

## Next Steps

After setup works:

1. **Add Knowledge**
   - Click "📚 Knowledge" button
   - Paste documents, notes, or instructions
   - AI will use these for context-aware responses

2. **Try Different Models**
   - `ollama pull mistral` (faster, smaller)
   - `ollama pull neural-chat` (optimized for chat)
   - Update `backend/.env` LLM_MODEL

3. **Customize UI**
   - Edit `frontend/src/App.tsx`
   - Modify colors in Tailwind classes
   - Add new components in `src/components/`

4. **Deploy** (Optional)
   - Backend: Deploy FastAPI app to cloud
   - Frontend: Build with `npm run build` and deploy
   - Keep Ollama local or self-host

---

## API Examples

### Chat
```bash
curl -X POST http://localhost:8000/api/chat/message \
  -H "Content-Type: application/json" \
  -d '{
    "query": "What is machine learning?",
    "conversation_history": []
  }'
```

### Add Knowledge
```bash
curl -X POST http://localhost:8000/api/knowledge/add \
  -H "Content-Type: application/json" \
  -d '{
    "text": "Machine learning is a subset of AI...",
    "metadata": {"source": "notes"}
  }'
```

---

## Architecture Diagram

```
User Browser (http://localhost:5173)
         ↓
    React + TypeScript UI
         ↓
    Axios HTTP Requests
         ↓
FastAPI Backend (http://localhost:8000)
    ↙        ↓        ↘
LLM      Chat API    Knowledge API
(Ollama)            ↓
            Pinecone Vector DB (Cloud)
```

---

Enjoy your personal AI assistant! 🤖
