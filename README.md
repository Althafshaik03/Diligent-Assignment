# Jarvis - Personal AI Assistant

A self-hosted AI assistant powered by LLaMA, featuring a React chatbot UI, FastAPI backend, and Chroma vector database for knowledge management.

## Architecture

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
   │Ollama  │ Pinecone  │  (Cloud Vector DB)
   │(LLM)   │ (Premium) │
   └─────┘   └──────────┘
```

## Prerequisites

- Python 3.9+
- Node.js 16+
- Ollama (download from https://ollama.ai)

## Installation

### 1. Install Ollama & Download Model

```bash
# Download and install Ollama from https://ollama.ai

# Jarvis — Personal AI Assistant (Clean)

Lightweight self-hosted assistant using a local LLM (Ollama), a FastAPI backend and Pinecone for vector search. This README is a concise entry point; full documentation and design artifacts are in the `docs/` folder.

Quick links
- Documentation: `docs/`
- Setup scripts: `scripts/` (hidden by default; not checked into source)
- Backend: `backend/`
- Frontend: `frontend/`

Quick start (Windows)
1. Install Ollama: https://ollama.ai
2. Right-click `scripts\setup-admin.bat` → "Run as Administrator"
3. Start services (or use `scripts/start-*.bat`)
4. Open `http://localhost:5173`

Quick start (Linux/macOS)
```bash
bash scripts/setup.sh
```

Notes
- `scripts/` is hidden and added to `.gitignore` to keep the repository clean. Use the scripts for setup and local development.
- Detailed guides, troubleshooting, and the product requirements document (PRD) are in `docs/PRD.md` and other files in `docs/`.

If you want the full technical documentation, open `docs/README.md`.
│   ├── package.json
│   └── vite.config.ts
└── README.md
```

## Next Steps

- Add authentication
- Deploy to cloud
- Add more models
- Implement streaming responses
- Add conversation persistence
- Build admin dashboard

## License

MIT
