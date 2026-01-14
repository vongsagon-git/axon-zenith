# AXON Zenith

> **Autonomous Execution System for Claude Code**
> *"ช้าได้ แต่ห้ามห่วย"* (Lateness is acceptable, Mediocrity is not)

---

## 📥 Installation

### Clone จาก GitHub (แนะนำ)

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

> หลังติดตั้ง พิมพ์ `/axon` จะเห็น commands ทั้ง 5 ตัว

---

## 🚀 What is AXON?

AXON Zenith เปลี่ยน Claude ให้เป็น **Autonomous Agent** ที่:

- **ทำงานไม่หยุด** จนกว่า user จะสั่งหยุด หรือติด limit
- **Zenith Quality** - ทุกงานต้อง "สุด" ทุกมิติ
- **Live Thinking** - คิด task สดๆ ระหว่างทำ
- **Parallel Execution** - ทำหลายงานพร้อมกัน
- **รับใบ้ได้** - User ชี้ทางระหว่างทำได้ตลอด

---

## 🎯 Commands

| Command | Description |
|---------|-------------|
| `/axon:setup` | Setup AXON + เลือก Knowledge Base |
| `/axon:concept [task]` | วางแผนงานแบบ Architecture First |
| `/axon:ignite` | เริ่ม Zenith Loop - ทำงานไม่หยุด |
| `/axon:enlighten [topic]` | ขุดข้อมูลไม่หยุด - คิดสดๆ - รับใบ้ได้ |
| `/axon:mcp [action]` | จัดการ MCP Servers |
| `/axon:upgrade` | อัพเกรดโปรเจคเก่าให้รองรับ version ใหม่ |

---

## 🔥 Quick Start

```bash
# 1. Setup AXON ในโปรเจค
/axon:setup

# 2. วางแผนงาน
/axon:concept สร้าง todo app ด้วย React

# 3. เริ่มทำงาน (Loop ไม่หยุด!)
/axon:ignite
```

หรือถ้าต้องการขุดข้อมูล:

```bash
# ขุดข้อมูลแบบไม่หยุด
/axon:enlighten ประวัติ Elon Musk ทุกมิติ

# ระหว่างขุด user สามารถใบ้ได้:
# "ลองหาจาก LinkedIn ด้วย"
# "ขุดเรื่องครอบครัวเพิ่ม"
```

---

## 📋 How Each Command Works

### 📐 `/axon:concept` - วางแผน

```
User: /axon:concept สร้างระบบ login

Claude:
┌─────────────────────────────────────────┐
│ 🤖 Opus 4.5 | 📐 CONCEPT | 📋 Planning │
└─────────────────────────────────────────┘

🔍 วิเคราะห์: ระบบ login

📊 3 OPTIONS:
| Option | วิธี | ข้อดี | ข้อเสีย |
|--------|------|-------|---------|
| A | JWT + bcrypt | เร็ว, Stateless | ต้อง handle refresh |
| B | Session-based | ง่าย | ต้องมี store |
| C | OAuth only | ไม่ต้อง manage password | depend 3rd party |

🏆 เลือก: Option A

📋 สร้าง Roadmap → AXON_MAP.md
```

### 🔥 `/axon:ignite` - ทำงาน

```
User: /axon:ignite

Claude:
┌─────────────────────────────────────────┐
│ 🤖 Opus 4.5 | 🔥 IGNITE | 📋 [T001]    │
│ 📊 0/5 tasks | Setup JWT               │
└─────────────────────────────────────────┘

⚡ กำลังทำ: [T001] Setup JWT authentication
...
✅ เสร็จ

┌─────────────────────────────────────────┐
│ 🤖 Opus 4.5 | 🔥 IGNITE | 📋 [T002]    │
│ 📊 1/5 tasks | Create login endpoint   │
└─────────────────────────────────────────┘

⚡ กำลังทำ: [T002] Create login endpoint
...
(วนต่อไปเรื่อยๆ จนกว่า user จะสั่งหยุด)
```

### 🧘 `/axon:enlighten` - ขุดข้อมูล

```
User: /axon:enlighten ประวัติ Elon Musk

Claude:
┌─────────────────────────────────────────┐
│ 🤖 Opus 4.5 | 🧘 ENLIGHTEN | Elon Musk │
│ 🔍 Dimension: 1 | Sources: 0           │
└─────────────────────────────────────────┘

[ค้น Wikipedia] → ได้ข้อมูลพื้นฐาน
💡 เจอ: มีบริษัทหลายอัน → ต้องขุดแต่ละอัน

[ค้น Tesla] [ค้น SpaceX] [ค้น X] (Parallel)
💡 เจอ: มีคดีความ SEC → ต้องขุดเพิ่ม

[ค้น SEC filings] [ค้น Lawsuits]
...

User: ลองหาจาก LinkedIn ด้วย    ← (ใบ้)

Claude:
💡 รับใบ้: หา LinkedIn
[ค้น LinkedIn profile]
...

(วนต่อไปเรื่อยๆ จนกว่า user จะสั่งหยุด)
```

---

## 🔄 Core Philosophy: ไม่มีจุดจบ

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

## 🖥️ Status Display

ทุก Mode จะแสดง Status ให้ user รู้ว่ากำลังทำอะไร:

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

## 🔗 Concept Modes

`/axon:concept` รองรับหลาย modes:

| Mode | วิธีใช้ | ทำอะไร |
|------|--------|-------|
| **NEW** | `/axon:concept สร้าง X` | สร้าง roadmap ใหม่ |
| **ADD** | `/axon:concept เพิ่ม: Y` | เพิ่มต่อ roadmap เดิม |
| **MODIFY** | `/axon:concept แก้: [ID]` | แก้ไข task ที่มี |
| **EXPAND** | `/axon:concept ขยาย: [ID]` | แตก task เป็น sub-tasks |
| **LINK** | `/axon:concept รวม` | สร้าง Master Roadmap |

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

## 📁 Files Created

เมื่อรัน `/axon:setup` จะสร้างไฟล์:

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

## 🔌 MCP Integration

```bash
# ดู MCP ที่ติดตั้ง
/axon:mcp list

# ดูคำแนะนำ
/axon:mcp recommend

# เพิ่ม MCP
/axon:mcp add puppeteer
```

**MCP ที่รองรับ:**
- puppeteer, fetch, brave-search
- sqlite, postgres, mongodb
- qdrant, chroma, pinecone
- huggingface, digitalocean

---

## 💎 The Zenith Protocol

ทุกงานต้องผ่าน **3 Quality Gates**:

1. **Deepest Dive** - ขุดลึกถึง Root Cause
2. **Comparative Selection** - หา 3 Options เปรียบเทียบ
3. **Structured Output** - จัดเรียงสวยงาม อ่านง่าย

---

## 🔄 Update Plugin

**อัพเดทเป็นเวอร์ชันล่าสุด:**

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

## 📖 Documentation

- **[คู่มือการใช้งาน (Thai)](GUIDE.md)** - คู่มือฉบับเต็มภาษาไทย
- **[Issues](https://github.com/vongsagon-git/axon-zenith/issues)** - รายงานปัญหา
- **[Discussions](https://github.com/vongsagon-git/axon-zenith/discussions)** - ถาม-ตอบ

---

## 🗺️ Roadmap

- [x] **v1.0** - Core Plugin (4 Commands)
- [x] **v1.1** - Enlighten Mode (ตรัสรู้)
- [x] **v1.1** - Status Display
- [x] **v1.1** - Token Management
- [x] **v1.1** - Concept Modes (NEW, ADD, MODIFY, EXPAND, LINK)
- [ ] **v2.0** - Multi-Agent Support
- [ ] **v2.0** - Vector Memory

---

## 📝 License

MIT License - ใช้ได้ฟรี แก้ไขได้ แจกจ่ายได้

---

**Made with 💎 by vongsagon-git**
