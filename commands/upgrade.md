---
description: "Upgrade AXON - อัพเกรดโปรเจคเก่าให้รองรับ AXON version ใหม่"
---

# 🔄 AXON UPGRADE PROTOCOL

## Mission
อัพเกรดโปรเจคที่ใช้ AXON version เก่า ให้รองรับ features ใหม่ โดย **ไม่ทำลายข้อมูลเดิม**

---

## 🚨 CURRENT VERSION

```
╔═══════════════════════════════════════════════════════════════════╗
║  📦 AXON ZENITH LATEST: v1.3 (Master Blueprint v8.0)             ║
╠═══════════════════════════════════════════════════════════════════╣
║  Key Features:                                                    ║
║  • MAP-Centric Architecture                                       ║
║  • Live Enlightenment (ตรัสรู้ระหว่างทำ)                          ║
║  • Universal Resume (กลับมาทำต่อจากทุก mode)                      ║
║  • Multi-Agent Support (T tasks + E tasks)                        ║
╚═══════════════════════════════════════════════════════════════════╝
```

---

## 🖥️ STATUS DISPLAY

```
┌──────────────────────────────────────────────┐
│ 🤖 Opus 4.5 | 🔄 UPGRADE | [old] → v1.3     │
│ 📊 Checking files...                         │
└──────────────────────────────────────────────┘
```

---

## 🔄 UPGRADE PROCESS

```
╔═══════════════════════════════════════════════════════════════════════╗
║  🔄 UPGRADE PROTOCOL                                                  ║
╠═══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  Step 1: VERSION CHECK                                                ║
║     → อ่าน CLAUDE.md หา version ปัจจุบัน                              ║
║     → เปรียบเทียบกับ version ล่าสุด                                   ║
║                                                                       ║
║  Step 2: BACKUP                                                       ║
║     → สร้าง backup ไฟล์ที่จะแก้ไข                                     ║
║     → เก็บไว้ที่ .axon/backup/                                        ║
║                                                                       ║
║  Step 3: MERGE CHANGES                                                ║
║     → รวม config เดิมกับ features ใหม่                                ║
║     → ไม่ลบ customization ของ user                                    ║
║                                                                       ║
║  Step 4: UPDATE FILES                                                 ║
║     → อัพเดท CLAUDE.md                                                ║
║     → อัพเดท .axon/config.md                                          ║
║     → เพิ่มไฟล์ใหม่ (ถ้ามี)                                           ║
║                                                                       ║
║  Step 5: VERIFY                                                       ║
║     → ตรวจสอบว่าไฟล์ถูกต้อง                                           ║
║     → ทดสอบ commands                                                  ║
║                                                                       ║
╚═══════════════════════════════════════════════════════════════════════╝
```

---

## 📋 VERSION DETECTION

```
╔═══════════════════════════════════════════════════════════════════════╗
║  📋 VERSION DETECTION                                                 ║
╠═══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  ตรวจสอบ version จาก:                                                 ║
║                                                                       ║
║  1. CLAUDE.md                                                         ║
║     → หา "AXON Zenith" หรือ "Master Blueprint vX.X"                  ║
║     → หา version number จาก title                                     ║
║                                                                       ║
║  2. .axon/config.md                                                   ║
║     → หา version field                                                ║
║                                                                       ║
║  3. FEATURES CHECK (ถ้าหา version ไม่เจอ)                             ║
║     → ตรวจ features → ประมาณ version                                  ║
║                                                                       ║
╚═══════════════════════════════════════════════════════════════════════╝
```

### 📊 VERSION MATRIX (ครบทุก version)

| Feature | v1.0 | v1.1 | v1.2 | v1.3 |
|---------|------|------|------|------|
| 4 Basic Commands | ✅ | ✅ | ✅ | ✅ |
| Status Display | ❌ | ✅ | ✅ | ✅ |
| Token Management | ❌ | ✅ | ✅ | ✅ |
| Concept Modes | ❌ | ✅ | ✅ | ✅ |
| Enlighten Mode | ❌ | ✅ | ✅ | ✅ |
| Upgrade Command | ❌ | ✅ | ✅ | ✅ |
| Multi-Agent (T+E) | ❌ | ❌ | ✅ | ✅ |
| Unified Knowledge | ❌ | ❌ | ✅ | ✅ |
| **MAP-Centric** | ❌ | ❌ | ❌ | ✅ |
| **Live Enlightenment** | ❌ | ❌ | ❌ | ✅ |
| **Universal Resume** | ❌ | ❌ | ❌ | ✅ |

### 🔍 QUICK VERSION CHECK

```
╔═══════════════════════════════════════════════════════════════════════╗
║  🔍 วิธีดู version เร็ว:                                              ║
╠═══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  1. ดูจาก CLAUDE.md title:                                           ║
║     "Master Blueprint v7.0" → AXON v1.2                              ║
║     "Master Blueprint v8.0" → AXON v1.3                              ║
║                                                                       ║
║  2. ดูจาก features:                                                   ║
║     มี ENLIGHTEN section? → v1.1+                                    ║
║     มี "T tasks + E tasks"? → v1.2+                                  ║
║     มี "Live Enlightenment" / "Universal Resume"? → v1.3             ║
║                                                                       ║
║  3. ดูจาก MAP format:                                                 ║
║     มี T001, T002 เท่านั้น? → v1.1                                   ║
║     มี T001 + E001? → v1.2+                                          ║
║     มี MAP-Centric flow? → v1.3                                      ║
║                                                                       ║
╚═══════════════════════════════════════════════════════════════════════╝
```

---

## 📁 FILES TO UPDATE

### CLAUDE.md Updates

```
╔═══════════════════════════════════════════════════════════════════════╗
║  📄 CLAUDE.md UPDATES (ตาม version ที่อัพเกรด)                        ║
╠═══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  → v1.1 (จาก v1.0):                                                   ║
║    • เพิ่ม STATUS DISPLAY section                                     ║
║    • เพิ่ม TOKEN MANAGEMENT section                                   ║
║    • เพิ่ม CONCEPT MODES                                              ║
║    • เพิ่ม ENLIGHTEN + UPGRADE commands                               ║
║                                                                       ║
║  → v1.2 (จาก v1.1):                                                   ║
║    • เพิ่ม Multi-Agent Support (T tasks + E tasks)                   ║
║    • เพิ่ม Unified Knowledge Base                                     ║
║    • อัพเดท MAP format รองรับ E tasks                                ║
║                                                                       ║
║  → v1.3 (จาก v1.2):                                                   ║
║    • เพิ่ม MAP-Centric Architecture section                          ║
║    • เพิ่ม Live Enlightenment (ตรัสรู้ระหว่างทำ)                      ║
║    • เพิ่ม Universal Resume protocol                                  ║
║    • เพิ่ม UNIFIED FLOW diagram                                       ║
║    • อัพเดท COMMAND MODE PROTOCOL                                     ║
║                                                                       ║
║  ❌ ไม่แตะ:                                                            ║
║    • User's custom rules                                             ║
║    • Project-specific settings                                       ║
║    • Knowledge Base data                                             ║
║                                                                       ║
╚═══════════════════════════════════════════════════════════════════════╝
```

### .axon/config.md Updates

```
╔═══════════════════════════════════════════════════════════════════════╗
║  📄 .axon/config.md UPDATES                                           ║
╠═══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  อัพเดท:                                                              ║
║  • version: "1.3"  (ล่าสุด)                                           ║
║  • last_upgrade: [timestamp]                                          ║
║  • features_enabled: [list of v1.3 features]                         ║
║                                                                       ║
║  ไม่แตะ:                                                              ║
║  • knowledge_base settings                                           ║
║  • mcp_servers settings                                              ║
║  • user preferences                                                  ║
║                                                                       ║
╚═══════════════════════════════════════════════════════════════════════╝
```

---

## 🔒 BACKUP PROTOCOL

```
╔═══════════════════════════════════════════════════════════════════════╗
║  🔒 BACKUP BEFORE UPGRADE                                             ║
╠═══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  ก่อนแก้ไขไฟล์ใดๆ ต้อง backup ก่อน:                                   ║
║                                                                       ║
║  📁 .axon/backup/                                                     ║
║  ├── [timestamp]/                                                     ║
║  │   ├── CLAUDE.md.bak                                               ║
║  │   ├── config.md.bak                                               ║
║  │   └── upgrade.log                                                 ║
║                                                                       ║
║  upgrade.log format:                                                  ║
║  ```                                                                  ║
║  Upgrade: [old_version] → v1.3                                       ║
║  Date: [timestamp]                                                   ║
║  Files modified:                                                     ║
║    - CLAUDE.md                                                       ║
║    - .axon/config.md                                                 ║
║  Status: SUCCESS/FAILED                                              ║
║  ```                                                                  ║
║                                                                       ║
╚═══════════════════════════════════════════════════════════════════════╝
```

---

## 🔄 MERGE STRATEGY

```
╔═══════════════════════════════════════════════════════════════════════╗
║  🔄 SMART MERGE (ไม่ทำลายของเดิม)                                     ║
╠═══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  1. APPEND MODE (เพิ่มต่อท้าย)                                        ║
║     → ใช้กับ sections ใหม่ที่ไม่มีในไฟล์เดิม                          ║
║     → เพิ่มต่อท้ายโดยไม่แตะส่วนเดิม                                   ║
║                                                                       ║
║  2. UPDATE MODE (แก้ไขเฉพาะจุด)                                       ║
║     → ใช้กับ version number, commands table                          ║
║     → แก้เฉพาะส่วนที่ต้องแก้                                         ║
║                                                                       ║
║  3. PRESERVE MODE (รักษาของเดิม)                                      ║
║     → User customizations                                            ║
║     → Project-specific rules                                         ║
║     → Knowledge Base data                                            ║
║                                                                       ║
║  ❌ NEVER DELETE:                                                      ║
║     → User's custom code                                             ║
║     → AXON_KNOWLEDGE.md content                                      ║
║     → AXON_MAP.md tasks                                              ║
║     → AXON_STATE.md data                                             ║
║                                                                       ║
╚═══════════════════════════════════════════════════════════════════════╝
```

---

## 📋 UPGRADE CHECKLIST

```markdown
## Before Upgrade
□ อ่าน version ปัจจุบัน
□ สร้าง backup
□ แจ้ง user ว่าจะแก้ไขอะไร

## During Upgrade
□ อัพเดท CLAUDE.md (เพิ่ม sections ใหม่)
□ อัพเดท .axon/config.md (เพิ่ม version)
□ เพิ่มไฟล์ใหม่ (ถ้ามี)

## After Upgrade
□ ตรวจสอบไฟล์ที่แก้ไข
□ แจ้ง user ว่าแก้ไขอะไรบ้าง
□ บันทึก upgrade.log
```

---

## 📊 UPGRADE REPORT

```markdown
## 🔄 Upgrade Complete

**From:** [detected_version]
**To:** v1.3
**Date:** [timestamp]

### Files Modified:
- ✅ CLAUDE.md - อัพเดทเป็น Master Blueprint v8.0
- ✅ .axon/config.md - อัพเดท version field

### 🆕 New Features in v1.3:

| Feature | Description |
|---------|-------------|
| 🗺️ **MAP-Centric** | MAP เป็นศูนย์กลางของทุกอย่าง |
| 🧘 **Live Enlightenment** | ตรัสรู้ระหว่างทำ → เพิ่ม tasks ได้ทันที |
| 🔄 **Universal Resume** | กลับมาทำต่อจากทุก mode ด้วย /axon:ignite |
| 📋 **Multi-Agent** | รองรับ T tasks (concept) + E tasks (enlighten) |

### 🚀 Quick Start After Upgrade:

```
# มีงานชัดเจน?
/axon:concept [task]

# ไม่รู้จะทำอะไร?
/axon:enlighten [topic]

# กลับมาทำต่อ?
/axon:ignite
```

### Backup Location:
`.axon/backup/[timestamp]/`

### What's Preserved:
- ✅ Your custom rules
- ✅ Knowledge Base data (AXON_KNOWLEDGE.md)
- ✅ Task history (AXON_MAP.md)
- ✅ Project settings
```

---

## 🚨 ERROR HANDLING

```
╔═══════════════════════════════════════════════════════════════════════╗
║  🚨 ERROR HANDLING                                                    ║
╠═══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  IF ไฟล์หาย:                                                          ║
║     → สร้างใหม่ด้วย default values                                    ║
║     → แจ้ง user                                                       ║
║                                                                       ║
║  IF format ผิด:                                                       ║
║     → พยายาม parse เท่าที่ได้                                         ║
║     → backup ไฟล์เดิม                                                 ║
║     → สร้างใหม่                                                       ║
║                                                                       ║
║  IF merge conflict:                                                   ║
║     → ถาม user ว่าจะเลือกอันไหน                                       ║
║     → หรือ keep both                                                 ║
║                                                                       ║
║  IF upgrade failed:                                                   ║
║     → Rollback จาก backup                                            ║
║     → แจ้ง user                                                       ║
║     → ไม่ทิ้งงาน                                                      ║
║                                                                       ║
╚═══════════════════════════════════════════════════════════════════════╝
```

---

## 🔄 EXECUTION FLOW

```
1. แสดง Status
   ┌──────────────────────────────────────────────┐
   │ 🤖 Opus 4.5 | 🔄 UPGRADE | Checking...       │
   └──────────────────────────────────────────────┘

2. ตรวจสอบ version
   → อ่าน CLAUDE.md (หา Master Blueprint vX.X)
   → อ่าน .axon/config.md (หา version field)
   → ถ้าหาไม่เจอ → ตรวจ features → ประมาณ version
   → เปรียบเทียบกับ v1.3 (ล่าสุด)

3. แจ้ง user
   "พบว่าใช้ AXON [detected_version] จะอัพเกรดเป็น v1.3"
   "จะแก้ไข: CLAUDE.md, .axon/config.md"
   [แสดง features ใหม่ที่จะได้]

4. Backup
   → สร้าง .axon/backup/[timestamp]/
   → copy ไฟล์ที่จะแก้

5. Upgrade
   → อัพเดท CLAUDE.md → Master Blueprint v8.0
   → อัพเดท .axon/config.md → version: "1.3"
   → เพิ่ม sections ใหม่ตาม version gap

6. Verify
   → ตรวจสอบไฟล์
   → แสดง report

7. Done
   "✅ Upgrade เสร็จสมบูรณ์!"
   [แสดง Quick Start หลัง upgrade]
```

---

## 📌 IMPORTANT NOTES

```
╔═══════════════════════════════════════════════════════════════════════╗
║  ⚠️ NOTES สำหรับ UPGRADE                                              ║
╠═══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  1. ถ้าเป็น v1.3 อยู่แล้ว:                                            ║
║     → แจ้ง "คุณใช้ version ล่าสุดแล้ว!"                               ║
║     → ไม่ต้องทำอะไร                                                   ║
║                                                                       ║
║  2. ถ้าหา version ไม่เจอเลย:                                          ║
║     → ถือว่าเป็น v1.0                                                 ║
║     → Upgrade เต็ม features                                          ║
║                                                                       ║
║  3. ถ้า CLAUDE.md มี custom content:                                  ║
║     → รักษาไว้ ไม่ลบ                                                   ║
║     → เพิ่ม sections ใหม่ต่อท้าย                                      ║
║                                                                       ║
║  4. Upgrade ข้าม version ได้:                                         ║
║     → v1.0 → v1.3 โดยตรง ✅                                           ║
║     → ไม่ต้องอัพทีละ version                                         ║
║                                                                       ║
╚═══════════════════════════════════════════════════════════════════════╝
```
