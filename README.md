# 🏪 Franchise Eval – ระบบประเมินความคุ้มค่าแฟรนไชส์

อ้างอิงสมการคณิตศาสตร์จากโครงงานโรงเรียนดีบุกพังงาวิทยายน

---

## 🚀 วิธีรันทดสอบ (ไม่ต้องติดตั้งอะไรเพิ่ม)

1. เปิดโฟลเดอร์ `d:\Franchise Eval\`
2. ดับเบิลคลิกที่ไฟล์ **`index.html`** — เปิดได้ทันทีใน Browser
3. ทุกอย่างทำงานได้เลย (Tailwind + Chart.js + Firebase SDK โหลดผ่าน CDN)

> หากต้องการใช้ Firebase ให้ทำตามขั้นตอนด้านล่างก่อน

---

## 🔥 ตั้งค่า Firebase (ทำครั้งเดียว)

1. ไปที่ [Firebase Console](https://console.firebase.google.com/)
2. สร้าง Project ใหม่ (หรือเลือก Project ที่มีอยู่)
3. ไปที่ **Project Settings → Your apps → Add app → Web**
4. Copy Firebase Config ที่ได้มา
5. เปิดไฟล์ `index.html` และหาส่วนนี้:

```javascript
const firebaseConfig = {
  apiKey:            "YOUR_API_KEY",      // ← วางค่าที่นี่
  authDomain:        "YOUR_AUTH_DOMAIN",
  projectId:         "YOUR_PROJECT_ID",
  storageBucket:     "YOUR_STORAGE_BUCKET",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId:             "YOUR_APP_ID",
};
```

6. แทนค่าทุก `"YOUR_..."` ด้วยค่าจาก Firebase Console
7. ไปที่ **Firestore Database → Create database** → เลือก Test mode (สำหรับ dev)
8. รีเฟรชหน้าเว็บ — ระบบจะเชื่อมต่อ Firebase อัตโนมัติ

---

## 📐 สมการคณิตศาสตร์ที่ใช้

| ฟังก์ชัน | สมการ | ตัวแปร |
|---|---|---|
| จุดคุ้มทุน | `x = b ÷ (p − v)` | b=ต้นทุนคงที่, p=ราคาขาย, v=ต้นทุนผันแปร |
| ราคาขั้นต่ำ | `P_min = (b + v·Q) ÷ Q` | Q=กำลังการผลิต×วัน |
| อุปทาน (Supply) | `y = S₀·[1 + r·(x − x₀)]` | S₀=Base Supply, r=อัตราเปลี่ยนแปลง |
| อุปสงค์ (Demand) | `y = D₀ − d·(x − x₀)` | D₀=อุปสงค์ฐาน, d=อัตราลด |
| จุดดุลยภาพ | `x* = x₀ + (D₀ − S₀) ÷ (S₀·r + d)` | แก้สมการ Supply = Demand |

---

## 📁 โครงสร้างไฟล์

```
d:\Franchise Eval\
└── index.html      ← ไฟล์หลัก (ทุกอย่างอยู่ในไฟล์เดียว)
└── README.md       ← คู่มือนี้
```

---

## ✨ ฟีเจอร์

- ✅ จุดคุ้มทุน (BEP) พร้อม CountUp animation
- ✅ ราคาขั้นต่ำ (Minimum Price Optimizer)
- ✅ กราฟ Supply/Demand อัปเดต Real-time ด้วย Chart.js
- ✅ บันทึก / ดึงประวัติจาก Firebase Firestore
- ✅ Dark mode + Glassmorphism + Responsive Design
- ✅ Toast notifications + Micro-animations
