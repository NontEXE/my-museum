# NONT — Inner Gallery

เว็บไซต์แกลเลอรีศิลปะส่วนตัวแบบ static ใช้เฉพาะ Plain HTML, CSS และ Vanilla JavaScript ไม่มี framework และไม่มี build step

## วิธีเปิดเว็บ

เปิดผ่าน local static server เพื่อให้ path ของรูปและ hash routing ทำงานเหมือนตอน deploy:

```sh
python3 -m http.server 8080
```

จากนั้นเปิด:

```text
http://localhost:8080
```

## โครงสร้างไฟล์

```text
.
├── index.html
├── styles.css
├── app.js
├── favicon.svg
├── assets/
│   ├── originals/
│   └── artworks/
└── README.md
```

`assets/originals` เก็บภาพต้นฉบับจาก archive โดยเปลี่ยนชื่อเป็น slug ภาษาอังกฤษ  
`assets/artworks` เก็บภาพสำหรับเว็บ แยกเป็น `*-thumb.webp` และ `*-detail.webp`

## วิธีเพิ่มงานศิลปะในอนาคต

1. วางภาพต้นฉบับใน `assets/originals`
2. สร้างไฟล์สำหรับเว็บใน `assets/artworks` อย่างน้อย 2 ขนาด:
   `slug-thumb.webp` และ `slug-detail.webp`
3. เพิ่ม object ใหม่ใน array `artworks` ที่อยู่ด้านบนของ `app.js`
4. ใส่ `width` และ `height` ของทั้ง thumbnail และ detail image ให้ตรงกับไฟล์จริง
5. ใส่ `alt`, `themes`, `shortLine`, `opening`, `personalMeaning`, `origin` และ `dailyQuote`

## วิธีแก้ข้อความของแต่ละภาพ

แก้ใน array `artworks` ภายใน `app.js` โดยตรง เพราะเว็บนี้ไม่ fetch JSON แยก ข้อความสำคัญอยู่ใน field เหล่านี้:

```text
shortLine
opening
personalMeaning
origin
dailyQuote
alt
```

## Deploy แบบ Static

GitHub Pages:

1. push ไฟล์ทั้งหมดขึ้น repository
2. เปิด Settings > Pages
3. เลือก branch และ root folder

Cloudflare Pages:

1. สร้าง Pages project จาก repository
2. Build command เว้นว่าง
3. Output directory ใช้ `/` หรือ root ของโปรเจกต์

Vercel:

1. Import repository
2. Framework preset เลือก Other
3. Build command เว้นว่าง
4. Output directory ใช้ `.`

## หมายเหตุเรื่องภาพ

ภาพทั้งหมดในเว็บนี้มาจาก archive ที่ผู้ใช้ให้มาเท่านั้น ไม่มีการดาวน์โหลดภาพจากอินเทอร์เน็ต และไฟล์ `__MACOSX` หรือ `._*` ไม่ถูกนำเข้าเว็บ
# my-museum
