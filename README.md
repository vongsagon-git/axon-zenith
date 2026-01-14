# ⚡ AXON Zenith

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

> หลังติดตั้ง พิมพ์ `/axon` จะเห็น commands ทั้ง 4 ตัว

**📖 [คู่มือการใช้งานฉบับเต็ม (ภาษาไทย)](GUIDE.md)**

---

## 🚀 What is AXON?

AXON Zenith เป็น Plugin สำหรับ Claude Code ที่เปลี่ยน Claude ให้เป็น **Autonomous Agent** ที่:

- 🔄 **ทำงานไม่หยุด** จนกว่างานจะเสร็จ (Infinite Loop)
- 💎 **Zenith Quality** - ทุกงานต้องผ่านการตรวจสอบคุณภาพ 3 ด้าน
- 🧠 **Knowledge Base** - รองรับ Text, Vector DB, Cloud AI
- ⚡ **Parallel Execution** - ทำหลายงานพร้อมกันเมื่อทำได้

---

## 🎯 Commands

| Command | Description |
|---------|-------------|
| `/axon:setup` | Setup AXON + เลือก Knowledge Base |
| `/axon:concept [task]` | วางแผนงานแบบ Architecture First |
| `/axon:ignite` | เริ่ม Zenith Loop - ทำงานไม่หยุด |
| `/axon:mcp [action]` | จัดการ MCP Servers |

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

---

## 🧠 Knowledge Base Options

| Type | รายละเอียด | เหมาะสำหรับ |
|------|-----------|------------|
| **Text Files** | Markdown files | โปรเจคเล็ก-กลาง |
| **DigitalOcean Gradient** | OpenSearch + gte-large | Production AI/RAG |
| **MongoDB Atlas** | Vector Search + Voyage AI | เพิ่ม vector ให้ MongoDB |
| **Local Vector** | Qdrant/Chroma | Development, Privacy |

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

## 💎 The Zenith Protocol

ทุกงานต้องผ่าน **3 Quality Gates**:

1. **Deepest Dive** - ขุดลึกถึง Root Cause
2. **Comparative Selection** - หา 3 Options เปรียบเทียบ
3. **Structured Output** - จัดเรียงสวยงาม อ่านง่าย

---

## 🔄 The Ignite Loop

```
┌─────────────────────────────────────────────────┐
│              ZENITH INFINITE LOOP               │
├─────────────────────────────────────────────────┤
│  1. อ่าน MAP หางาน [ ] ที่ยังไม่เสร็จ            │
│  2. ทำงานจนเสร็จ                                │
│  3. Mark [x] และบันทึก Knowledge                │
│  4. สร้างงานใหม่ถ้าจำเป็น                       │
│  5. วนกลับ Step 1                              │
│                                                │
│  ❌ ห้ามหยุด  ❌ ห้ามถาม  ❌ ห้ามรอ              │
└─────────────────────────────────────────────────┘
```

**หยุดได้เฉพาะ:**
- ติด API limit
- User พิมพ์ "หยุด"

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

## 🔄 Update Plugin

```bash
/plugin update axon-zenith
```

---

## 🗺️ Roadmap

- [x] **v1.0** - Core Plugin (4 Commands)
- [x] **v1.0** - Knowledge Base Options
- [x] **v1.0** - MCP Catalog
- [ ] **v1.1** - Auto MCP Installation
- [ ] **v2.0** - Multi-Agent Support

---

## 📖 Documentation

- **[คู่มือการใช้งาน (Thai)](GUIDE.md)** - คู่มือฉบับเต็มภาษาไทย
- **[Issues](https://github.com/vongsagon-git/axon-zenith/issues)** - รายงานปัญหา
- **[Discussions](https://github.com/vongsagon-git/axon-zenith/discussions)** - ถาม-ตอบ

---

## 📝 License

MIT License - ใช้ได้ฟรี แก้ไขได้ แจกจ่ายได้

---

**Made with 💎 by vongsagon-git**
