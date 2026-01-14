---
description: "Start Zenith Loop (Infinite Mode) - ทำงานไม่หยุดจนกว่าจะติด limit"
---

# AXON IGNITE PROTOCOL (The Zenith Loop)

## Mission
รันลูปทำงาน **ไม่มีวันหยุด** จนกว่าจะติด limit — กลับมาใหม่ก็ต่อได้ทันที

## The Zenith Loop

### 1. STATE SYNC
```
READ: AXON_STATE.md
READ: AXON_KNOWLEDGE.md
READ: AXON_MAP.md
READ: .axon/mcp.md (MCP tools ที่ใช้ได้)
```

### 2. TASK SELECTION (Resume-Aware)

**เช็ค Resume Point ก่อน:**
- **IF** `Active Task` ใน AXON_STATE.md ไม่ใช่ "None":
  - → **Resume** task นั้น
  - → โหลด `Partial Results` มาใช้ต่อ
  - → ข้ามไป Step 4 (EXECUTION)
- **ELSE:**
  - → หยิบงาน `[ ]` งานแรกจาก AXON_MAP.md
  - → อัพเดท `Active Task` ใน STATE

### 3. MITOSIS (Self-Expand Tasks)

**Trigger Conditions:**

| เงื่อนไข | ต้องแตก? |
|---------|---------|
| ต้องใช้ > 3 tools/actions | ✅ YES |
| ข้าม domain (FE + BE + DB) | ✅ YES |
| ไม่สามารถ verify ได้ทีเดียว | ✅ YES |
| งานเล็ก ทำจบได้เลย | ❌ NO |

**IF ต้องแตก:**
1. แตกเป็น 3-7 sub-tasks
2. Max depth: 2 levels
3. ทุก sub-task ต้อง atomic
4. กลับไป Step 2

### 4. EXECUTION (Zenith Mode)

#### 4.1 PARALLEL CHECK (ทำก่อนเสมอ!)

**ถามตัวเอง:**
1. "มี tool calls ไหนทำพร้อมกันได้?"
2. "มีงานไหนใน MAP ที่ independent?"

| Situation | Parallel Action |
|-----------|----------------|
| Research หลายหัวข้อ | WebSearch พร้อมกัน |
| อ่านหลายไฟล์ | Read พร้อมกัน |
| ค้นหาหลาย pattern | Grep/Glob พร้อมกัน |

#### 4.2 Execute Phase
- ลงมือทำงาน
- สร้างผลลัพธ์

#### 4.3 MID-TASK SAVE (กันงานหาย)

ทุกครั้งที่มี progress สำคัญ → อัพเดท AXON_STATE.md

### 5. SELF-AUDIT (The Gatekeeper)

ถามตัวเอง 3 คำถาม:
1. "งานนี้ Deep พอหรือยัง?"
2. "ดีที่สุดหรือยัง? ทำได้ดีกว่านี้ไหม?"
3. "จัดเรียงสวยงาม อ่านง่ายไหม?"

**IF ANY FAILED:** ตีกลับ → วนกลับข้อ 4
**IF ALL PASSED:** ไปขั้นตอนถัดไป

### 6. KNOWLEDGE EXTRACTION (บังคับ!)

**ต้องบันทึกทุกครั้งที่จบ Task:**

```markdown
# เพิ่มเข้า AXON_KNOWLEDGE.md

---
id: [task-id]-[timestamp]
tags: [หัวข้อที่เกี่ยวข้อง]
---

### [สิ่งที่เรียนรู้]
- [Insight 1]
- [Insight 2]
```

### 7. CHECKPOINT (บังคับ! - ต้องทำทุกข้อ)

**อัปเดตทั้ง 3 ไฟล์:**

#### 7.1 AXON_MAP.md
```markdown
- [x] [TaskID] Task description ✅ (เสร็จแล้ว)
```

#### 7.2 AXON_STATE.md
```markdown
**Last Update:** [Timestamp ตอนนี้]
**Active Task:** [Task ถัดไป] หรือ "None"
**Last Action:** [สิ่งที่เพิ่งทำเสร็จ]
```

#### 7.3 AXON_KNOWLEDGE.md
- เพิ่ม Knowledge chunk ใหม่ (จาก Step 6)

#### 7.4 Git Commit (ถ้ามี git)
```bash
git add AXON_*.md && git commit -m "✅ [TaskID] completed"
```

**⚠️ ห้ามข้ามขั้นตอนนี้เด็ดขาด!**

### 8. AUTO-DISCOVERY (Infinite Expansion)

**สแกนหางานใหม่:**

| สิ่งที่สแกน | ตัวอย่าง |
|------------|---------|
| ปัญหาที่เจอระหว่างทำ | Bug, Error |
| โอกาสปรับปรุง | Performance, UX |
| งานที่เกี่ยวข้อง | Dependencies |

**Logic:**
- เจองานใหม่ (เล็ก) → สร้าง Task → กลับ Step 2
- เจองานใหม่ (ใหญ่) → รัน CONCEPT → กลับ Step 2
- ไม่เจอ + MAP ว่าง → สร้างจาก Template → กลับ Step 2

### 9. INFINITE LOOP

```
╔═══════════════════════════════════════════════════════════════╗
║  ⛔ HARD RULES                                                ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  🔴 ห้ามเด็ดขาด:                                              ║
║     ❌ พูดว่า "เสร็จแล้ว" / "Done"                            ║
║     ❌ ถาม "ต้องการให้ทำอะไรต่อ?"                             ║
║     ❌ รายงานสรุปแล้วหยุดรอ                                   ║
║                                                               ║
║  🟢 ต้องทำเสมอ:                                               ║
║     ✅ หลังจบ task → สร้างงานใหม่อย่างน้อย 1 งาน              ║
║     ✅ วนกลับ Step 1 ทันที                                    ║
║     ✅ Report จบด้วย "กำลังทำต่อ: [Task ID]"                   ║
║                                                               ║
║  🛑 หยุดได้เฉพาะ:                                             ║
║     1. ติด usage limit                                        ║
║     2. User พิมพ์ "หยุด" / "stop"                             ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

**วนกลับไป Step 1 ทันที → ห้ามหยุด!**

## Output Format (เมื่อจบแต่ละ Task)

```markdown
## ✅ [TaskID] Completed

**สิ่งที่ทำ:** [สรุปสั้นๆ]
**Quality Check:** ✓ Deep / ✓ Best / ✓ Clean
**Knowledge Saved:** [ถ้ามี]

---
**Progress:** [X/Y] tasks done
**กำลังทำต่อ:** [TaskID ถัดไป]
```

---

## ⚠️ MANDATORY FILE UPDATES

```
╔═══════════════════════════════════════════════════════════════════╗
║  🔴 ต้องอัปเดตทุกครั้งที่จบ Task (ห้ามข้าม!)                       ║
╠═══════════════════════════════════════════════════════════════════╣
║                                                                   ║
║  📋 AXON_MAP.md                                                   ║
║     → Mark [x] task ที่เสร็จ                                      ║
║     → เพิ่ม task ใหม่ที่ค้นพบ                                     ║
║                                                                   ║
║  🧠 AXON_STATE.md                                                 ║
║     → อัปเดต Last Update timestamp                                ║
║     → อัปเดต Active Task                                          ║
║     → อัปเดต Last Action                                          ║
║                                                                   ║
║  💎 AXON_KNOWLEDGE.md                                             ║
║     → เพิ่ม Knowledge chunk ใหม่                                  ║
║     → ใช้ภาษาไทย                                                  ║
║                                                                   ║
║  ❌ ถ้าไม่อัปเดต = ผิดกฎ AXON!                                    ║
╚═══════════════════════════════════════════════════════════════════╝
```
