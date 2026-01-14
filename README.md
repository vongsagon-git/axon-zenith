# ⚡ AXON Zenith

> **Autonomous Execution System for Claude Code**
> *"ช้าได้ แต่ห้ามห่วย"* (Lateness is acceptable, Mediocrity is not)

## 🚀 What is AXON?

AXON Zenith เป็น Plugin สำหรับ Claude Code ที่เปลี่ยน Claude ให้เป็น **Autonomous Agent** ที่:

- 🔄 **ทำงานไม่หยุด** จนกว่างานจะเสร็จ (Infinite Loop)
- 💎 **Zenith Quality** - ทุกงานต้องผ่านการตรวจสอบคุณภาพ 3 ด้าน
- 🧠 **Self-Learning** - เก็บความรู้ไว้ใน Knowledge Vault
- ⚡ **Parallel Execution** - ทำหลายงานพร้อมกันเมื่อทำได้

## 📦 Installation

### Local Install
```bash
# Clone plugin
git clone https://github.com/pinkkydev/axon-zenith.git

# In Claude Code
/plugin install ./axon-zenith
```

### npm Install (Coming Soon)
```bash
/plugin install axon-zenith
```

## 🎯 Commands

| Command | Description |
|---------|-------------|
| `/axon:setup` | Setup AXON system files ในโปรเจค |
| `/axon:concept [task]` | วางแผนงานแบบ Architecture First |
| `/axon:ignite` | เริ่ม Zenith Loop - ทำงานไม่หยุด |
| `/axon:mcp [action]` | จัดการ MCP Servers |

## 🔥 Quick Start

```bash
# 1. Setup AXON ในโปรเจค
/axon:setup

# 2. วางแผนงาน
/axon:concept สร้าง todo app ด้วย React

# 3. เริ่มทำงาน (Loop ไม่หยุด!)
/axon:ignite
```

## 📁 Files Created

เมื่อรัน `/axon:setup` จะสร้างไฟล์:

| File | Purpose |
|------|---------|
| `AXON_STATE.md` | Current state + Resume point |
| `AXON_MAP.md` | Task roadmap |
| `AXON_KNOWLEDGE.md` | Knowledge vault |
| `.axon/mcp.md` | MCP configuration |

## 💎 The Zenith Protocol

ทุกงานต้องผ่าน **3 Quality Gates**:

1. **Deepest Dive** - ขุดลึกถึง Root Cause
2. **Comparative Selection** - หา 3 Options เปรียบเทียบ
3. **Structured Output** - จัดเรียงสวยงาม อ่านง่าย

## 🔄 The Ignite Loop

```
STATE SYNC → TASK SELECT → MITOSIS → EXECUTE
     ↑                                   ↓
     └── INFINITE ← AUTO-DISCOVERY ← CHECKPOINT
```

**หยุดได้เฉพาะ:**
- ติด usage limit
- User พิมพ์ "หยุด"

## 🔌 MCP Integration

AXON รองรับ MCP servers เพื่อเพิ่มความสามารถ:

```bash
# ดู MCP ที่ติดตั้ง
/axon:mcp list

# ดูคำแนะนำ
/axon:mcp recommend

# เพิ่ม MCP
/axon:mcp add puppeteer
```

## 📊 Comparison with Similar Tools

| Feature | AXON Zenith | nat-agents-core | OpenAGI |
|---------|-------------|-----------------|---------|
| Infinite Loop | ✅ | ✅ | ❌ |
| Quality Gates | ✅ 3 Gates | ✅ | ❌ |
| Knowledge Vault | ✅ Markdown | ✅ ChromaDB | ✅ ChromaDB |
| MCP Integration | ✅ | ✅ | ❌ |
| Thai Native | ✅ | ❌ | ❌ |

## 🗺️ Roadmap

- [x] **v1.0** - Core Plugin (Commands)
- [ ] **v1.1** - MCP Tools Integration
- [ ] **v2.0** - Multi-Agent Support
- [ ] **v2.1** - Vector Memory (ChromaDB)

## 📝 License

MIT License - Feel free to use and modify!

---

**Made with 💎 by pinkkydev**
