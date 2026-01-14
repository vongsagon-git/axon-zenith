---
description: "Manage MCP Servers - เพิ่ม/ลบ/ดูรายการ MCP ที่เหมาะสม"
---

# AXON MCP PROTOCOL

## Mission
จัดการ MCP (Model Context Protocol) Servers - เพิ่มความสามารถให้ Claude Code

## Arguments
- `list` - แสดงรายการ MCP ที่ติดตั้งอยู่
- `recommend` - แนะนำ MCP ที่เหมาะกับโปรเจค
- `add <name>` - เพิ่ม MCP server ใหม่
- `remove <name>` - ลบ MCP server

**Input:** $ARGUMENTS

---

## MCP CATALOG (Verified Packages)

### 📡 Web & Browser

| MCP Server | Install Command | ความสามารถ |
|------------|-----------------|------------|
| **puppeteer** | `npx -y @modelcontextprotocol/server-puppeteer` | ควบคุม Browser, screenshot, click, fill form |
| **fetch** | `uvx mcp-server-fetch` | ดึงข้อมูล URL (Python - ต้องมี uv) |
| **brave-search** | `npx -y @modelcontextprotocol/server-brave-search` | ค้นหาเว็บ (ต้องมี API key) |

### 💾 Database (SQL)

| MCP Server | Install Command | ความสามารถ |
|------------|-----------------|------------|
| **sqlite** | `npx -y @modelcontextprotocol/server-sqlite` | SQLite database |
| **postgres** | `npx -y @modelcontextprotocol/server-postgres` | PostgreSQL |

### 🍃 Database (NoSQL)

| MCP Server | Install Command | ความสามารถ |
|------------|-----------------|------------|
| **mongodb** | `npx -y mongodb-mcp-server` | MongoDB + Atlas Vector Search (Official) |

> 🔗 **MongoDB Atlas Vector Search:**
> - รองรับ vector search + auto-embedding
> - ต้องมี Voyage AI API key สำหรับ embedding
> - ดู [MongoDB MCP Docs](https://www.mongodb.com/docs/mcp-server/)

### 🧠 Vector Database (AI/RAG)

| MCP Server | Install Command | ความสามารถ |
|------------|-----------------|------------|
| **qdrant** | `uvx mcp-server-qdrant` | Qdrant vector search (Official) |
| **chroma** | `npx -y @nicholasoxford/chroma-mcp` | ChromaDB vector storage |
| **pinecone** | `npx -y pinecone-mcp` | Pinecone vector database |

> 💡 **Vector DB ใช้สำหรับ:** RAG (Retrieval Augmented Generation), Semantic Search, AI Memory

### 🤖 AI & Embedding

| MCP Server | Install Command | ความสามารถ |
|------------|-----------------|------------|
| **huggingface** | Remote MCP: `https://huggingface.co/mcp` | ค้นหา models, datasets, spaces (รวม gte-large-en-v1.5) |
| **hfspace** | `npx -y mcp-hfspace` | ใช้ HuggingFace Spaces + Gradio endpoints |

> 💡 **Embedding Models:** ใช้ผ่าน HuggingFace MCP หรือ DigitalOcean Gradient AI Platform

### ☁️ Cloud Providers

| MCP Server | Install Command | ความสามารถ |
|------------|-----------------|------------|
| **digitalocean** | Remote MCP (Official) | จัดการ Droplets, DOKS, Databases, Spaces, Gradient |

> 🔗 **DigitalOcean MCP:** ใช้ natural language สั่ง cloud resources
> - รองรับ: Droplets, App Platform, DOKS, Databases, Spaces
> - Setup: ดู [DO MCP Docs](https://www.digitalocean.com/blog/mcp-server-public-release)

---

## 🧠 DigitalOcean Gradient Knowledge Base (RAG Solution)

### Architecture
```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Data Sources  │───▶│  Embedding Model │───▶│    OpenSearch   │
│ (Files, URLs)   │    │  (gte-large etc) │    │  (Vector Store) │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                                                       │
                       ┌──────────────────┐            │
                       │   Gradient Agent │◀───────────┘
                       │   (RAG Query)    │
                       └──────────────────┘
```

### Embedding Models & Pricing

| Model | ราคา | คุณสมบัติ | แนะนำสำหรับ |
|-------|------|----------|------------|
| **gte-large-en-v1.5** | $0.09/1M tokens | High quality, 1024 dims | Production English RAG |
| **all-mini-lm-l6-v2** | $0.01/1M tokens | Fast, lightweight | Development/Testing |
| **multi-qa-mpnet-base-dot-v1** | $0.01/1M tokens | Q&A optimized | FAQ/Support bots |
| **Qwen3 Embedding 0.6B** | $0.04/1M tokens | Multilingual | Thai/Multi-language |

### Cost Estimation (gte-large-en-v1.5)

| Dataset Size | Embedded Size | Tokens | Indexing Cost |
|--------------|---------------|--------|---------------|
| 10 MB | ~80-100 MB | 3M | $0.225 |
| 100 MB | ~800 MB-1GB | 25M | $2.25 |
| 500 MB | ~4-5 GB | 125M | $11.25 |
| 1 GB | ~8-10 GB | 250M | $22.50 |

### API Access

```bash
# Create Knowledge Base
POST https://api.digitalocean.com/v2/gen-ai/knowledge_bases

# List Models
GET https://api.digitalocean.com/v2/gen-ai/models?usecases=embedding
```

> ⚠️ **หมายเหตุสำคัญ:**
> - เปลี่ยน Embedding Model หลังสร้าง Knowledge Base ไม่ได้!
> - OpenSearch database จะถูกสร้างอัตโนมัติ
> - ลบ OpenSearch = ลบ Knowledge Base ทั้งหมด

### 📂 Files & Git

| MCP Server | Install Command | ความสามารถ |
|------------|-----------------|------------|
| **filesystem** | `npx -y @modelcontextprotocol/server-filesystem /path` | Filesystem access |
| **github** | `npx -y @modelcontextprotocol/server-github` | GitHub API (ต้องมี token) |
| **memory** | `npx -y @modelcontextprotocol/server-memory` | Knowledge graph memory |

---

## Execution Logic

### IF `list`:
```
1. รัน: claude mcp list
2. แสดงผลเป็นตาราง
3. บอกสถานะแต่ละ MCP
```

### IF `recommend`:
```
1. วิเคราะห์โปรเจค:
   - มี package.json? → แนะนำ Node tools
   - มี requirements.txt? → แนะนำ Python tools
   - มี Dockerfile? → แนะนำ Docker MCP
   - ทำ web scraping? → แนะนำ puppeteer
   - มี database? → แนะนำ sqlite/postgres
   - ทำ AI/RAG/LangChain? → แนะนำ vector db (qdrant/chroma)
   - มี mongodb connection string? → แนะนำ mongodb

2. แสดงคำแนะนำเป็นลำดับความสำคัญ
```

### IF `add <name>`:
```
1. ค้นหา package จาก CATALOG
2. รัน: claude mcp add <name> -- <install-command>
3. ตรวจสอบว่า MCP ทำงานได้
4. แนะนำให้ user reload Claude Code
```

> ⚠️ **สำคัญ:** หลังติดตั้ง MCP ใหม่ ต้อง **Reload Claude Code** เพื่อให้ MCP ทำงาน!
> - VSCode: กด `Ctrl+Shift+P` → "Developer: Reload Window"
> - Terminal: ปิดแล้วเปิด Claude Code ใหม่

**ตัวอย่างคำสั่ง:**
```bash
# Puppeteer (แนะนำ)
claude mcp add puppeteer -- npx -y @modelcontextprotocol/server-puppeteer

# SQLite
claude mcp add sqlite -- npx -y @modelcontextprotocol/server-sqlite --db-path ./data.db

# Filesystem
claude mcp add filesystem -- npx -y @modelcontextprotocol/server-filesystem /allowed/path

# GitHub (ต้อง set GITHUB_TOKEN)
claude mcp add github -- npx -y @modelcontextprotocol/server-github

# MongoDB
claude mcp add mongodb -- npx -y mcp-mongo-server

# Qdrant (Vector DB - ต้องมี uv)
claude mcp add qdrant -- uvx mcp-server-qdrant

# ChromaDB (Vector DB)
claude mcp add chroma -- npx -y @nicholasoxford/chroma-mcp

# Pinecone (Vector DB - ต้องมี API key)
claude mcp add pinecone -- npx -y pinecone-mcp
```

### IF `remove <name>`:
```
1. รัน: claude mcp remove <name>
2. ยืนยันการลบ
```

---

## Output Format

### สำหรับ `list`:
```markdown
# 📡 MCP Servers ที่ติดตั้ง

| ชื่อ | สถานะ | Tools ที่ได้ |
|-----|-------|------------|
| puppeteer | ✅ Connected | navigate, screenshot, click |
| fetch | ✅ Connected | fetch_html, fetch_markdown |

**Total:** X servers active
```

### สำหรับ `recommend`:
```markdown
# 💡 MCP แนะนำสำหรับโปรเจคนี้

## 🥇 ความสำคัญสูง
- **puppeteer** - ควบคุม browser, screenshot

## 🥈 ทางเลือกเสริม
- **sqlite** - local database

## ⚡ คำสั่งติดตั้ง
\`\`\`bash
claude mcp add puppeteer -- npx -y @modelcontextprotocol/server-puppeteer
\`\`\`
```

### สำหรับ `add`:
```markdown
# ✅ เพิ่ม MCP สำเร็จ

**Server:** puppeteer
**Tools ที่ได้:**
- puppeteer_navigate
- puppeteer_screenshot
- puppeteer_click
- puppeteer_fill

---

⚠️ **ขั้นตอนสุดท้าย:** กรุณา **Reload Claude Code** เพื่อให้ MCP ใหม่ทำงาน
- VSCode: `Ctrl+Shift+P` → "Developer: Reload Window"
- Terminal: ปิดแล้วเปิด Claude Code ใหม่
```

---

## 📚 Sources
- [MCP Servers GitHub](https://github.com/modelcontextprotocol/servers)
- [npm: @modelcontextprotocol/server-puppeteer](https://www.npmjs.com/package/@modelcontextprotocol/server-puppeteer)
- [Qdrant MCP Server](https://github.com/qdrant/mcp-server-qdrant)
- [PulseMCP - MCP Directory](https://pulsemcp.com)
- [HuggingFace MCP Server](https://huggingface.co/docs/hub/hf-mcp-server)
- [DigitalOcean MCP Server](https://www.digitalocean.com/blog/mcp-server-public-release)
- [DigitalOcean Gradient AI Platform](https://docs.digitalocean.com/products/gradient-ai-platform/)
- [DigitalOcean Knowledge Base](https://docs.digitalocean.com/products/gradient-ai-platform/how-to/create-manage-agent-knowledge-bases/)
- [MongoDB MCP Server](https://github.com/mongodb-js/mongodb-mcp-server)
- [GTE-Large Model](https://huggingface.co/thenlper/gte-large)
