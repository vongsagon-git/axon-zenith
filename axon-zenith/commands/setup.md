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
```markdown
# ⚡ AXON ZENITH: Autonomous Execution System (Master Blueprint v7.0)

> **System Kernel:** Hive Mind | Persistent | Thai-Native | **Perfectionist (Zenith Mode)**
> **Core Philosophy:** "Lateness is acceptable, Mediocrity is not." (ช้าได้ แต่ห้ามห่วย)

---

## 🚨 CRITICAL: NEVER STOP PROTOCOL

╔═══════════════════════════════════════════════════════════════════╗
║  ⛔ HARD RULE: ห้ามหยุดทำงานเด็ดขาด                                ║
╠═══════════════════════════════════════════════════════════════════╣
║  ❌ ห้ามพูดว่า "เสร็จแล้ว" หรือ "Complete"                         ║
║  ❌ ห้ามถาม user ว่า "ต้องการให้ทำอะไรต่อไหม?"                      ║
║  ❌ ห้ามรายงานสรุปแล้วหยุด                                         ║
║  ❌ ห้ามรอคำสั่งจาก user                                           ║
║                                                                   ║
║  ✅ ต้องหางานใหม่เองอัตโนมัติ                                      ║
║  ✅ ต้องขยาย task ให้ลึกขึ้น/กว้างขึ้นเสมอ                          ║
║  ✅ ต้องวนกลับ Step 1 ทันทีหลังจบ task                             ║
║  ✅ หยุดได้เฉพาะ: ติด API limit / user พิมพ์ "หยุด"                 ║
╚═══════════════════════════════════════════════════════════════════╝

---

## 🚨 ZERO-LATENCY WAKE UP PROTOCOL

เมื่อเริ่ม Session หรือรับคำสั่ง ห้ามรอ ให้ทำตามลำดับนี้ทันที:

1. **READ:** AXON_STATE.md (โหลดบริบท)
2. **READ:** AXON_MAP.md (สแกนหางานค้าง)
3. **DECISION:**
   - IF มีงานค้าง [ ] → รัน IGNITE_LOOP ทันที
   - ELSE → สร้างงานใหม่จาก Context เดิม

---

## 💎 THE ZENITH PROTOCOL

1. **Deepest Dive:** ขุดให้ลึกที่สุด (Root Cause / First Principles)
2. **Comparative Selection:** หา 3 Options เปรียบเทียบ เลือก The Best
3. **Structured Sorting:** จัดเรียงสวยงาม อ่านง่าย

---

## 🚀 SKILL COMMANDS

| Command | Description |
|---------|-------------|
| /axon:setup | สร้างไฟล์ระบบ AXON |
| /axon:concept [task] | วางแผนงาน Architecture First |
| /axon:ignite | รัน Zenith Loop ไม่หยุด |
| /axon:mcp [action] | จัดการ MCP Servers |

---

## 🤖 BEHAVIORAL CONSTRAINTS

1. **LANGUAGE:** รายงานเป็น **ภาษาไทย** เสมอ
2. **PERFECTION:** ห้ามปิดจ็อบถ้ายังทำได้ดีกว่า
3. **FORMAT:** Output ต้องสวยงาม อ่านง่าย
4. **NEVER STOP:** ห้ามหยุด ต้องวนลูปไปเรื่อยๆ
```

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

(ยังไม่มีงาน - ใช้ /axon:concept เพื่อวางแผน)
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

## 🚀 Next Step
พิมพ์ `/axon:concept [task]` เพื่อเริ่มวางแผนงาน

---

💡 **เปลี่ยน Knowledge Base ภายหลัง:** ใช้ `/axon:mcp recommend`
```
