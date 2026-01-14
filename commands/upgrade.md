---
description: "Upgrade AXON - อัพเกรดโปรเจคเก่าให้รองรับ AXON version ใหม่"
---

# 🔄 AXON UPGRADE PROTOCOL

## Mission
อัพเกรดโปรเจคที่ใช้ AXON version เก่า ให้รองรับ features ใหม่ โดย **ไม่ทำลายข้อมูลเดิม**

---

## 🚨 DYNAMIC VERSION DETECTION

```
╔═══════════════════════════════════════════════════════════════════╗
║  📦 LATEST VERSION = อ่านจาก SOURCE CLAUDE.md!                    ║
╠═══════════════════════════════════════════════════════════════════╣
║                                                                   ║
║  🔍 STEP 1: อ่าน CLAUDE.md จาก axon-new repository               ║
║     → หา "Master Blueprint vX.X" ใน title                        ║
║     → นั่นคือ LATEST VERSION                                      ║
║                                                                   ║
║  🔍 STEP 2: อ่าน user's CLAUDE.md                                 ║
║     → หา "Master Blueprint vX.X" ใน title                        ║
║     → นั่นคือ CURRENT VERSION                                     ║
║                                                                   ║
║  🔍 STEP 3: เปรียบเทียบ                                           ║
║     → CURRENT < LATEST → ต้อง upgrade                            ║
║     → CURRENT = LATEST → ไม่ต้องทำอะไร                            ║
║                                                                   ║
║  ⚠️ ไม่มี HARDCODE VERSION ในไฟล์นี้!                             ║
║     → ทุกครั้งที่รัน จะอ่านจาก source ใหม่                        ║
║                                                                   ║
╚═══════════════════════════════════════════════════════════════════╝
```

---

## 🖥️ STATUS DISPLAY

```
┌──────────────────────────────────────────────────────────┐
│ 🤖 Opus 4.5 | 🔄 UPGRADE                                 │
│ 📊 Current: [detected] | Latest: [from source]          │
└──────────────────────────────────────────────────────────┘
```

---

## 🔄 UPGRADE PROCESS

```
╔═══════════════════════════════════════════════════════════════════════╗
║  🔄 DYNAMIC UPGRADE PROTOCOL                                         ║
╠═══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  Step 1: DETECT LATEST VERSION                                       ║
║     → อ่าน CLAUDE.md จาก axon-new repository                        ║
║     → หา "Master Blueprint vX.X" → นั่นคือ latest                    ║
║     → หา features ใน source CLAUDE.md                                ║
║                                                                       ║
║  Step 2: DETECT CURRENT VERSION                                      ║
║     → อ่าน user's CLAUDE.md                                          ║
║     → หา "Master Blueprint vX.X"                                     ║
║     → ถ้าหาไม่เจอ → detect จาก features                              ║
║                                                                       ║
║  Step 3: COMPARE                                                     ║
║     → IF current == latest → "คุณใช้ version ล่าสุดแล้ว!"           ║
║     → IF current < latest → proceed to upgrade                      ║
║                                                                       ║
║  Step 4: BACKUP (if upgrading)                                       ║
║     → สร้าง backup ไฟล์ที่จะแก้ไข                                    ║
║     → เก็บไว้ที่ .axon/backup/                                       ║
║                                                                       ║
║  Step 5: COPY FROM SOURCE                                            ║
║     → Copy CLAUDE.md จาก axon-new/templates/                        ║
║     → รักษา user customizations                                      ║
║                                                                       ║
║  Step 6: VERIFY                                                      ║
║     → ตรวจสอบว่าไฟล์ถูกต้อง                                          ║
║     → แสดง features ใหม่ที่ได้                                       ║
║                                                                       ║
╚═══════════════════════════════════════════════════════════════════════╝
```

---

## 📋 VERSION DETECTION RULES

```
╔═══════════════════════════════════════════════════════════════════════╗
║  📋 FEATURE-BASED VERSION DETECTION                                   ║
╠═══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  ถ้าหา "Master Blueprint vX.X" ไม่เจอ → ดูจาก features:              ║
║                                                                       ║
║  🔍 มี "AUDIT AGENT PROTOCOL"?                                       ║
║     → Yes = v1.4+                                                    ║
║                                                                       ║
║  🔍 มี "DUAL POWER PROTOCOL"?                                        ║
║     → Yes = v1.4+                                                    ║
║                                                                       ║
║  🔍 มี "Live Enlightenment" / "Universal Resume"?                    ║
║     → Yes = v1.3+                                                    ║
║                                                                       ║
║  🔍 มี "MAP-Centric"?                                                ║
║     → Yes = v1.3+                                                    ║
║                                                                       ║
║  🔍 มี "T tasks + E tasks"?                                          ║
║     → Yes = v1.2+                                                    ║
║                                                                       ║
║  🔍 มี "ENLIGHTEN section"?                                          ║
║     → Yes = v1.1+                                                    ║
║                                                                       ║
║  🔍 มีแค่ Basic Commands?                                            ║
║     → v1.0                                                           ║
║                                                                       ║
╚═══════════════════════════════════════════════════════════════════════╝
```

### 📊 VERSION MATRIX (Reference Only)

| Feature | v1.0 | v1.1 | v1.2 | v1.3 | v1.4 |
|---------|------|------|------|------|------|
| 4 Basic Commands | ✅ | ✅ | ✅ | ✅ | ✅ |
| Status Display | ❌ | ✅ | ✅ | ✅ | ✅ |
| Token Management | ❌ | ✅ | ✅ | ✅ | ✅ |
| Concept Modes | ❌ | ✅ | ✅ | ✅ | ✅ |
| Enlighten Mode | ❌ | ✅ | ✅ | ✅ | ✅ |
| Upgrade Command | ❌ | ✅ | ✅ | ✅ | ✅ |
| Multi-Agent (T+E) | ❌ | ❌ | ✅ | ✅ | ✅ |
| Unified Knowledge | ❌ | ❌ | ✅ | ✅ | ✅ |
| MAP-Centric | ❌ | ❌ | ❌ | ✅ | ✅ |
| Live Enlightenment | ❌ | ❌ | ❌ | ✅ | ✅ |
| Universal Resume | ❌ | ❌ | ❌ | ✅ | ✅ |
| **PARALLEL EXECUTION** | ❌ | ❌ | ❌ | ❌ | ✅ |
| **DUAL POWER PROTOCOL** | ❌ | ❌ | ❌ | ❌ | ✅ |
| **AUDIT AGENT** | ❌ | ❌ | ❌ | ❌ | ✅ |
| **A tasks (Audit)** | ❌ | ❌ | ❌ | ❌ | ✅ |

---

## 📁 SOURCE FILES

```
╔═══════════════════════════════════════════════════════════════════════╗
║  📁 SOURCE = axon-new repository                                      ║
╠═══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  Latest CLAUDE.md:                                                    ║
║     → axon-new/templates/CLAUDE.md                                   ║
║                                                                       ║
║  Feature Reference:                                                   ║
║     → axon-new/CLAUDE.md (root)                                      ║
║                                                                       ║
║  Commands:                                                            ║
║     → axon-new/commands/*.md                                         ║
║                                                                       ║
║  ⚠️ เวลา upgrade ต้องอ่านจาก source ไม่ใช่ hardcode!                  ║
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
║  Upgrade: [old_version] → [new_version]                              ║
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
║  1. COPY FROM SOURCE                                                  ║
║     → Copy templates/CLAUDE.md จาก axon-new                         ║
║     → นี่คือ latest version                                          ║
║                                                                       ║
║  2. PRESERVE USER CONTENT                                             ║
║     → หา sections ที่ user เพิ่มเอง                                   ║
║     → Append กลับไปท้ายไฟล์ใหม่                                       ║
║                                                                       ║
║  3. UPDATE CONFIG                                                     ║
║     → อัพเดท .axon/config.md                                         ║
║     → version = [detected from source]                               ║
║     → last_upgrade = [timestamp]                                     ║
║                                                                       ║
║  ❌ NEVER DELETE:                                                      ║
║     → User's custom code/rules                                       ║
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
□ อ่าน version จาก source (axon-new/CLAUDE.md)
□ อ่าน version จาก user's CLAUDE.md
□ เปรียบเทียบ → ต้อง upgrade หรือเปล่า?
□ สร้าง backup

## During Upgrade
□ Copy templates/CLAUDE.md จาก source
□ รักษา user customizations
□ อัพเดท .axon/config.md

## After Upgrade
□ ตรวจสอบไฟล์ที่แก้ไข
□ แสดง features ใหม่ที่ได้
□ บันทึก upgrade.log
```

---

## 📊 UPGRADE REPORT FORMAT

```markdown
## 🔄 Upgrade Complete

**From:** [detected from user's CLAUDE.md]
**To:** [detected from source CLAUDE.md]
**Date:** [timestamp]

### Files Modified:
- ✅ CLAUDE.md - อัพเดทจาก source
- ✅ .axon/config.md - อัพเดท version field

### 🆕 New Features:
[List features ที่มีใน source แต่ไม่มีใน user's version]

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
║  IF source ไม่เจอ:                                                   ║
║     → แจ้ง error "ไม่พบ axon-new repository"                         ║
║     → หยุด upgrade                                                   ║
║                                                                       ║
║  IF user's CLAUDE.md ไม่เจอ:                                         ║
║     → ถือว่าเป็น fresh install                                       ║
║     → Copy จาก source โดยตรง                                         ║
║                                                                       ║
║  IF backup failed:                                                   ║
║     → แจ้ง warning แต่ไม่หยุด                                        ║
║     → ถาม user ว่าจะดำเนินการต่อไหม                                  ║
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
   ┌──────────────────────────────────────────────────────────┐
   │ 🤖 Opus 4.5 | 🔄 UPGRADE | Checking...                   │
   └──────────────────────────────────────────────────────────┘

2. อ่าน LATEST VERSION จาก source
   → Read axon-new/CLAUDE.md หรือ axon-new/templates/CLAUDE.md
   → หา "Master Blueprint vX.X"
   → หา features (AUDIT AGENT, DUAL POWER, etc.)

3. อ่าน CURRENT VERSION จาก user
   → Read user's CLAUDE.md
   → หา "Master Blueprint vX.X"
   → ถ้าหาไม่เจอ → detect จาก features

4. เปรียบเทียบ
   → IF current == latest:
        แสดง "✅ คุณใช้ version ล่าสุดแล้ว!"
        แสดง features ที่มี
        จบ
   → IF current < latest:
        แสดง features ใหม่ที่จะได้
        proceed to upgrade

5. Backup (if upgrading)
   → สร้าง .axon/backup/[timestamp]/
   → copy ไฟล์ที่จะแก้

6. Upgrade
   → Copy CLAUDE.md จาก source
   → รักษา user customizations
   → อัพเดท .axon/config.md

7. Verify + Report
   → ตรวจสอบไฟล์
   → แสดง upgrade report
   → "✅ Upgrade เสร็จสมบูรณ์!"
```

---

## 📌 IMPORTANT NOTES

```
╔═══════════════════════════════════════════════════════════════════════╗
║  ⚠️ CRITICAL: DYNAMIC VERSION SYSTEM                                  ║
╠═══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  ❌ ห้าม HARDCODE version ในไฟล์นี้                                   ║
║                                                                       ║
║  ✅ ต้อง READ version จาก:                                            ║
║     • Source: axon-new/CLAUDE.md (latest)                            ║
║     • User: user's CLAUDE.md (current)                               ║
║                                                                       ║
║  🔄 เมื่อมี version ใหม่:                                             ║
║     • อัพเดท CLAUDE.md ใน axon-new                                   ║
║     • อัพเดท templates/CLAUDE.md ใน axon-new                         ║
║     • ไม่ต้องแก้ไฟล์ upgrade.md นี้!                                  ║
║                                                                       ║
║  📋 VERSION DETECTION PRIORITY:                                       ║
║     1. หา "Master Blueprint vX.X" ใน title                          ║
║     2. ถ้าหาไม่เจอ → detect จาก features                             ║
║     3. ถ้าหาไม่เจอเลย → ถือว่า v1.0                                  ║
║                                                                       ║
╚═══════════════════════════════════════════════════════════════════════╝
```

---

## 🔍 FEATURE DETECTION CODE (Pseudo)

```
function detectVersion(claudeContent):
    # 1. Try to find version in title
    if "Master Blueprint v8.0" in title:
        # Check for v1.4 features
        if "AUDIT AGENT PROTOCOL" in content:
            return "v1.4"
        else:
            return "v1.3"

    if "Master Blueprint v7.0" in title:
        return "v1.2"

    # 2. Feature-based detection
    if "AUDIT AGENT PROTOCOL" in content:
        return "v1.4"

    if "DUAL POWER PROTOCOL" in content:
        return "v1.4"

    if "PARALLEL EXECUTION RULE" in content:
        return "v1.4"

    if "Live Enlightenment" in content:
        return "v1.3"

    if "MAP-Centric" in content:
        return "v1.3"

    if "T tasks + E tasks" in content:
        return "v1.2"

    if "ENLIGHTEN" in content:
        return "v1.1"

    return "v1.0"
```
