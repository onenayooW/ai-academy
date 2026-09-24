# Definition of Done

## Tech stack

### Frontend (Vue.js)

- Node.js `24.20.0` (เครื่อง dev ใช้ 24.x ได้ — อาจมี EBADENGINE warning)
- Vue `3.5.x`
- vue-router `4.6.x`
- Vite `6.4.x`
- `@vitejs/plugin-vue` `5.2.x`
- `@lucide/vue` — ไอคอนทั่วไป (โทร, แก้ไข, ลบ, ลูกศร, ตัวกรอง ฯลฯ)
- คอมโพเนนต์ UI กลาง: `Button`, `LineIcon`, `SellerAvatar`, `Pagination`

### Backend (Node + Express)

- express `5.2.x`
- drizzle-orm `0.44.x` + better-sqlite3 `12.x`
- SQLite ไฟล์ `backend/data/truck2hand.db` (WAL mode)
- multer — อัปโหลดรูปสินค้า (สูงสุด 4) และ avatar
- cors, swagger-ui-express (ถ้าเปิด docs)

### Dev & proxy

- Frontend dev: `http://127.0.0.1:5173`
- Backend: port `3001`
- Vite proxy `/api` และ `/uploads` ไป backend

---

## Product — ฟังก์ชันหลัก

- ครบ 3 หน้าเชื่อมโยงกัน: **หน้าแรก** `/`, **รายละเอียด** `/products/:id`, **admin** `/admin`
- Responsive ตาม breakpoint การ์ด grid / drawer / modal
- **Filter** หลายเงื่อนไขพร้อมกัน (ประเภท, ยี่ห้อ, รุ่น, ช่วงราคา, ช่วงปี) ผ่าน drawer + filter chips
- **Sort** ผ่าน API: `newest` (default), `views`, `price`, `price_desc` — UI ไม่มี `oldest`
- **Pagination** API: query `page`, `pageSize` (default 10) → response `{ data, meta: { page, pageSize, total } }`
  - หน้าแรก: 12/หน้า
  - Admin: 10/หน้า
- รายละเอียด: gallery slide, สินค้าแนะนำ 4 รายการ (API เดิม, filter id ตัวเอง)
- Admin CRUD ผ่าน modal + ตาราง paginated

---

## Product — รูปภาพ & ภาพปก

- Mock/seed ใช้รูปรถจริง `mock-truck.jpg`
- อัปโหลด `.png` / `.jpg` สูงสุด 4 รูปต่อ listing
- ตั้งภาพปกได้ — **cover index 0 หลังบันทึก** (UI บังคับปกอยู่ช่องแรก, ส่ง `imageOrder` + `coverIndex: 0`)
- ลากเรียงลำดับรูปใน modal (ยกเว้นช่องปก)
- ลบรูปเก่าจาก disk เมื่อแก้ไข/ลบสินค้า

---

## Product — Validation & Error handling

- Backend `validateProduct`: ชื่อซ้ำ, ราคา (< 0 หรือ > 99,999,999), คีย์เวิร์ดผิดกฎหมาย, จำนวนรูป, cover index
- API ตอบ `{ error, fields[] }` — frontend แสดง `form-error` และ `field-error` ต่อฟิลด์
- 404 เมื่อไม่พบสินค้า; ดูรายละเอียด increment `viewCount`

---

## Product — UI / Design system

- ธีม **อู่น้ำเงิน**: พื้น `#F4F7FB`, header `#0B1F3A`, ปุ่มหลัก `#F97316`, ราคา `#DC2626`, LINE `#06C755`
- Design tokens อยู่ที่ `frontend/src/styles.css` (`:root`)
- ฟอnt **Prompt** (400–700)
- Scale ตัวอักษร: 12, 16, 18, 20, 24, 28, 32, 36 (ไม่ใช้ 11/13/14/22)
- หน้า reference: `/design-system`
- โลโก้ header: CARHUB แนวนอน (ไม่ใช่ Truck2Hand text)
- ไม่แสดง verified-seller badge ใน UI
- Seller avatar fallback: Lucide `UserRound` วงกลมสี brand

---

## Data

- Seed เริ่มต้น 8 รายการ + **seedMissing** เติมอีก 20 รายการ (รวม ~28 สำหรับทดสอบ pagination)
- `sellerAvatar` เป็น null ได้ (ไม่ generate avatar ปลอม)
- Product id 10 (test) เก็บรูป/avatar อัปโหลดจริงไว้ทดสอบ gallery หลายรูป

---

## Demo & quality

- Demo flow ได้ครบ: ดูสินค้า → sort → เปิด filter/chip → pagination → ดูรายละเอียด (slide รูป, สินค้าแนะนำ) → admin เพิ่ม/แก้/ลบ
- อธิบายได้ว่า AI ช่วยส่วนใด และมนุษย์ตรวจ/ปรับ UI, seed, ธีม
- Backend unit test: `npm test` (productService — filter, sort, pagination, CRUD, cover)
- ไม่มี regression ที่รู้จักบน filter drawer, modal form, และ pagination ทั้ง home/admin

---

## Out of scope / ยังไม่อัปเดตใน repo

- README / ARCHITECTURE / DATABASE docs บางส่วนยังอ้าง badge, avatar default, sort เก่า — อัปเดต docs แยกเมื่อต้องการ
- ไม่มีลิงก์ design-system ใน header โดยเจตนา
- Sort `oldest` มีใน API/tests แต่ไม่ expose ใน UI
