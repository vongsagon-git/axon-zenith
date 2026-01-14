# 📖 คู่มือการใช้งาน AXON Zenith Plugin

> **Version:** 1.0.0
> **Philosophy:** "ช้าได้ แต่ห้ามห่วย" (Lateness is acceptable, Mediocrity is not)

---

## 📥 การติดตั้ง

### วิธีที่ 1: Clone จาก GitHub (แนะนำ - ใช้งานส่วนตัว)

**Windows (PowerShell):**
```powershell
# ล้างของเดิม (ถ้ามี)
Remove-Item -Recurse -Force "$env:USERPROFILE\.claude\commands\axon" -ErrorAction SilentlyContinue

# ติดตั้งใหม่
git clone https://github.com/vongsagon-git/axon-zenith.git "$env:USERPROFILE\.claude\temp-axon"
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\commands\axon"
Copy-Item "$env:USERPROFILE\.claude\temp-axon\commands\*.md" "$env:USERPROFILE\.claude\commands\axon\"
Remove-Item -Recurse -Force "$env:USERPROFILE\.claude\temp-axon"
```

**macOS / Linux:**
```bash
# ล้างของเดิม (ถ้ามี)
rm -rf ~/.claude/commands/axon

# ติดตั้งใหม่
git clone https://github.com/vongsagon-git/axon-zenith.git /tmp/axon-zenith
mkdir -p ~/.claude/commands/axon
cp /tmp/axon-zenith/commands/*.md ~/.claude/commands/axon/
rm -rf /tmp/axon-zenith
```

> 💡 **หมายเหตุ:** วิธีนี้จะติดตั้ง commands แบบ global ใช้ได้ทุกโปรเจค

### วิธีที่ 2: ติดตั้งผ่าน Official Marketplace (เร็วๆ นี้)
```bash
/plugin install vongsagon-git/axon-zenith
```
> ⚠️ ต้องรอ Anthropic อนุมัติก่อน

### ตรวจสอบการติดตั้ง
หลังติดตั้งแล้ว ลองพิมพ์ `/axon` ใน Claude Code จะเห็น:
```
/axon:setup
/axon:concept
/axon:ignite
/axon:mcp
```

---

## 🚀 เริ่มต้นใช้งาน

### ขั้นตอนที่ 1: Setup ระบบ
```bash
/axon:setup
```

ระบบจะถามให้เลือก Knowledge Base:

| ตัวเลือก | รายละเอียด | เหมาะสำหรับ |
|---------|-----------|------------|
| **Text Files** | ใช้ Markdown เก็บความรู้ | โปรเจคเล็ก-กลาง |
| **DigitalOcean Gradient** | OpenSearch + Embedding | Production AI/RAG |
| **MongoDB Atlas** | Vector Search + Voyage AI | เพิ่ม vector ให้ MongoDB เดิม |
| **Local Vector** | Qdrant/Chroma บนเครื่อง | Development, Privacy |
| **Skip** | ตั้งค่าภายหลัง | ยังไม่แน่ใจ |

### ขั้นตอนที่ 2: วางแผนงาน
```bash
/axon:concept สร้างระบบ login ด้วย OAuth
```

ระบบจะ:
1. วิเคราะห์ Root Cause / First Principles
2. หา 3 Options เปรียบเทียบ
3. เลือก The Best → สร้าง Roadmap

### ขั้นตอนที่ 3: รัน Loop
```bash
/axon:ignite
```

ระบบจะทำงานไม่หยุดจนกว่า:
- งานเสร็จ 100%
- ติด API limit
- คุณพิมพ์ "หยุด"

---

## 🔧 คำสั่งทั้งหมด

### `/axon:setup`
สร้างไฟล์ระบบ AXON ทั้งหมด

**ไฟล์ที่สร้าง:**
```
📁 โปรเจคของคุณ/
├── CLAUDE.md          # Master Blueprint
├── AXON_STATE.md      # System State (RAM)
├── AXON_MAP.md        # Task Roadmap
├── AXON_KNOWLEDGE.md  # Knowledge Vault
├── .axon/
│   └── config.md      # Configuration
└── .gitignore
```

---

### `/axon:concept [task]`
วางแผนงานแบบ Architecture First

**ตัวอย่าง:**
```bash
/axon:concept เพิ่มระบบ notification แบบ real-time
/axon:concept refactor database layer ให้รองรับ sharding
/axon:concept สร้าง API สำหรับ mobile app
```

**Output:**
- วิเคราะห์ปัญหาลึกๆ
- เปรียบเทียบ 3 วิธีแก้
- สร้าง Roadmap ใน AXON_MAP.md

---

### `/axon:ignite`
รัน Zenith Loop - ทำงานไม่หยุดจนเสร็จ

**Flow:**
```
┌─────────────────────────────────────────────────┐
│                 ZENITH LOOP                     │
├─────────────────────────────────────────────────┤
│  1. อ่าน AXON_MAP.md หางาน [ ] ที่ยังไม่เสร็จ    │
│  2. ทำงานจนเสร็จ                                 │
│  3. Mark [x] และบันทึก Knowledge                │
│  4. สร้างงานใหม่ถ้าจำเป็น                        │
│  5. วนกลับ Step 1                               │
│                                                 │
│  ❌ ห้ามหยุด ❌ ห้ามถาม ❌ ห้ามรอ                │
└─────────────────────────────────────────────────┘
```

**หยุด Loop:**
- พิมพ์ `หยุด` หรือ `stop`
- ติด API limit

---

### `/axon:mcp [action]`
จัดการ MCP Servers

**Actions:**

| Action | รายละเอียด | ตัวอย่าง |
|--------|-----------|---------|
| `list` | แสดง MCP ที่ติดตั้ง | `/axon:mcp list` |
| `recommend` | แนะนำ MCP ที่เหมาะ | `/axon:mcp recommend` |
| `add <name>` | เพิ่ม MCP | `/axon:mcp add puppeteer` |
| `remove <name>` | ลบ MCP | `/axon:mcp remove sqlite` |

**MCP ที่รองรับ:**

| หมวด | MCP | ใช้สำหรับ |
|------|-----|---------|
| **Web** | puppeteer | ควบคุม browser |
| **Web** | fetch | ดึงข้อมูล URL |
| **Database** | sqlite, postgres | SQL database |
| **NoSQL** | mongodb | MongoDB + Vector |
| **Vector** | qdrant, chroma, pinecone | Vector search |
| **AI** | huggingface | Models, Datasets |
| **Cloud** | digitalocean | DO resources |

---

## 🧠 Knowledge Base Types

### 1. Text Files (Default)
ใช้ `AXON_KNOWLEDGE.md` เก็บความรู้แบบ Markdown

```markdown
---
id: unique-id
tags: [topic, subtopic]
quality: zenith-verified
---

### หัวข้อความรู้

เนื้อหาที่ตกผลึกแล้ว...
```

**ข้อดี:** ง่าย, ไม่มีค่าใช้จ่าย, version control ได้
**ข้อเสีย:** ไม่รองรับ semantic search

---

### 2. DigitalOcean Gradient
ใช้ OpenSearch + Embedding Models

**Setup:**
1. สร้าง DO Account
2. ไปที่ Gradient AI Platform
3. สร้าง Knowledge Base
4. เลือก Embedding Model

**Embedding Models:**

| Model | ราคา | แนะนำ |
|-------|------|------|
| gte-large-en-v1.5 | $0.09/1M tokens | Production |
| all-mini-lm-l6-v2 | $0.01/1M tokens | Development |
| Qwen3 0.6B | $0.04/1M tokens | Thai/Multilingual |

**ข้อดี:** Semantic search, Managed service
**ข้อเสีย:** มีค่าใช้จ่าย

---

### 3. MongoDB Atlas Vector
ใช้ MongoDB + Voyage AI Embedding

**Setup:**
1. สร้าง MongoDB Atlas cluster
2. Enable Vector Search
3. สร้าง Voyage AI account
4. ติดตั้ง MCP: `/axon:mcp add mongodb`

**ข้อดี:** ใช้ MongoDB เดิมได้, Auto-embedding
**ข้อเสีย:** ต้องมี Voyage AI key

---

### 4. Local Vector (Qdrant/Chroma)
รัน Vector DB บนเครื่อง

**Setup Qdrant:**
```bash
# Docker
docker run -p 6333:6333 qdrant/qdrant

# MCP
/axon:mcp add qdrant
```

**Setup Chroma:**
```bash
# MCP
/axon:mcp add chroma
```

**ข้อดี:** ฟรี, Privacy, เร็ว
**ข้อเสีย:** ต้อง embed เอง

---

## 📁 ไฟล์ระบบ

### CLAUDE.md
Master Blueprint - กฎและพฤติกรรมของระบบ

### AXON_STATE.md
System State - สถานะปัจจุบัน, Resume Point

### AXON_MAP.md
Task Roadmap - รายการงานทั้งหมด

**Format:**
```markdown
- [x] [T001] งานที่เสร็จแล้ว
- [ ] [T002] งานที่ยังไม่เสร็จ ← ระบบจะทำอันนี้
- [ ] [T003] งานถัดไป
```

### AXON_KNOWLEDGE.md
Knowledge Vault - ความรู้ที่ตกผลึกแล้ว

### .axon/config.md
Configuration - ตั้งค่า Knowledge Base, MCP

---

## 🔄 การอัพเดท Plugin

### อัพเดทเป็นเวอร์ชันล่าสุด
```bash
/plugin update axon-zenith
```

### ดูเวอร์ชันปัจจุบัน
```bash
/plugin list
```

---

## ❓ FAQ

### Q: ทำไมระบบไม่หยุด?
**A:** นี่คือ design - ระบบจะทำงานไปเรื่อยๆ จนเสร็จ พิมพ์ `หยุด` ถ้าต้องการหยุด

### Q: เปลี่ยน Knowledge Base ได้ไหม?
**A:** ได้ แก้ไขที่ `.axon/config.md` แล้วรัน `/axon:mcp recommend`

### Q: รองรับภาษาไทยไหม?
**A:** รองรับ! ระบบจะรายงานเป็นภาษาไทยเสมอ

### Q: MCP ไม่ทำงาน?
**A:** หลังติดตั้ง MCP ต้อง Reload Claude Code:
- VSCode: `Ctrl+Shift+P` → "Developer: Reload Window"
- Terminal: ปิดแล้วเปิดใหม่

---

## 🆘 ขอความช่วยเหลือ

- **Issues:** https://github.com/vongsagon-git/axon-zenith/issues
- **Discussions:** https://github.com/vongsagon-git/axon-zenith/discussions

---

## 📜 License

MIT License - ใช้ได้ฟรี แก้ไขได้ แจกจ่ายได้

---

> **Remember:** "ช้าได้ แต่ห้ามห่วย" 💎
