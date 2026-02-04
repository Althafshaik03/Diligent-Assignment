# 🔧 Pinecone Integration Guide

Your Jarvis AI Assistant is now powered by **Pinecone** - a cloud-native vector database for scalable knowledge management!

## ✅ What's Already Done

Your Pinecone API key is **already configured** in `.env`:
```
PINECONE_API_KEY=pcsk_5eK74B_RtyUv3SYrx2ht1YYaJ3a44d9nxhKMvtv2T12rRhEK6f9ZkwSBZdT4N3r2XKPD7T
PINECONE_INDEX_NAME=jarvis-knowledge
PINECONE_ENVIRONMENT=us-east-1
PINECONE_NAMESPACE=default
```

## ⚠️ Important: Create Your Index in Pinecone

Before running the backend, you need to create the index in Pinecone:

### Option 1: Via Pinecone Console (Recommended)

1. Go to https://app.pinecone.io
2. Sign in with your account
3. Click **Create Index**
4. Configure:
   - **Name**: `jarvis-knowledge`
   - **Dimension**: `384` (for Ollama embeddings)
   - **Metric**: `cosine` (for similarity search)
   - **Environment**: `us-east-1` (or your preferred region)
5. Click Create
6. Wait for status to show "Ready"

### Option 2: Via API (Command Line)

```bash
# Make sure you have curl installed
curl -X POST https://controller.us-east-1.pinecone.io/databases \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{
    "name": "jarvis-knowledge",
    "dimension": 384,
    "metric": "cosine"
  }'
```

## 🚀 Now Start Your Jarvis

```powershell
# Terminal 1: Start Ollama
ollama serve

# Terminal 2: Start Backend
cd backend
venv\Scripts\activate
python -m uvicorn app.main:app --reload

# Terminal 3: Start Frontend
cd frontend
npm run dev
```

## 💡 What Happens When You Use Jarvis

1. **Add Knowledge** 📚
   - Click "Knowledge" button in UI
   - Paste documents, notes, or instructions
   - Your text is automatically:
     - Converted to 384-dimensional embeddings (via Ollama)
     - Stored in Pinecone with metadata
     - Immediately searchable

2. **Chat** 💬
   - Type a query
   - System searches Pinecone for similar knowledge
   - Retrieved context is sent to LLaMA
   - AI responds with context-aware answers

3. **Persistence** 💾
   - All knowledge stays in Pinecone
   - Survives app restarts
   - Accessible from anywhere

## 🔍 Monitor Your Knowledge Base

### Check Index Status
```bash
# Via Pinecone Console Dashboard
# https://app.pinecone.io
```

### Via API
```bash
curl https://jarvis-knowledge-us-east-1.pinecone.io/describe_index_stats \
  -H "Api-Key: pcsk_5eK74B_RtyUv3SYrx2ht1YYaJ3a44d9nxhKMvtv2T12rRhEK6f9ZkwSBZdT4N3r2XKPD7T"
```

## 📊 Pinecone Tiers

| Tier | Storage | Cost | Good For |
|------|---------|------|----------|
| Free | 1GB | Free | Development, testing |
| Standard | Unlimited | $0.03/hour | Production, personal use |
| Enterprise | Custom | Custom | Large-scale deployments |

You're currently on the **Starter Pack** plan.

## 🎯 Use Cases

### Knowledge Management
- Store company documentation
- Upload training materials
- Store research papers
- Build custom knowledge bases

### RAG (Retrieval Augmented Generation)
- Your knowledge + LLaMA = Accurate answers
- No hallucinations (grounded in your data)
- Always up-to-date information

### Team Collaboration
- Shared knowledge across team members
- Consistent AI responses
- Document organization

## ⚙️ Configuration Options

Edit `backend/.env` to customize:

```ini
# Model Settings
LLM_MODEL=llama2          # Can also use: mistral, neural-chat, etc.
OLLAMA_BASE_URL=http://localhost:11434

# Pinecone Settings
PINECONE_API_KEY=your_key_here
PINECONE_ENVIRONMENT=us-east-1
PINECONE_INDEX_NAME=jarvis-knowledge
PINECONE_NAMESPACE=default

# Multiple Namespaces (Optional)
# Use different namespaces for different knowledge bases
# PINECONE_NAMESPACE=team-docs
# PINECONE_NAMESPACE=research-papers
```

## 🚨 Troubleshooting

| Issue | Solution |
|-------|----------|
| "Index does not exist" | Create index in Pinecone console (see above) |
| "API key invalid" | Verify key in `backend/.env` |
| "Connection timeout" | Check internet connection, Pinecone status |
| "Dimension mismatch" | Ensure index dimension is 384 |
| "Rate limited" | Wait or upgrade Pinecone plan |

## 💰 Pricing Estimate

For personal use:
- **Storage**: ~$0.10/million vectors/month
- **Compute**: ~$0.03/hour (when active)
- **Free tier**: 1GB included

Example: 10,000 documents = ~$0.001/month

## 🔐 Security Notes

- Keep your API key in `.env` (never commit to git)
- Use different namespaces for different users/projects
- Pinecone encrypts data in transit and at rest
- Enable VPC if deploying to production

## 📚 Next Steps

1. ✅ API key configured
2. 📝 Create index in Pinecone console
3. 🚀 Start Jarvis (see Quick Start)
4. 📚 Add knowledge to your index
5. 💬 Start chatting!

---

Questions? Check Pinecone docs: https://docs.pinecone.io
