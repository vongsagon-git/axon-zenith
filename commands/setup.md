---
description: "Setup AXON system - สร้างทุกไฟล์ที่จำเป็น (CLAUDE.md, STATE, MAP, KNOWLEDGE)"
---

# AXON SETUP PROTOCOL

## Mission
สร้างไฟล์ระบบ AXON **ทั้งหมด** ให้พร้อมใช้งาน + ถามเรื่อง Knowledge Base

## Execution Steps

### 0. ถาม Knowledge Base Configuration

**ถาม user ด้วย AskUserQuestion:**

```
🧠 เลือก Knowledge Base Type:

1. **Text Files (Default)**
   - ใช้ AXON_KNOWLEDGE.md เก็บความรู้
   - ไม่ต้อง setup เพิ่ม
   - เหมาะสำหรับ: โปรเจคเล็ก-กลาง

2. **DigitalOcean Gradient**
   - ใช้ OpenSearch + Embedding (gte-large, etc.)
   - ต้องมี DO Account + API Key
   - เหมาะสำหรับ: RAG, Production AI

3. **MongoDB Atlas Vector**
   - ใช้ MongoDB + Voyage AI Embedding
   - ต้องมี MongoDB Atlas + Voyage API Key
   - เหมาะสำหรับ: เพิ่ม vector search ให้ MongoDB เดิม

4. **Local Vector (Qdrant/Chroma)**
   - รัน vector DB บนเครื่อง
   - ไม่มีค่าใช้จ่าย cloud
   - เหมาะสำหรับ: Development, Privacy-first

5. **Skip (ตั้งค่าภายหลัง)**
   - ใช้ Text Files ก่อน
   - เพิ่ม Knowledge Base ทีหลังได้ด้วย /axon:mcp
```

### 0.1 บันทึก Knowledge Config

บันทึกตัวเลือกใน `.axon/config.md`:

```markdown
# AXON Configuration

## Knowledge Base
**Type:** [user choice]
**Status:** [configured/pending]

## Transform Settings
**Auto-embed:** [true/false]
**Embedding Model:** [model name if applicable]

## API Keys Required
- [ ] DigitalOcean API Key
- [ ] Voyage AI Key
- [ ] etc.
```

### 1. สร้างไฟล์ทั้งหมด (ถ้ายังไม่มี)

#### CLAUDE.md (Master Blueprint)

**Copy from:** `templates/CLAUDE.md`

> ⚠️ **Single Source of Truth:** ไฟล์ CLAUDE.md อยู่ที่ `templates/CLAUDE.md` (Master Blueprint v8.0)
>
> `/axon:setup` จะ copy จาก templates/ ไปโปรเจคที่ติดตั้ง

**วิธี Copy:**
```
1. Read templates/CLAUDE.md
2. Write to [project_root]/CLAUDE.md
```

**เนื้อหาใน templates/CLAUDE.md:**
- NEVER STOP PROTOCOL
- PARALLEL EXECUTION RULE (v1.4)
- DUAL POWER PROTOCOL (v1.4)
- AUDIT AGENT PROTOCOL (v1.4)
- ZENITH PROTOCOL
- SKILL COMMANDS
- และอื่นๆ...

#### AXON_STATE.md (The RAM)
```markdown
# 🧠 System State

**Last Update:** [Timestamp]
**Quality Score:** 0

## 🎯 Current Execution (Resume Point)

**Active Task:** None
**Progress:** -
**Last Action:** -

## 📋 Partial Results (กันงานหาย)

(ยังไม่มีผลลัพธ์ระหว่างทาง)

## 🛠️ Active Tools Protocol

- [x] Read/Write Files
- [x] Bash Commands
- [x] Web Search

## 📝 Context Dump

(ยังไม่มีงานที่กำลังทำ - รอรับคำสั่ง)
```

#### AXON_MAP.md (The Mission Plan)
```markdown
# 🗺️ Zenith Roadmap

> **Philosophy:** "ช้าได้ แต่ห้ามห่วย"

## 📋 Active Tasks

(ยังไม่มีงาน - ใช้ /axon:concept หรือ /axon:enlighten เพื่อเริ่มต้น)
```

#### AXON_KNOWLEDGE.md (The Wisdom Vault)
```markdown
# 💎 Zenith Knowledge Vault

> บันทึกเฉพาะสิ่งที่ **"ตกผลึกแล้ว"** และ **"ใช้งานได้จริง"**

---
id: system-init
tags: [axon, setup]
quality: zenith-verified
---

### ระบบ AXON พร้อมใช้งาน

- Setup เสร็จสมบูรณ์
- ไฟล์ระบบถูกสร้างแล้ว
- พร้อมรับคำสั่ง
```

### 2. สร้าง .gitignore (Best Practice)

```
# Dependencies
node_modules/

# OS files
.DS_Store
Thumbs.db

# IDE
.vscode/
.idea/

# Environment
.env
.env.local

# Logs
*.log

# Temp
tmpclaude-*
```

### 3. ตรวจสอบและสร้าง Git Repository

- ถ้ายังไม่มี `.git` → รัน `git init`

### 4. สร้าง folder .axon/ (ถ้ายังไม่มี)

- สร้าง folder `.axon/` เตรียมไว้สำหรับ MCP config

### 5. ตรวจสอบและแนะนำ MCP Servers

รัน `claude mcp list` และแนะนำ MCP **ตาม Knowledge Type ที่เลือก:**

#### IF Knowledge = Text Files:
| MCP | ใช้สำหรับ |
|-----|---------|
| fetch | ดึงข้อมูลจาก URL |
| puppeteer | ควบคุม browser |
| memory | Knowledge graph |

#### IF Knowledge = DigitalOcean Gradient:
| MCP | ใช้สำหรับ |
|-----|---------|
| digitalocean | จัดการ DO resources + Gradient |
| fetch | ดึงข้อมูลเข้า Knowledge Base |

> 📝 **Transform:** ใช้ DO API `/v2/gen-ai/knowledge_bases` เพื่อ index ข้อมูล

#### IF Knowledge = MongoDB Atlas:
| MCP | ใช้สำหรับ |
|-----|---------|
| mongodb | MongoDB + Atlas Vector Search |

> 📝 **Transform:** ใช้ Voyage AI embedding ผ่าน MCP

#### IF Knowledge = Local Vector:
| MCP | ใช้สำหรับ |
|-----|---------|
| qdrant | Vector search (แนะนำ) |
| chroma | Alternative vector DB |

> 📝 **Transform:** ต้อง embed เอง หรือใช้ HuggingFace MCP

### 6. แสดงคำสั่ง Transform (ถ้าเลือก Vector DB)

```markdown
## 📥 Transform Data (เพิ่มข้อมูลเข้า Knowledge Base)

### DigitalOcean Gradient:
\`\`\`bash
# สร้าง Knowledge Base + index ข้อมูลอัตโนมัติ
# ผ่าน DO Console หรือ API
POST /v2/gen-ai/knowledge_bases
\`\`\`

### MongoDB Atlas:
\`\`\`bash
# ใช้ MCP insert พร้อม auto-embedding
# ต้อง set voyageApiKey ใน config
\`\`\`

### Local Qdrant:
\`\`\`bash
# ใช้ HuggingFace MCP หรือ local embedding
# แล้ว insert เข้า Qdrant
\`\`\`
```

## Output

รายงานสถานะเป็นภาษาไทย:

```markdown
# ✅ AXON Setup Complete

## 📁 ไฟล์ที่สร้าง
- [x] CLAUDE.md (Master Blueprint)
- [x] AXON_STATE.md (System State)
- [x] AXON_MAP.md (Task Roadmap)
- [x] AXON_KNOWLEDGE.md (Knowledge Vault)
- [x] .axon/config.md (Configuration)
- [x] .gitignore

## 🧠 Knowledge Base
**Type:** [ที่เลือก]
**Status:** [configured/pending setup]
**Transform:** [ready/need API keys]

## 🔌 MCP Status
[รายการ MCP ที่แนะนำตาม Knowledge Type]

## ⚙️ ต้องทำเพิ่ม (ถ้ามี)
- [ ] เพิ่ม API Key ใน environment
- [ ] รัน `claude mcp add [name]`

## 🚀 Next Steps (เลือก Mode ที่เหมาะ)

### ⚡ Quick Start (เริ่มต้นใน 30 วินาที)

```
# มีงานชัดเจน? → วางแผนก่อน
/axon:concept สร้าง login page

# ไม่รู้จะทำอะไร? → สำรวจไปเลย
/axon:enlighten ปรับปรุง codebase นี้

# มี MAP แล้ว / กลับมาต่อ?
/axon:ignite
```

### 📋 ตาราง Mode เต็ม

| Mode | Command | ใช้เมื่อ | ผลลัพธ์ |
|------|---------|----------|---------|
| 📐 **Concept** | `/axon:concept [task]` | มีงานชัดเจน | วางแผน 3 Options → เลือก Best → สร้าง MAP → รอคำสั่ง |
| 🧘 **Enlighten** | `/axon:enlighten [topic]` | **ไม่รู้จะทำอะไร** / อยากสำรวจ | ตรัสรู้ → เจองาน → เพิ่ม MAP → **ทำเลยทันที!** |
| 🔥 **Ignite** | `/axon:ignite` | มี MAP แล้ว / Resume | ทำงานตาม MAP ไม่หยุดจนกว่าจะติด limit |

### 💡 เลือก Mode ไหนดี?

```
รู้แล้วว่าจะทำอะไร?
│
├── ✅ รู้ชัดเจน
│   └── /axon:concept [งาน]
│       → วางแผน 3 Options → เลือก Best → สร้าง MAP
│       → รอ user อนุมัติ → /axon:ignite ทำต่อ
│
└── ❌ ไม่รู้ / อยากสำรวจ / อยากให้ AI คิดให้
    └── /axon:enlighten [หัวข้อ]
        → AI สำรวจ codebase → เจองานก็ทำเลย!
        → MAP โตขึ้นเรื่อยๆ ระหว่างทำ
```

### 🔄 การกลับมาทำต่อ (Resume)

ไม่ว่าจะใช้ mode ไหน กลับมาทำต่อด้วย:
```
/axon:ignite
```
ระบบจะอ่าน MAP + STATE แล้วทำต่อจากจุดที่ค้างไว้อัตโนมัติ

---

💡 **Tips:**
- เปลี่ยน Knowledge Base ภายหลัง: `/axon:mcp recommend`
- ดูสถานะ MCP: `/axon:mcp list`
- เพิ่ม MCP ใหม่: `/axon:mcp add [name]`
```
