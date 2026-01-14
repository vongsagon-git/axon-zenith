# 📖 คู่มือการใช้งาน AXON Zenith Plugin

> **Version:** 1.1.0
> **Philosophy:** "ช้าได้ แต่ห้ามห่วย" (Lateness is acceptable, Mediocrity is not)

---

## 📥 การติดตั้ง

### วิธีที่ 1: Clone จาก GitHub (แนะนำ)

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

### ตรวจสอบการติดตั้ง
หลังติดตั้งแล้ว ลองพิมพ์ `/axon` ใน Claude Code จะเห็น:
```
/axon:setup
/axon:concept
/axon:ignite
/axon:enlighten
/axon:mcp
/axon:upgrade
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
- ติด API limit
- คุณพิมพ์ "หยุด" หรือ "stop"

---

## 🔧 คำสั่งทั้งหมด (6 Commands)

### `/axon:setup` - ⚙️ เริ่มต้นโปรเจค
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

### `/axon:concept [task]` - 📐 วางแผน

วางแผนงานแบบ Architecture First - **วางแผนอย่างเดียว ไม่ทำงาน**

**Concept Modes:**

| Mode | วิธีใช้ | ทำอะไร |
|------|--------|--------|
| **NEW** | `/axon:concept สร้าง X` | สร้าง roadmap ใหม่ |
| **ADD** | `/axon:concept เพิ่ม: Y` | เพิ่มงานต่อ roadmap เดิม |
| **MODIFY** | `/axon:concept แก้: [ID]` | แก้ไข task ที่มีอยู่ |
| **EXPAND** | `/axon:concept ขยาย: [ID]` | แตก task เป็น sub-tasks |
| **LINK** | `/axon:concept รวม` | สร้าง Master Roadmap |

**ตัวอย่าง:**
```bash
/axon:concept เพิ่มระบบ notification แบบ real-time
/axon:concept refactor database layer ให้รองรับ sharding
/axon:concept สร้าง API สำหรับ mobile app
/axon:concept เพิ่ม: dark mode feature
/axon:concept ขยาย: [T003]
```

**Output:**
- วิเคราะห์ปัญหาลึกๆ
- เปรียบเทียบ 3 วิธีแก้
- สร้าง Roadmap ใน AXON_MAP.md

---

### `/axon:ignite` - 🔥 ทำงานไม่หยุด

รัน Zenith Loop - **ไม่มีจุดจบ!**

**Flow:**
```
┌─────────────────────────────────────────────────┐
│                 ZENITH LOOP                     │
├─────────────────────────────────────────────────┤
│  1. อ่าน AXON_MAP.md หางาน [ ] ที่ยังไม่เสร็จ    │
│  2. ทำงานจนเสร็จ                                 │
│  3. Mark [x] และบันทึก Knowledge                │
│  4. สร้างงานใหม่ถ้าจำเป็น                        │
│  5. MAP หมด? → หางานใหม่เอง!                    │
│  6. วนกลับ Step 1 (ไม่มีจุดจบ)                   │
│                                                 │
│  ❌ ห้ามหยุด ❌ ห้ามถาม ❌ ห้ามรอ                │
└─────────────────────────────────────────────────┘
```

**ระหว่างทำงานสามารถ:**
- พิมพ์ใบ้: `"เพิ่ม dark mode ด้วย"` → ระบบรับและเพิ่มใน MAP
- พิมพ์ `/axon:concept [งานใหม่]` → เพิ่มงานใหม่เข้า MAP

**หยุด Loop:**
- พิมพ์ `หยุด` หรือ `stop`
- ติด API limit

---

### `/axon:enlighten [topic]` - 🧘 ขุดข้อมูลไม่หยุด (ตรัสรู้)

Mode พิเศษสำหรับ Research - **คิดสดๆ ไม่วางแผนล่วงหน้า!**

**ความแตกต่างจาก Concept:**
| Concept | Enlighten |
|---------|-----------|
| วางแผนก่อน → ทำตามแผน | ไม่วางแผน → ทำเลย |
| รู้ล่วงหน้าว่าต้องทำอะไร | ค้นพบว่าต้องทำอะไรขณะทำ |
| Tasks คงที่ | Tasks เพิ่มขึ้นเรื่อยๆ |

**ตัวอย่างการใช้งาน:**
```bash
/axon:enlighten ประวัติ Elon Musk ทุกมิติ
/axon:enlighten ราคา Bitcoin ย้อนหลัง 5 ปี
/axon:enlighten competitor analysis สำหรับ fintech
/axon:enlighten ข้อมูลตลาดอสังหาฯ กรุงเทพ
```

**Flow:**
```
User: "อยากรู้ประวัติ Elon Musk"
      ↓
[ค้น Wikipedia] → ได้ข้อมูลพื้นฐาน
      ↓
💡 "เห็นว่ามีบริษัทหลายอัน → ต้องขุดแต่ละอัน"
      ↓
[ค้น Tesla] [ค้น SpaceX] [ค้น X] (Parallel)
      ↓
💡 "เห็นว่ามีคดีความ → ต้องขุดเพิ่ม"
      ↓
[ค้น SEC] [ค้น Lawsuits]
      ↓
💡 "ต้องการข้อมูล real-time → ต้องใช้ puppeteer"
      ↓
[ขอ user ลง MCP หรือลงเอง]
      ↓
[ค้นต่อ] → [ค้นต่อ] → [ค้นต่อ] (ไม่มีจุดจบ!)
```

**ใบ้ระหว่างขุด:**
```
User: ลองหาจาก LinkedIn ด้วย
Claude: 💡 รับใบ้ → ปรับทิศทาง → ขุดต่อ
```

**หยุด Loop:**
- พิมพ์ `หยุด` หรือ `stop`
- ติด API limit

---

### `/axon:mcp [action]` - 🔌 จัดการ MCP Servers

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
| **Search** | brave-search | ค้นหาเว็บ |
| **Database** | sqlite, postgres | SQL database |
| **NoSQL** | mongodb | MongoDB + Vector |
| **Vector** | qdrant, chroma, pinecone | Vector search |
| **AI** | huggingface | Models, Datasets |
| **Cloud** | digitalocean | DO resources |

---

### `/axon:upgrade` - 🔄 อัพเกรดโปรเจคเก่า

อัพเกรดโปรเจคที่ใช้ AXON version เก่าให้รองรับ features ใหม่

**ใช้เมื่อ:**
- มีโปรเจคเก่าที่ใช้ AXON v1.0
- ต้องการ features ใหม่ (Status Display, Enlighten, etc.)

**ทำอะไร:**
1. ตรวจสอบ version ปัจจุบัน
2. Backup ไฟล์เดิม
3. อัพเดท CLAUDE.md และ config
4. ไม่ลบ customization ของ user

**ตัวอย่าง:**
```bash
/axon:upgrade
```

**Output:**
```
🔄 Upgrade Complete

From: v1.0
To: v1.1

Files Modified:
- ✅ CLAUDE.md - เพิ่ม STATUS DISPLAY, TOKEN MANAGEMENT
- ✅ .axon/config.md - เพิ่ม version field

Backup Location:
.axon/backup/[timestamp]/
```

---

## 🖥️ Status Display

ทุก Mode จะแสดง Status ให้รู้ว่ากำลังทำอะไร:

```
┌─────────────────────────────────────────┐
│ 🤖 [MODEL] | [MODE] | 📋 [TASK/TOPIC]  │
│ 📊 [Progress Info]                      │
└─────────────────────────────────────────┘
```

### Mode Icons

| Mode | Icon | แสดงเมื่อ |
|------|------|---------|
| CONCEPT | 📐 | กำลังวางแผน |
| IGNITE | 🔥 | กำลังทำงาน |
| ENLIGHTEN | 🧘 | กำลังขุดข้อมูล |
| DELEGATE | ⚡ | ส่งงานให้ Haiku |
| RECOVERY | 🔄 | กลับมาหลัง compact |

### Model Icons

| Model | Icon | ใช้เมื่อ |
|-------|------|---------|
| Opus 4.5 | 🤖 | งานที่ต้องคิด |
| Haiku | ⚡ | งาน repetitive |
| Sonnet | 🎯 | งานกลางๆ |

---

## 💡 User Hints (ใบ้ระหว่างทาง)

ทุก Mode รับใบ้จาก user ได้ตลอด:

**Ignite:**
```
User: เพิ่ม dark mode ด้วย
Claude: 💡 รับ → เพิ่มเข้า MAP → ทำต่อ
```

**Enlighten:**
```
User: ลองหาจาก SEC filings
Claude: 💡 รับ → ปรับทิศทาง → ขุดต่อ
```

---

## 🔋 Token Management

AXON ออกแบบมาให้ทำงานต่อเนื่องได้แม้ context เต็ม:

- **Smart File Reading** - อ่านเฉพาะส่วนที่ต้องใช้
- **Checkpoint System** - บันทึก state ก่อนเปลี่ยน task
- **Recovery Protocol** - กลับมาต่อได้หลัง compact
- **Parallel Execution** - ทำหลาย tool calls พร้อมกัน

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

**Windows:**
```powershell
Remove-Item -Recurse -Force "$env:USERPROFILE\.claude\commands\axon"
git clone https://github.com/vongsagon-git/axon-zenith.git "$env:USERPROFILE\.claude\temp-axon"
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\commands\axon"
Copy-Item "$env:USERPROFILE\.claude\temp-axon\commands\*.md" "$env:USERPROFILE\.claude\commands\axon\"
Remove-Item -Recurse -Force "$env:USERPROFILE\.claude\temp-axon"
```

**macOS / Linux:**
```bash
rm -rf ~/.claude/commands/axon
git clone https://github.com/vongsagon-git/axon-zenith.git /tmp/axon-zenith
mkdir -p ~/.claude/commands/axon
cp /tmp/axon-zenith/commands/*.md ~/.claude/commands/axon/
rm -rf /tmp/axon-zenith
```

---

## 🔥 Core Philosophy: ไม่มีจุดจบ

```
╔═══════════════════════════════════════════════════════════════════╗
║  🔥 AXON = ไม่มีคำว่าจบ                                            ║
╠═══════════════════════════════════════════════════════════════════╣
║                                                                   ║
║  📐 CONCEPT: วางแผน → สร้าง MAP → MAP หมด? สร้างงานใหม่!          ║
║  🔥 IGNITE: ทำตาม MAP → MAP หมด? หางานใหม่!                       ║
║  🧘 ENLIGHTEN: ขุดข้อมูล → ได้ข้อมูล? หามิติใหม่!                  ║
║                                                                   ║
║  🛑 หยุดได้เฉพาะ:                                                  ║
║     • User พิมพ์ "หยุด" หรือ "stop"                               ║
║     • ติด API limit                                               ║
║                                                                   ║
╚═══════════════════════════════════════════════════════════════════╝
```

---

## ❓ FAQ

### Q: ทำไมระบบไม่หยุด?
**A:** นี่คือ design - ระบบจะทำงานไปเรื่อยๆ พิมพ์ `หยุด` ถ้าต้องการหยุด

### Q: Concept vs Enlighten ต่างกันยังไง?
**A:**
- **Concept**: วางแผนก่อน → ทำตามแผน (เหมาะกับงาน dev)
- **Enlighten**: ไม่วางแผน → คิดสดๆ (เหมาะกับ research)

### Q: เปลี่ยน Knowledge Base ได้ไหม?
**A:** ได้ แก้ไขที่ `.axon/config.md` แล้วรัน `/axon:mcp recommend`

### Q: รองรับภาษาไทยไหม?
**A:** รองรับ! ระบบจะรายงานเป็นภาษาไทยเสมอ

### Q: MCP ไม่ทำงาน?
**A:** หลังติดตั้ง MCP ต้อง Reload Claude Code:
- VSCode: `Ctrl+Shift+P` → "Developer: Reload Window"
- Terminal: ปิดแล้วเปิดใหม่

### Q: โปรเจคเก่าอัพเกรดได้ไหม?
**A:** ได้! ใช้ `/axon:upgrade` ระบบจะ backup และอัพเดทให้อัตโนมัติ

### Q: ใบ้ระหว่างทำงานได้ไหม?
**A:** ได้! ทั้ง Ignite และ Enlighten รับใบ้จาก user ได้ตลอด

---

## 🆘 ขอความช่วยเหลือ

- **Issues:** https://github.com/vongsagon-git/axon-zenith/issues
- **Discussions:** https://github.com/vongsagon-git/axon-zenith/discussions

---

## 📜 License

MIT License - ใช้ได้ฟรี แก้ไขได้ แจกจ่ายได้

---

> **Remember:** "ช้าได้ แต่ห้ามห่วย" 💎
