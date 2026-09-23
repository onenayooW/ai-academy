# AI Academy Training — Truck2Hand

**Repo สำหรับฝึกสร้างผลิตภัณฑ์ด้วย AI (Cursor / AI coding assistant)**  
**Training repository for building a product with AI-assisted development**

| | |
| --- | --- |
| **Product** | **Truck2Hand** — เว็บขายรถบรรทุกมือสอง / used commercial truck marketplace |
| **Spec** | [`AcceptanceCriteria.md`](AcceptanceCriteria.md) · [`DefinitionOfDone.md`](DefinitionOfDone.md) |
| **Prompts** | [`prompt/backend/`](prompt/backend/) · [`prompt/frontend/`](prompt/frontend/) |

---

## Table of contents / สารบัญ

1. [What you will build / สิ่งที่ต้องทำ](#1-what-you-will-build--สิ่งที่ต้องทำ)
2. [Tech stack / เทคโนโลยีที่ใช้](#2-tech-stack--เทคโนโลยีที่ใช้)
3. [How to use this repo / วิธีใช้ repo นี้](#3-how-to-use-this-repo--วิธีใช้-repo-นี้)
4. [Backend steps / ขั้นตอน Backend](#4-backend-steps--ขั้นตอน-backend)
5. [Frontend steps / ขั้นตอน Frontend](#5-frontend-steps--ขั้นตอน-frontend)
6. [Demo checklist / เช็กลิสต์ก่อน Demo](#6-demo-checklist--เช็กลิสต์ก่อน-demo)

---

## 1. What you will build / สิ่งที่ต้องทำ

### English

You will implement **Truck2Hand**, a responsive web app for listing and managing second-hand trucks. The product has **three connected pages**:

| Page | Purpose |
| --- | --- |
| **Home** | Product grid, filters (type, price, year, brand/model), seller badges, Line/phone actions, link to admin |
| **Product detail** | Image gallery, specs, seller contact, primary CTA |
| **Admin** | CRUD for listings (modal form, image upload, validation), data table with edit/delete |

Behavior must match [`AcceptanceCriteria.md`](AcceptanceCriteria.md). Quality, stack, validation, sorting, duplicate-title checks, and tests must match [`DefinitionOfDone.md`](DefinitionOfDone.md).

### ไทย

คุณจะพัฒนา **Truck2Hand** เว็บแสดงและจัดการรถบรรทุกมือสองที่ **Responsive** มี **3 หน้าที่เชื่อมโยงกัน**:

| หน้า | หน้าที่ |
| --- | --- |
| **หน้าแรก** | Grid สินค้า, ตัวกรอง (ประเภทรถ, ราคา, ปี, ยี่ห้อ/รุ่น), ป้ายผู้ขาย, ปุ่ม Line/โทร, ไปหน้าจัดการ |
| **รายละเอียดสินค้า** | แกลเลอรีรูป, ข้อมูลรถ, ข้อมูลผู้ขาย, ปุ่มติดต่อ |
| **จัดการสินค้า** | สร้าง/แก้ไข/ลบ listing (ฟอร์มใน Modal, อัปโหลดรูป, validation), ตารางพร้อมแก้ไข/ลบ |

รายละเอียด UI/UX ดูที่ [`AcceptanceCriteria.md`](AcceptanceCriteria.md)  
ข้อกำหนดเทคนิค การ validate, sort, unit test ฯลฯ ดูที่ [`DefinitionOfDone.md`](DefinitionOfDone.md)

---

## 2. Tech stack / เทคโนโลยีที่ใช้

| Layer | Requirement (from DoD) |
| --- | --- |
| **Frontend** | Vue 3, vue-router, Vite — versions ตาม `DefinitionOfDone.md` |
| **Backend** | Node.js + Express, Drizzle ORM, SQLite (`better-sqlite3`), CORS, Multer, Swagger UI |

**EN:** Do not swap stacks unless your instructor says otherwise.  
**TH:** ห้ามเปลี่ยน stack นอกเหนือจาก DoD เว้นแต่ผู้สอนกำหนดเป็นอย่างอื่น

---

## 3. How to use this repo / วิธีใช้ repo นี้

### English

1. **Read** `DefinitionOfDone.md` and `AcceptanceCriteria.md` once before coding.
2. **Choose language** for prompts: Thai (`prompt/**/th/`) or English (`prompt/**/en/`). Use one language consistently per session if possible.
3. **Work in order:** complete **Backend steps 1 → 4**, then **Frontend steps** in numeric order.
4. **For each step:** open the matching `.md` file under `prompt/`, **copy the entire file content**, paste it into your AI assistant chat (e.g. Cursor Agent), and let it implement. Review diff, run the app, fix issues, then go to the next step.
5. **When stuck:** ask the AI to clarify against AC/DoD only; adjust prompts or fix code manually as needed.
6. **Before demo:** you should explain **what AI did** and **what humans verified or changed** (required in DoD).

### ไทย

1. **อ่าน** `DefinitionOfDone.md` และ `AcceptanceCriteria.md` ก่อนเริ่มเขียนโค้ด
2. **เลือกภาษา prompt:** ไทย (`prompt/**/th/`) หรืออังกฤษ (`prompt/**/en/`) — ควรใช้ภาษาเดียวกันตลอด session
3. **ทำตามลำดับ:** **Backend ขั้น 1 → 4** แล้วค่อย **Frontend** ตามเลขนำหน้าไฟล์
4. **แต่ละขั้น:** เปิดไฟล์ `.md` ใน `prompt/` → **คัดลอกทั้งไฟล์** → วางในแชท AI (เช่น Cursor Agent) → ตรวจโค้ด รัน แก้บั๊ก → ไปขั้นถัดไป
5. **ติดขัด:** ให้ AI อ้างอิงแค่ AC/DoD; ปรับ prompt หรือแก้มือตามความเหมาะสม
6. **ก่อน Demo:** เตรียมอธิบาย **AI ช่วยส่วนไหน** และ **มนุษย์ตรวจ/แก้อะไร** (บังคับใน DoD)

**EN:** This repo does not prescribe a fixed project folder layout — organize backend/frontend code however your team prefers.  
**TH:** repo นี้ **ไม่กำหนด** โครงสร้างโฟลเดอร์โปรเจกต์ — จัดวาง backend/frontend ตามที่ทีมสะดวก

---

## 4. Backend steps / ขั้นตอน Backend

ทำครบและเรียงตามนี้ **ก่อน** Frontend  
Complete these **before** starting the frontend.

| Step | Thai prompt | English prompt | Topic |
| ---: | --- | --- | --- |
| **1** | [`prompt/backend/th/1.SetUpProject.md`](prompt/backend/th/1.SetUpProject.md) | [`prompt/backend/en/1.SetUpProject.md`](prompt/backend/en/1.SetUpProject.md) | ตั้งค่าโปรเจกต์ Backend / Backend project setup |
| **2** | [`prompt/backend/th/2.DesignDatabase.md`](prompt/backend/th/2.DesignDatabase.md) | [`prompt/backend/en/2.DesignDatabase.md`](prompt/backend/en/2.DesignDatabase.md) | ออกแบบ schema (Drizzle + SQLite) / Database design |
| **3** | [`prompt/backend/th/3.APIDesign.md`](prompt/backend/th/3.APIDesign.md) | [`prompt/backend/en/3.APIDesign.md`](prompt/backend/en/3.APIDesign.md) | REST API + Swagger / API design |
| **4** | [`prompt/backend/th/4.SeedData.md`](prompt/backend/th/4.SeedData.md) | [`prompt/backend/en/4.SeedData.md`](prompt/backend/en/4.SeedData.md) | ข้อมูลตัวอย่าง CSV + seed / Seed data |

**EN — After step 4:** API should support listing, filtering, sorting, CRUD, uploads, and rules in DoD (duplicate titles, price bounds, etc.). Backend must include **unit tests**.

**TH — หลังขั้น 4:** API ควรรองรับ list, filter, sort, CRUD, อัปโหลด และกฎใน DoD (ชื่อซ้ำ, ราคาไม่สมเหตุสมผล ฯลฯ) และมี **unit test**

---

## 5. Frontend steps / ขั้นตอน Frontend

เริ่ม Frontend เมื่อ Backend ขั้น **1–4** ใช้งานได้แล้ว (หรือรัน API + seed ได้ขั้นต่ำ)  
Start frontend only after backend steps **1–4** work (or the API runs with seed data).

ใช้ไฟล์ใน `prompt/frontend/{th,en}/` **เรียงตามเลขนำหน้า** — ขั้นถัดไปจะเพิ่มใน repo ทีละไฟล์  
Use prompts **in numeric order** — additional steps will be added to the repo over time.

| Step | Thai prompt | English prompt | Topic |
| ---: | --- | --- | --- |
| **1** | [`prompt/frontend/th/1.SetUpProject.md`](prompt/frontend/th/1.SetUpProject.md) | [`prompt/frontend/en/1.SetUpProject.md`](prompt/frontend/en/1.SetUpProject.md) | ตั้งค่าโปรเจกต์ Frontend / Frontend project setup |
| **2+** | *(ตามมาทีหลัง / coming later)* | *(ตามมาทีหลัง / coming later)* | หน้า UI ตาม AC (หน้าแรก, รายละเอียด, จัดการ) / AC pages |

**EN — Planned themes for later steps:** home (Story 1), product detail (Story 2), admin (Story 3), plus responsive/error handling per DoD.  
**TH — ธีมขั้นถัดไป (เมื่อมีไฟล์):** หน้าแรก (Story 1), รายละเอียด (Story 2), จัดการ (Story 3), responsive และ error handling ตาม DoD

---

## 6. Demo checklist / เช็กลิสต์ก่อน Demo

| Check | EN | TH |
| --- | --- | --- |
| Flow | Browse → filter → detail → admin create/edit/delete | ดูสินค้า → กรอง → รายละเอียด → หลังบ้าน CRUD |
| DoD | Validation, error handling, sort options, duplicate title, price rules | ครบตาม DoD |
| Tests | Backend unit tests pass | unit test ผ่าน |
| Reflection | Explain AI vs human review | อธิบาย AI vs มนุษย์ตรวจ |

---

## Reference documents / เอกสารอ้างอิง

- [`AcceptanceCriteria.md`](AcceptanceCriteria.md) — UI และพฤติกรรมที่ต้องมี / UI & behavior
- [`DefinitionOfDone.md`](DefinitionOfDone.md) — stack, คุณภาพ, demo / stack, quality, demo

---

**Questions?** Ask your instructor or the AI using only AC + DoD as source of truth.  
**มีคำถาม?** ถามผู้สอนหรือ AI โดยอ้างอิง AC + DoD เป็นหลัก
