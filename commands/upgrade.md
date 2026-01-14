---
description: "Upgrade AXON - อัพเกรดโปรเจคเก่าให้รองรับ AXON version ใหม่"
---

# 🔄 AXON UPGRADE PROTOCOL

## Mission
อัพเกรดโปรเจคที่ใช้ AXON version เก่า ให้รองรับ features ใหม่ โดย **ไม่ทำลายข้อมูลเดิม**

---

## 🖥️ STATUS DISPLAY

```
┌─────────────────────────────────────────┐
│ 🤖 Opus 4.5 | 🔄 UPGRADE | v1.0 → v1.1 │
│ 📊 Checking files...                    │
└─────────────────────────────────────────┘
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
║     → หา "AXON Zenith" หรือ "Master Blueprint"                       ║
║     → หา version number (ถ้ามี)                                       ║
║                                                                       ║
║  2. .axon/config.md                                                   ║
║     → หา version field                                                ║
║                                                                       ║
║  3. FEATURES CHECK                                                    ║
║     → มี STATUS DISPLAY ไหม? (v1.1+)                                  ║
║     → มี TOKEN MANAGEMENT ไหม? (v1.1+)                                ║
║     → มี CONCEPT MODES ไหม? (v1.1+)                                   ║
║     → มี ENLIGHTEN ไหม? (v1.1+)                                       ║
║                                                                       ║
║  📊 VERSION MATRIX:                                                   ║
║     | Feature | v1.0 | v1.1 |                                        ║
║     |---------|------|------|                                        ║
║     | 4 Commands | ✅ | ✅ |                                          ║
║     | Status Display | ❌ | ✅ |                                      ║
║     | Token Management | ❌ | ✅ |                                    ║
║     | Concept Modes | ❌ | ✅ |                                       ║
║     | Enlighten | ❌ | ✅ |                                           ║
║     | Upgrade Command | ❌ | ✅ |                                     ║
║                                                                       ║
╚═══════════════════════════════════════════════════════════════════════╝
```

---

## 📁 FILES TO UPDATE

### CLAUDE.md Updates

```
╔═══════════════════════════════════════════════════════════════════════╗
║  📄 CLAUDE.md UPDATES                                                 ║
╠═══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  v1.0 → v1.1:                                                         ║
║                                                                       ║
║  เพิ่ม:                                                               ║
║  • STATUS DISPLAY section                                             ║
║  • TOKEN MANAGEMENT section                                           ║
║  • CONCEPT MODES (NEW, ADD, MODIFY, EXPAND, LINK)                    ║
║  • ENLIGHTEN command reference                                        ║
║  • UPGRADE command reference                                          ║
║                                                                       ║
║  แก้ไข:                                                               ║
║  • Version number                                                     ║
║  • Commands table (เพิ่ม enlighten, upgrade)                         ║
║                                                                       ║
║  ไม่แตะ:                                                              ║
║  • User's custom rules                                               ║
║  • Project-specific settings                                         ║
║  • Knowledge Base config                                             ║
║                                                                       ║
╚═══════════════════════════════════════════════════════════════════════╝
```

### .axon/config.md Updates

```
╔═══════════════════════════════════════════════════════════════════════╗
║  📄 .axon/config.md UPDATES                                           ║
╠═══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  เพิ่ม:                                                               ║
║  • version: "1.1"                                                     ║
║  • last_upgrade: [timestamp]                                          ║
║  • features_enabled: [list]                                           ║
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
║  Upgrade: v1.0 → v1.1                                                ║
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

**From:** v1.0
**To:** v1.1
**Date:** [timestamp]

### Files Modified:
- ✅ CLAUDE.md - เพิ่ม STATUS DISPLAY, TOKEN MANAGEMENT
- ✅ .axon/config.md - เพิ่ม version field

### New Features Available:
- 🖥️ Status Display - แสดง Model/Mode/Task
- 🔋 Token Management - ประหยัด context
- 🔗 Concept Modes - NEW, ADD, MODIFY, EXPAND, LINK
- 🧘 Enlighten - ขุดข้อมูลไม่หยุด
- 🔄 Upgrade - อัพเกรดโปรเจคเก่า

### Backup Location:
`.axon/backup/[timestamp]/`

### What's Preserved:
- ✅ Your custom rules
- ✅ Knowledge Base data
- ✅ Task history
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
   ┌─────────────────────────────────────────┐
   │ 🤖 Opus 4.5 | 🔄 UPGRADE | Checking... │
   └─────────────────────────────────────────┘

2. ตรวจสอบ version
   → อ่าน CLAUDE.md
   → หา version ปัจจุบัน
   → เปรียบเทียบกับ latest

3. แจ้ง user
   "พบว่าใช้ AXON v1.0 จะอัพเกรดเป็น v1.1"
   "จะแก้ไข: CLAUDE.md, .axon/config.md"

4. Backup
   → สร้าง .axon/backup/[timestamp]/
   → copy ไฟล์ที่จะแก้

5. Upgrade
   → อัพเดท CLAUDE.md
   → อัพเดท .axon/config.md

6. Verify
   → ตรวจสอบไฟล์
   → แสดง report

7. Done
   "✅ Upgrade เสร็จสมบูรณ์!"
```
