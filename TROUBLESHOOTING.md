# Troubleshooting Guide

คู่มือแก้ปัญหาสำหรับ AXON Zenith

---

## Command ไม่ทำงาน

### ปัญหา: พิมพ์ `/axon:xxx` แล้วไม่เกิดอะไร

**สาเหตุ:** ไฟล์ command ไม่ได้ติดตั้งในตำแหน่งที่ถูกต้อง

**วิธีแก้:**

1. ตรวจสอบว่าไฟล์อยู่ถูกที่:
   ```bash
   # Windows
   ls $env:USERPROFILE\.claude\commands\axon\

   # macOS/Linux
   ls ~/.claude/commands/axon/
   ```

2. ต้องเห็นไฟล์เหล่านี้:
   ```
   setup.md
   concept.md
   ignite.md
   enlighten.md
   mcp.md
   upgrade.md
   ```

3. ถ้าไม่มี ให้ติดตั้งใหม่ตาม README.md

---

### ปัญหา: Command ทำงานไม่ครบ

**สาเหตุ:** ไฟล์ command เวอร์ชันเก่า

**วิธีแก้:**
```bash
# ลบของเก่า แล้วติดตั้งใหม่
# Windows
Remove-Item -Recurse -Force "$env:USERPROFILE\.claude\commands\axon"

# macOS/Linux
rm -rf ~/.claude/commands/axon
```

จากนั้นติดตั้งใหม่ตาม README.md

---

## Claude หยุดกลางคัน

### ปัญหา: Claude หยุดทำงานเองโดยไม่มีเหตุผล

**สาเหตุที่เป็นไปได้:**

1. **Context เต็ม** - Claude ถูก compact
2. **API Rate Limit** - ถูก limit การเรียก API
3. **Network Error** - Connection ขาด

**วิธีแก้:**

1. พิมพ์ `/axon:ignite` อีกครั้ง - Claude จะอ่าน `AXON_STATE.md` และทำต่อ
2. ตรวจสอบ `AXON_STATE.md` ว่ามี resume point ไหม
3. ถ้าต้องการเริ่มใหม่ พิมพ์ `/axon:concept [งาน]` แทน

---

### ปัญหา: Claude ลืม context หลัง compact

**สาเหตุ:** Context ถูก compact แต่ไม่ได้อ่าน STATE/MAP

**วิธีแก้:**

1. Claude ควรอ่าน `AXON_STATE.md` อัตโนมัติ
2. ถ้าไม่ ให้พิมพ์: "อ่าน AXON_STATE.md และทำต่อ"

---

## Knowledge ไม่บันทึก

### ปัญหา: ทำงานเสร็จแต่ไม่เห็น knowledge ใน AXON_KNOWLEDGE.md

**สาเหตุที่เป็นไปได้:**

1. Claude ลืมบันทึก (ไม่น่าเกิด ถ้า AXON ทำงานถูกต้อง)
2. ไม่มี knowledge ที่ "ตกผลึก" พอจะบันทึก

**วิธีแก้:**

1. บอก Claude: "บันทึก knowledge ที่ได้ลง AXON_KNOWLEDGE.md"
2. ตรวจสอบว่า knowledge มี format ถูกต้อง:
   ```markdown
   ---
   id: unique-id
   tags: [tag1, tag2]
   quality: zenith-verified
   ---

   ### หัวข้อ
   เนื้อหา
   ```

---

### ปัญหา: Knowledge ซ้ำกัน

**สาเหตุ:** Claude ไม่ได้ check ก่อนบันทึก

**วิธีแก้:**

1. บอก Claude: "ตรวจสอบ AXON_KNOWLEDGE.md ก่อนบันทึกใหม่"
2. ลบ entries ที่ซ้ำด้วยมือ

---

## MCP Connection Failed

### ปัญหา: MCP server ไม่ทำงาน

**สาเหตุที่เป็นไปได้:**

1. MCP ไม่ได้ติดตั้ง
2. MCP config ผิด
3. MCP process crash

**วิธีแก้:**

1. ตรวจสอบ MCP ที่ติดตั้ง:
   ```bash
   claude mcp list
   ```

2. ถ้าไม่มี ให้ติดตั้ง:
   ```bash
   claude mcp add puppeteer
   claude mcp add fetch
   ```

3. ตรวจสอบ config:
   ```bash
   # Windows
   cat $env:USERPROFILE\.claude\settings.json

   # macOS/Linux
   cat ~/.claude/settings.json
   ```

---

### ปัญหา: MCP puppeteer ไม่เปิด browser

**สาเหตุ:** Chrome/Chromium ไม่ได้ติดตั้ง หรือ path ผิด

**วิธีแก้:**

1. ติดตั้ง Chrome/Chromium
2. หรือใช้ `fetch` MCP แทนสำหรับ simple web requests

---

## AXON_MAP.md ปัญหา

### ปัญหา: Task ไม่ถูก mark เป็น [x]

**สาเหตุ:** Claude ลืม update หรือ format ผิด

**วิธีแก้:**

1. บอก Claude: "อัพเดท AXON_MAP.md - mark task ที่เสร็จแล้ว"
2. ตรวจสอบ format:
   ```markdown
   - [ ] [T001] Task ที่ยังไม่เสร็จ
   - [x] [T002] Task ที่เสร็จแล้ว
   ```

---

### ปัญหา: Task ID ซ้ำกัน

**สาเหตุ:** สร้าง task โดยไม่ check ID เดิม

**วิธีแก้:**

1. แก้ ID ด้วยมือให้ไม่ซ้ำ
2. บอก Claude: "ตรวจสอบ task IDs ใน MAP ก่อนสร้างใหม่"

---

## Performance Issues

### ปัญหา: Claude ทำงานช้า

**สาเหตุที่เป็นไปได้:**

1. ไฟล์ใหญ่เกินไป
2. ไม่ใช้ parallel execution
3. Context เกือบเต็ม

**วิธีแก้:**

1. ใช้ smart file reading (อ่านเฉพาะส่วนที่ต้องการ)
2. ใช้ parallel tool calls เมื่อทำได้
3. Checkpoint บ่อยๆ เพื่อป้องกัน context เต็ม

---

### ปัญหา: Token หมดเร็ว

**สาเหตุ:** อ่านไฟล์ใหญ่ทั้งไฟล์

**วิธีแก้:**

1. ใช้ line range เมื่ออ่านไฟล์
2. ใช้ search/grep แทนการอ่านทั้งไฟล์
3. Summarize ก่อนบันทึก knowledge

---

## Project-Specific Issues

### ปัญหา: โปรเจคเก่าใช้ AXON ไม่ได้

**สาเหตุ:** ไม่มีไฟล์ระบบ AXON

**วิธีแก้:**

1. รัน `/axon:setup` ในโปรเจค
2. หรือรัน `/axon:upgrade` ถ้ามี AXON เวอร์ชันเก่า

---

### ปัญหา: CLAUDE.md ถูก overwrite

**สาเหตุ:** รัน setup ซ้ำ หรือ merge conflict

**วิธีแก้:**

1. Restore จาก git: `git checkout CLAUDE.md`
2. หรือ copy จาก templates/

---

## ติดต่อขอความช่วยเหลือ

ถ้าแก้ไขไม่ได้:

1. เปิด Issue ที่ [GitHub Issues](https://github.com/vongsagon-git/axon-zenith/issues)
2. แนบข้อมูล:
   - Error message ที่เห็น
   - OS และ Claude Code version
   - ไฟล์ AXON_STATE.md (ถ้ามี)
