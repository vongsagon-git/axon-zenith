# AXON Configuration

> สร้างโดย `/axon:setup` - แก้ไขได้ภายหลังด้วย `/axon:mcp`

## 🧠 Knowledge Base

**Type:** {{KNOWLEDGE_TYPE}}
**Status:** {{STATUS}}

### Type Options:
- `text` - ใช้ AXON_KNOWLEDGE.md (Default)
- `digitalocean` - DO Gradient + OpenSearch
- `mongodb` - MongoDB Atlas Vector
- `qdrant` - Local Qdrant
- `chroma` - Local ChromaDB

---

## 📥 Transform Settings

**Auto-embed:** {{AUTO_EMBED}}
**Embedding Model:** {{EMBEDDING_MODEL}}
**Chunk Size:** {{CHUNK_SIZE}}

### Embedding Models Available:

| Provider | Model | ราคา |
|----------|-------|------|
| DigitalOcean | gte-large-en-v1.5 | $0.09/1M tokens |
| DigitalOcean | all-mini-lm-l6-v2 | $0.01/1M tokens |
| DigitalOcean | Qwen3 Embedding 0.6B | $0.04/1M tokens |
| MongoDB | Voyage AI | ตาม Voyage pricing |
| Local | HuggingFace models | Free |

---

## 🔑 API Keys Required

> ตั้งค่าใน environment variables หรือ `.env`

### IF Type = digitalocean:
- [ ] `DIGITALOCEAN_TOKEN` - DO API Token

### IF Type = mongodb:
- [ ] `MONGODB_URI` - Connection string
- [ ] `VOYAGE_API_KEY` - Voyage AI key

### IF Type = qdrant/chroma:
- [ ] (ไม่ต้องใช้ API key - รันบนเครื่อง)

---

## 🔌 MCP Servers

**Installed:**
{{MCP_LIST}}

**Recommended:**
{{MCP_RECOMMENDED}}

---

## 📝 Notes

- เปลี่ยน Knowledge Type: แก้ไฟล์นี้ แล้วรัน `/axon:mcp recommend`
- Transform data: ใช้ MCP tools หรือ API ตาม type ที่เลือก
- ดูรายละเอียด: `/axon:mcp list`
