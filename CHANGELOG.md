# Changelog

All notable changes to AXON Zenith will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [1.2.0] - Multi-Agent Support

### Added
- **Boss-Worker Pattern** - Opus 4.5 เป็น Boss, Haiku เป็น Workers
- **Multi-Agent Execution** - ทำงานหลายอย่างพร้อมกัน
- **Multi-Vector Search** - ค้นหลายทางพร้อมกันใน Enlighten mode
- **Unified Knowledge Tracking** - IGNITE และ ENLIGHTEN ใช้ AXON_KNOWLEDGE.md ร่วมกัน
- **Credibility Scoring** - Score 0-100% สำหรับทุก fact
- **Check Before Search** - ตรวจ Knowledge ก่อนค้นซ้ำ

### Changed
- ปรับปรุง Status Display ให้แสดง Workers status
- เพิ่ม Vector progress indicators

---

## [1.1.0] - Enlighten Mode

### Added
- **`/axon:enlighten`** - ขุดข้อมูลไม่หยุด + คิดสดๆ + รับใบ้ได้
- **`/axon:upgrade`** - อัพเกรดโปรเจคเก่าให้รองรับ version ใหม่
- **Status Display** - แสดง Model, Mode, Task, Progress ทุก mode
- **Token Management** - Smart file reading + Checkpoint system
- **Concept Modes** - 5 โหมด (NEW, ADD, MODIFY, EXPAND, LINK)
- **User Hints** - รับใบ้จาก user ระหว่างทำงาน
- **Recovery Protocol** - กลับมาต่อได้หลัง context compact

### Changed
- ปรับปรุง Zenith Protocol ให้เข้มงวดขึ้น
- เพิ่ม Never Stop Protocol enforcement

---

## [1.0.0] - Initial Release

### Added
- **`/axon:setup`** - สร้างไฟล์ระบบ AXON + เลือก Knowledge Base
- **`/axon:concept`** - วางแผนงานแบบ Architecture First (3 Options)
- **`/axon:ignite`** - รัน Zenith Loop จนกว่างานจะเสร็จ
- **`/axon:mcp`** - จัดการ MCP Servers (add/list/recommend/remove)
- **AXON_MAP.md** - Task Roadmap (Checkbox format)
- **AXON_STATE.md** - System State + Resume Point
- **AXON_KNOWLEDGE.md** - Knowledge Vault
- **Zenith Protocol** - 3 Quality Gates
- **Never Stop Protocol** - ห้ามหยุดจนกว่าจะติด limit
- **Parallel Execution** - ทำ tool calls พร้อมกัน

---

## Version History Summary

| Version | Codename | Key Feature |
|---------|----------|-------------|
| 1.0.0 | Core | 4 Commands (setup, concept, ignite, mcp) |
| 1.1.0 | Enlighten | +2 Commands (enlighten, upgrade) + Status Display |
| 1.2.0 | Multi-Agent | Boss-Worker Pattern + Unified Knowledge |
| 2.0.0 | (Planned) | Vector Memory |
