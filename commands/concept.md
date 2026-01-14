---
description: "Architecture First planning - วางแผนงานแบบไม่ถูไถ"
---

# AXON CONCEPT PROTOCOL

## Mission
วางแผนงานตาม Zenith Philosophy - แผนต้องมีโครงสร้างชัดเจน ไม่ "Muddle through"

## Input
Task/Prompt: $ARGUMENTS

---

## 🔗 CONCEPT MODES

```
╔═══════════════════════════════════════════════════════════════════════╗
║  📐 CONCEPT สามารถใช้ได้หลายรูปแบบ:                                    ║
╠═══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  1️⃣ NEW CONCEPT (สร้างใหม่):                                          ║
║     /axon:concept สร้าง Todo App                                     ║
║     → สร้าง roadmap ใหม่จากศูนย์                                      ║
║                                                                       ║
║  2️⃣ ADD CONCEPT (เพิ่มต่อ):                                           ║
║     /axon:concept เพิ่ม: ระบบ User Authentication                    ║
║     /axon:concept +: ระบบ Payment                                    ║
║     → เพิ่มเข้า roadmap เดิม + วิเคราะห์ความสัมพันธ์                  ║
║                                                                       ║
║  3️⃣ MODIFY CONCEPT (แก้ไข):                                           ║
║     /axon:concept แก้: [TASK_ID] ให้รองรับ mobile ด้วย               ║
║     /axon:concept ปรับ: เปลี่ยนจาก React เป็น Vue                    ║
║     → แก้ไข roadmap ที่มีอยู่                                         ║
║                                                                       ║
║  4️⃣ EXPAND CONCEPT (ขยาย):                                            ║
║     /axon:concept ขยาย: [TASK_ID] ให้ละเอียดกว่านี้                   ║
║     /axon:concept ลึก: ระบบ Security ทั้งหมด                         ║
║     → แตก task เดิมเป็น sub-tasks ที่ละเอียดขึ้น                      ║
║                                                                       ║
║  5️⃣ LINK CONCEPTS (เชื่อมต่อ):                                        ║
║     /axon:concept รวม                                                ║
║     /axon:concept master                                             ║
║     → สร้าง Master Roadmap ที่เชื่อมทุก concept                      ║
║                                                                       ║
╚═══════════════════════════════════════════════════════════════════════╝
```

---

## 🎯 DETECT MODE (ตรวจสอบว่า user ต้องการทำอะไร)

```
PARSE $ARGUMENTS:

IF contains "เพิ่ม:" or "+:" or "add:"
  → MODE = ADD_CONCEPT
  → เพิ่ม concept ใหม่เข้า roadmap เดิม

ELSE IF contains "แก้:" or "ปรับ:" or "modify:"
  → MODE = MODIFY_CONCEPT
  → แก้ไข task/concept ที่มีอยู่

ELSE IF contains "ขยาย:" or "ลึก:" or "expand:"
  → MODE = EXPAND_CONCEPT
  → แตก task เป็น sub-tasks

ELSE IF contains "รวม" or "master" or "link"
  → MODE = LINK_CONCEPTS
  → สร้าง Master Roadmap

ELSE
  → MODE = NEW_CONCEPT
  → สร้าง roadmap ใหม่ (default)
```

---

## Execution Steps

### 1. STATE SYNC
อ่าน AXON_STATE.md และ AXON_KNOWLEDGE.md เพื่อโหลดบริบท
**อ่าน AXON_MAP.md เพื่อดู concepts ที่มีอยู่แล้ว**

### 2. DEEP ANALYSIS (Zenith Protocol)

#### 2.1 Deepest Dive
- วิเคราะห์ Root Cause / First Principles
- ห้ามตอบผิวเผิน ต้องขุดให้ลึกที่สุด

#### 2.2 Comparative Selection
- หาอย่างน้อย 3 Options/Approaches
- เปรียบเทียบข้อดี/ข้อเสียของแต่ละวิธี
- เลือก **The Best** พร้อมเหตุผล

#### 2.3 Architecture First
- วางโครงสร้างก่อนลงมือทำ
- แบ่งงานเป็น Tasks ย่อยที่ตรวจสอบคุณภาพได้

### 3. MCP REQUIREMENT ANALYSIS

**อ่านไฟล์:** `.axon/mcp.md` เพื่อดู MCP ที่โปรเจคนี้ใช้

**วิเคราะห์ว่างานนี้ต้องใช้ MCP อะไรบ้าง:**

| ลักษณะงาน | MCP ที่ต้องใช้ | Package |
|----------|--------------|---------|
| ดึงข้อมูลจากเว็บ/API | `fetch` | `@anthropic-ai/mcp-fetch` |
| ทดสอบ UI / Screenshot | `puppeteer` | `@anthropic-ai/mcp-puppeteer` |
| จัดการ Database SQLite | `sqlite` | `@anthropic-ai/mcp-server-sqlite` |
| จัดการ GitHub (PR/Issues) | `github` | `@anthropic-ai/mcp-server-github` |

**Execution:**
1. รัน: `claude mcp list` → ดู MCP ที่มีอยู่
2. วิเคราะห์งาน → ระบุ MCP ที่ต้องใช้
3. IF ขาด MCP ที่จำเป็น → แนะนำคำสั่งติดตั้ง
4. สร้าง/อัพเดท `.axon/mcp.md`

### 4. CREATE/UPDATE ROADMAP

**ตาม MODE ที่ตรวจจับได้:**

#### MODE: NEW_CONCEPT
```markdown
## 📋 [NEW] Concept: [Name]
**Created:** [Timestamp]
**ID:** CONCEPT_001

- [ ] [C001.1] Task description
- [ ] [C001.2] Task description
...
```

#### MODE: ADD_CONCEPT
```markdown
## 📋 [ADD] Concept: [Name]
**Created:** [Timestamp]
**ID:** CONCEPT_002
**Related to:** CONCEPT_001

- [ ] [C002.1] Task description
- [ ] [C002.2] Task description

### 🔗 Dependencies with existing concepts:
- [C002.1] depends on [C001.3] (ต้องมี auth ก่อนทำ payment)
- [C001.2] และ [C002.1] ทำ parallel ได้
```

#### MODE: MODIFY_CONCEPT
```markdown
## ✏️ Modified: [TASK_ID]
**Original:** [เนื้อหาเดิม]
**Changed to:** [เนื้อหาใหม่]
**Reason:** [เหตุผลที่เปลี่ยน]
**Impact:** [งานอื่นที่ได้รับผลกระทบ]
```

#### MODE: EXPAND_CONCEPT
```markdown
## 🔍 Expanded: [TASK_ID]
**Original task:** [Task เดิม]
**Broken into:**
- [ ] [TASK_ID.1] Sub-task 1
- [ ] [TASK_ID.2] Sub-task 2
- [ ] [TASK_ID.3] Sub-task 3
```

#### MODE: LINK_CONCEPTS (Master Roadmap)
```markdown
# 🗺️ MASTER ROADMAP

## 🎯 Vision
[เป้าหมายรวมของทุก concept]

## 📊 Concepts Overview
| ID | Concept | Tasks | Status | Dependencies |
|----|---------|-------|--------|--------------|
| C001 | [Name] | 5 | 2/5 done | None |
| C002 | [Name] | 3 | 0/3 done | C001 |
| C003 | [Name] | 4 | 0/4 done | C001, C002 |

## 🔗 Dependency Graph
```
C001 (Foundation)
  ├──→ C002 (depends on C001)
  └──→ C003 (depends on C001)
         └──→ C004 (depends on C002 + C003)
```

## 📅 Execution Phases

### Phase 1: Foundation
- [ ] [C001.1] ... (no dependencies)
- [ ] [C001.2] ... (parallel with C001.1)

### Phase 2: Core
- [ ] [C002.1] ... (after C001 complete)
- [ ] [C003.1] ... (parallel with C002.1)

### Phase 3: Integration
- [ ] [C004.1] ... (after C002 + C003)

### Phase 4: Polish
- [ ] [MERGE] Final integration & testing

## ⚡ Parallel Opportunities
- C001.1 || C001.2 (ทำพร้อมกันได้)
- C002.1 || C003.1 (ทำพร้อมกันได้)

## ⚠️ Critical Path
C001.1 → C001.3 → C002.2 → C004.1 → MERGE
(ถ้า delay ที่ task เหล่านี้ จะ delay ทั้งโปรเจค)
```

### 5. UPDATE STATE

อัพเดท AXON_STATE.md:
- Context Dump: สรุปสิ่งที่กำลังจะทำ
- Quality Score: ประเมินความพร้อม
- **MCP Ready:** รายการ MCP ที่พร้อมใช้งาน
- **Concepts:** รายการ concepts ทั้งหมด
- **Master Vision:** เป้าหมายรวม (ถ้ามีหลาย concepts)

## Output Format

### สำหรับ NEW/ADD/MODIFY/EXPAND:

```markdown
# 📐 AXON Concept Report

## 🎯 Mode: [NEW/ADD/MODIFY/EXPAND]

## 🎯 Mission Understanding
[สรุปความเข้าใจในงาน]

## 🔍 Deep Analysis
[การวิเคราะห์เชิงลึก]

## ⚖️ Options Comparison

| Option | Pros | Cons | Score |
|--------|------|------|-------|
| A | ... | ... | X/10 |
| B | ... | ... | X/10 |
| C | ... | ... | X/10 |

## 💎 Selected Approach
[The Best option พร้อมเหตุผล]

## 🔌 MCP Requirements

| MCP | สถานะ | ใช้สำหรับ |
|-----|-------|---------|
| fetch | ✅ Ready / ❌ Need install | [เหตุผล] |
| puppeteer | ✅ Ready / ❌ Need install | [เหตุผล] |

## 🗺️ Roadmap Created/Updated
[รายการ Tasks ที่สร้าง/แก้ไขใน AXON_MAP.md]

## 🔗 Relationship with Existing Concepts
[ถ้ามี concepts เดิม - แสดงความสัมพันธ์]

## 📊 Next Steps
✅ แผนพร้อมแล้ว - มีทางเลือก:
- `/axon:concept เพิ่ม: [งานอื่น]` → เพิ่ม concept อีก
- `/axon:concept รวม` → ดู Master Roadmap
- `/axon:ignite` → เริ่มทำงานทันที
```

### สำหรับ LINK (Master Roadmap):

```markdown
# 🗺️ MASTER ROADMAP REPORT

## 📊 All Concepts
[ตาราง concepts ทั้งหมด]

## 🔗 Dependency Analysis
[วิเคราะห์ความสัมพันธ์]

## ⚡ Parallel Opportunities
[งานที่ทำพร้อมกันได้]

## ⚠️ Critical Path
[เส้นทางวิกฤต]

## 📅 Recommended Execution Order
[ลำดับการทำงานที่แนะนำ]

## 📊 Next Step
✅ Master Plan พร้อมแล้ว - พิมพ์ `/axon:ignite` เพื่อเริ่มทำงาน
```

---

## ⚠️ IMPORTANT RULE

**หลังจากสร้าง/อัพเดท Roadmap เสร็จแล้ว:**
- ✅ แสดงรายงาน Concept Report
- ✅ หยุดรอคำสั่งถัดไป
- ❌ **ห้ามเริ่มทำงานเอง**
- ❌ **ห้ามรัน IGNITE_LOOP อัตโนมัติ**

**User อาจต้องการ:**
- เพิ่ม concept อื่นก่อน ignite
- ปรับแก้ concept ที่วางไว้
- ขยายรายละเอียดเพิ่มเติม
- ดู Master Roadmap ก่อนตัดสินใจ

---

## 🔗 CONCEPT TAGGING RULES

**เพื่อให้ track ได้ว่า task มาจาก concept ไหน:**

```markdown
# Task ID Format:
[CONCEPT_ID.TASK_NUMBER]

# Examples:
[C001.1] = Concept 1, Task 1
[C001.2] = Concept 1, Task 2
[C002.1] = Concept 2, Task 1
[C002.3.1] = Concept 2, Task 3, Sub-task 1 (expanded)

# Special Tags:
[MERGE] = Integration task ที่รวมหลาย concepts
[SHARED] = Task ที่ใช้ร่วมกันหลาย concepts
[CRITICAL] = Task ที่อยู่บน Critical Path
```

---

## 📊 RELATIONSHIP TYPES

```
╔═══════════════════════════════════════════════════════════════════════╗
║  🔗 ประเภทความสัมพันธ์ระหว่าง Concepts/Tasks:                         ║
╠═══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  ➡️ DEPENDS ON (ต้องรอ):                                              ║
║     [C002.1] depends on [C001.3]                                     ║
║     = C002.1 ทำได้ต่อเมื่อ C001.3 เสร็จ                               ║
║                                                                       ║
║  ⚡ PARALLEL (ทำพร้อมกันได้):                                         ║
║     [C001.1] || [C001.2]                                             ║
║     = ทำพร้อมกันได้ ไม่ต้องรอกัน                                      ║
║                                                                       ║
║  🔄 SYNERGY (เสริมกัน):                                               ║
║     [C001] <-> [C002]                                                ║
║     = ทำด้วยกันได้ผลดีกว่าทำแยก                                       ║
║                                                                       ║
║  ⚠️ CONFLICT (ขัดแย้ง):                                               ║
║     [C001.2] ⚠️ [C003.1]                                              ║
║     = ต้องเลือกอันใดอันหนึ่ง หรือต้องปรับให้เข้ากัน                   ║
║                                                                       ║
║  📦 SHARED (ใช้ร่วมกัน):                                              ║
║     [SHARED.1] → [C001], [C002], [C003]                              ║
║     = Task ที่หลาย concepts ใช้ร่วมกัน                                ║
║                                                                       ║
╚═══════════════════════════════════════════════════════════════════════╝
```

---

## 🔄 CONCEPT EVOLUTION

**Concepts สามารถพัฒนาได้ตลอดเวลา:**

```
Initial State:
  /axon:concept สร้าง E-commerce
  → C001: E-commerce (5 tasks)

After adding:
  /axon:concept เพิ่ม: Payment System
  → C001: E-commerce (5 tasks)
  → C002: Payment (3 tasks)
  → Dependencies identified

After expanding:
  /axon:concept ขยาย: [C001.3]
  → C001: E-commerce (7 tasks - C001.3 split into 3)
  → C002: Payment (3 tasks)

After modifying:
  /axon:concept แก้: เปลี่ยนจาก Stripe เป็น PayPal
  → C002: Payment (3 tasks - updated)

After linking:
  /axon:concept รวม
  → MASTER ROADMAP created
  → 10 tasks total
  → Optimal execution order determined
```
