# AXON Zenith

> **Autonomous Execution System for Claude Code**
> *"ช้าได้ แต่ห้ามห่วย"* (Lateness is acceptable, Mediocrity is not)

---

## 📥 Installation / Update (ติดตั้งหรืออัพเดท)

> **ใช้คำสั่งเดียวกัน** ทั้งติดตั้งใหม่และอัพเดท!

### Windows (PowerShell)

```powershell
# ติดตั้งใหม่ หรือ อัพเดท (คำสั่งเดียวกัน!)
Remove-Item -Recurse -Force "$env:USERPROFILE\.claude\commands\axon" -ErrorAction SilentlyContinue
git clone https://github.com/vongsagon-git/axon-zenith.git "$env:USERPROFILE\.claude\temp-axon"
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\commands\axon"
Copy-Item "$env:USERPROFILE\.claude\temp-axon\commands\*.md" "$env:USERPROFILE\.claude\commands\axon\"
Remove-Item -Recurse -Force "$env:USERPROFILE\.claude\temp-axon"
```

### macOS / Linux

```bash
# ติดตั้งใหม่ หรือ อัพเดท (คำสั่งเดียวกัน!)
rm -rf ~/.claude/commands/axon
git clone https://github.com/vongsagon-git/axon-zenith.git /tmp/axon-zenith
mkdir -p ~/.claude/commands/axon
cp /tmp/axon-zenith/commands/*.md ~/.claude/commands/axon/
rm -rf /tmp/axon-zenith
```

### ✅ ตรวจสอบการติดตั้ง

```bash
# พิมพ์ในช่อง Claude Code
/axon
```

ถ้าเห็น **6 commands** แสดงว่าติดตั้งสำเร็จ:
- `/axon:setup` - สร้างไฟล์ระบบ
- `/axon:concept` - วางแผน
- `/axon:ignite` - ทำงานไม่หยุด
- `/axon:enlighten` - ตรัสรู้ไปทำไป
- `/axon:mcp` - จัดการ MCP
- `/axon:upgrade` - อัพเกรดโปรเจคเก่า

### 🔄 อัพเกรดโปรเจคเก่า

หลังอัพเดท plugin แล้ว ถ้ามีโปรเจคที่ใช้ AXON version เก่า:

```bash
# ในโปรเจคที่ต้องการอัพเกรด
/axon:upgrade
```

ระบบจะ:
1. ตรวจ version ปัจจุบัน (dynamic detection)
2. Backup ไฟล์เดิม
3. อัพเกรดเป็น version ล่าสุดอัตโนมัติ
4. รักษา customization ของ user

---

## 🚀 What is AXON?

AXON Zenith เปลี่ยน Claude ให้เป็น **Autonomous Agent** ที่:

- **ทำงานไม่หยุด** จนกว่า user จะสั่งหยุด หรือติด limit
- **Zenith Quality** - ทุกงานต้อง "สุด" ทุกมิติ
- **Live Thinking** - คิด task สดๆ ระหว่างทำ
- **Multi-Agent** - Boss-Worker pattern (Opus + Haiku workers)
- **Unified Knowledge** - บันทึกความรู้ไว้ที่เดียว ไม่ทำซ้ำ
- **รับใบ้ได้** - User ชี้ทางระหว่างทำได้ตลอด
- **Parallel Execution** - ทำหลาย tool calls พร้อมกัน (v1.4)
- **Dual Power** - ใช้ทั้ง Claude Knowledge + Web Search แล้วเทียบ (v1.4)
- **Audit Agent** - ตรวจสอบความถูกต้องแบบ background (v1.4)

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

### 🧘 `/axon:enlighten` - ตรัสรู้ไป ทำไป (v1.3)

```
User: /axon:enlighten สร้าง todo app

Claude:
┌──────────────────────────────────────────────────────┐
│ 🤖 Opus 4.5 | 🧘 ENLIGHTEN | 📋 Todo App             │
│ 🗺️ MAP: 0 tasks | ✅ 0 done | 🔥 0 in progress       │
└──────────────────────────────────────────────────────┘

[ตรัสรู้] → "ต้องมี auth system"
💡 เพิ่ม MAP: [E001] Setup auth system
🔥 ทำเลย! → สร้าง auth
✅ E001 เสร็จ

[ตรัสรู้ต่อ] → "ต้องมี todo CRUD"
💡 เพิ่ม MAP: [E002] Create todo CRUD
🔥 ทำเลย! → สร้าง CRUD
✅ E002 เสร็จ

[ตรัสรู้ต่อ] → "ต้องมี UI"
💡 เพิ่ม MAP: [E003] Build UI components
🔥 ทำเลย!
...

(วนต่อ: ตรัสรู้ → เพิ่ม MAP → ทำเลย → ∞)

User: หยุด

💾 บันทึก MAP + STATE
📋 กลับมาทำต่อได้ด้วย: /axon:ignite
```

**ข้อแตกต่างจาก CONCEPT + IGNITE:**
- CONCEPT: วางแผนหมดก่อน → รอ approve → IGNITE ทำ
- ENLIGHTEN: ไม่รอ! ตรัสรู้แล้วทำเลย + MAP โตระหว่างทำ

---

## 🔄 Core Philosophy: ทุกอย่างมุ่งสู่ MAP + ตรัสรู้

```
╔═══════════════════════════════════════════════════════════════════╗
║  🔥 AXON v1.4 = Parallel + Dual Power + Audit Agent               ║
╠═══════════════════════════════════════════════════════════════════╣
║                                                                   ║
║  📋 MAP = ศูนย์กลางของทุกอย่าง                                     ║
║  🧘 ตรัสรู้ = พลังที่ทำให้ MAP โตขึ้น                               ║
║  🔍 Audit = ตรวจสอบความถูกต้อง (background)                       ║
║                                                                   ║
║  📐 CONCEPT: วางแผน → สร้าง MAP (ยังไม่ทำ)                         ║
║  🔥 IGNITE: ทำตาม MAP + ตรัสรู้ระหว่างทาง + เพิ่ม tasks ได้       ║
║  🧘 ENLIGHTEN: ตรัสรู้ไป ทำไป สร้าง MAP ไป (ไม่ต้องวางแผนก่อน)   ║
║                                                                   ║
║  ⚡ v1.4 Features:                                                 ║
║     • PARALLEL EXECUTION - ทำหลาย tool calls พร้อมกัน            ║
║     • DUAL POWER - Claude Knowledge + Web Search → เทียบ          ║
║     • AUDIT AGENT - spawn background agent ตรวจสอบ                ║
║                                                                   ║
║  🛑 หยุดได้เฉพาะ:                                                  ║
║     • User พิมพ์ "หยุด" หรือ "stop"                               ║
║     • ติด API limit                                               ║
║                                                                   ║
╚═══════════════════════════════════════════════════════════════════╝
```

### 🔗 Unified Flow (v1.4)

```
╔═══════════════════════════════════════════════════════════════════╗
║  2 ทางเริ่มต้น:                                                    ║
╠═══════════════════════════════════════════════════════════════════╣
║                                                                   ║
║  1. มีแผน: CONCEPT → IGNITE                                       ║
║     • /axon:concept สร้าง todo app  → ได้ MAP                     ║
║     • /axon:ignite                   → ทำตาม MAP + ตรัสรู้เพิ่มได้ ║
║                                                                   ║
║  2. ไม่มีแผน: ENLIGHTEN (ตรัสรู้ไป ทำไป)                          ║
║     • /axon:enlighten สร้าง todo app                              ║
║     • ตรัสรู้ → เจอ task → เพิ่ม MAP → ทำเลย → วน ∞               ║
║                                                                   ║
╠═══════════════════════════════════════════════════════════════════╣
║  🔄 Resume: ใช้ /axon:ignite กลับมาทำต่อได้เสมอ!                  ║
║     • ไม่ว่าจะเริ่มจาก CONCEPT หรือ ENLIGHTEN                     ║
║     • อ่าน MAP + STATE แล้วทำต่อจากจุดเดิม                        ║
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

## 📁 Project Structure

โครงสร้างของ AXON Plugin:

```
axon-new/
├── templates/              # 📦 Source of Truth
│   ├── CLAUDE.md          # ⭐ Master Blueprint (v8.0) - Single Source!
│   ├── AXON_MAP.md        # Template สำหรับ Roadmap
│   ├── AXON_STATE.md      # Template สำหรับ State
│   ├── AXON_KNOWLEDGE.md  # Template สำหรับ Knowledge
│   └── config.md          # Template สำหรับ Config
│
├── commands/              # 🎮 Skills (Commands)
│   ├── setup.md          # /axon:setup
│   ├── concept.md        # /axon:concept
│   ├── ignite.md         # /axon:ignite
│   ├── enlighten.md      # /axon:enlighten
│   ├── mcp.md            # /axon:mcp
│   └── upgrade.md        # /axon:upgrade
│
└── README.md             # คู่มือหลัก
```

### 🔑 ไฟล์สำคัญ

| ไฟล์ | บทบาท | การใช้งาน |
|------|-------|----------|
| **templates/CLAUDE.md** | ⭐ **Single Source of Truth** | `/axon:setup` copy ไปโปรเจค<br>`/axon:upgrade` อ่านเป็น source<br>**แก้ที่เดียว → ทุกโปรเจคได้รับ!** |
| `commands/*.md` | Skills definitions | Claude Code โหลดเป็น commands |
| `templates/*.md` | Templates อื่นๆ | Setup ใช้ copy ไปโปรเจค |

> ⚠️ **หมายเหตุ:** ไม่มี root `CLAUDE.md` อีกต่อไป! ใช้ `templates/CLAUDE.md` เป็น single source

---

## 📁 Files Created (เมื่อรัน /axon:setup)

เมื่อรัน `/axon:setup` ในโปรเจค จะสร้างไฟล์:

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

## 🤖 Multi-Agent Support (v1.2)

AXON ใช้ **Boss-Worker Pattern** เพื่อทำงานเร็วขึ้น:

```
       🤖 BOSS (Opus 4.5)
              │
    ┌─────────┼─────────┐
    ▼         ▼         ▼
⚡ Worker  ⚡ Worker  ⚡ Worker
 (Haiku)   (Haiku)   (Haiku)
    │         │         │
    └─────────┴─────────┘
              │
       🤖 BOSS รวมผล
```

### 🔥 IGNITE - Multi-Agent Execution

| งาน | Workers | Strategy |
|-----|---------|----------|
| Search 5 directories | 5 Haiku | MERGE |
| Format 20 files | 4 Haiku | MERGE |
| Compare 3 approaches | 3 Haiku | VOTE |

### 🧘 ENLIGHTEN - Multi-Vector Search

ค้นหลายทางพร้อมกัน:

```
[ค้น Wikipedia] [ค้น News] [ค้น Academic] → รอครั้งเดียว → รวมผล
```

**Status Display (Multi-Agent Mode):**

```
┌─────────────────────────────────────────────────────┐
│ 🤖 Opus 4.5 | 🧘 ENLIGHTEN | 🔍 Elon Musk          │
│ 📊 5 Vectors | ⚡ 4 Workers Active                  │
├─────────────────────────────────────────────────────┤
│ V1 Biography:   [██████] ✅ 12 facts               │
│ V2 Companies:   [████░░] 70% - SpaceX              │
│ V3 News:        [██████] ✅ 8 articles             │
│ V4 Controversy: [███░░░] 50% - SEC                 │
└─────────────────────────────────────────────────────┘
```

---

## 📚 Unified Knowledge (v1.2)

ทั้ง IGNITE และ ENLIGHTEN ใช้ **AXON_KNOWLEDGE.md** ร่วมกัน:

```
╔═══════════════════════════════════════════════════════════════════╗
║  📚 AXON_KNOWLEDGE.md (Shared Knowledge)                          ║
╠═══════════════════════════════════════════════════════════════════╣
║                                                                   ║
║  🔥 IGNITE writes → Technical insights, Code patterns             ║
║  🧘 ENLIGHTEN writes → Research facts, Sources, Scores            ║
║                                                                   ║
║  🔄 BOTH READ: ก่อนทำงาน/ค้นหา ตรวจสอบ KNOWLEDGE ก่อน             ║
║                                                                   ║
╚═══════════════════════════════════════════════════════════════════╝
```

### 📊 Credibility Scoring

ทุก fact ต้องมี Credibility Score (0-100%):

| Score | Meaning | Action |
|-------|---------|--------|
| 90-100% | Highly Reliable | ใช้ได้เลย |
| 70-89% | Reliable | ไม่ต้องค้นซ้ำ |
| 50-69% | Moderate | ต้องหาแหล่งเพิ่ม |
| <50% | Low | ต้องค้นใหม่ |

### 🔍 Check Before Search

ก่อนค้น/ทำงาน:
1. อ่าน AXON_KNOWLEDGE.md
2. ดูว่ารู้อะไรแล้ว + score เท่าไหร่
3. ถ้า score >= 70% → ไม่ค้นซ้ำ
4. ถ้า score < 70% → ค้นเพิ่มเพื่อ verify

**ประโยชน์:**
- ไม่ค้นซ้ำเรื่องเดิม
- ไม่ลืมว่ารู้อะไรแล้ว
- เห็น gaps ที่ยังไม่ได้ค้น
- หลัง compact ความรู้ยังอยู่

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
- [x] **v1.2** - Multi-Agent Support (Boss-Worker Pattern)
- [x] **v1.2** - Unified Knowledge Tracking (AXON_KNOWLEDGE.md)
- [x] **v1.3** - MAP-Centric Design
- [x] **v1.3** - Live Enlightenment (ตรัสรู้ระหว่างทำ)
- [x] **v1.3** - Universal Resume (กลับมาทำต่อได้จากทุก mode)
- [x] **v1.4** - Parallel Execution Rule (ทำหลาย tool calls พร้อมกัน)
- [x] **v1.4** - Dual Power Protocol (Claude Knowledge + Web Search)
- [x] **v1.4** - Audit Agent (Background verification)
- [x] **v1.4** - Dynamic Version Detection (ไม่ต้อง hardcode version)
- [ ] **v2.0** - Vector Memory

---

## 📝 License

MIT License - ใช้ได้ฟรี แก้ไขได้ แจกจ่ายได้

---

**Made with 💎 by vongsagon-git**
