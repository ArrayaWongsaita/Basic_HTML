# กล่องทั่วไป: `<div>` และอินไลน์ทั่วไป: `<span>`

## ภาพรวม

`<div>` และ `<span>` เป็น HTML elements ที่เรียกว่า "Generic Elements" หรือ "กล่องทั่วไป" ซึ่ง:

- **ไม่มีความหมายเฉพาะ** (Non-semantic)
- **ใช้เป็นตัวแบ่งกลุ่ม** และจัดระเบียบเนื้อหา
- **เป็นพื้นฐานสำหรับ CSS และ JavaScript**
- **ใช้เมื่อไม่มี semantic element ที่เหมาะสม**

## แนวคิดหลัก

```
HTML Semantic Hierarchy:
┌─────────────────────────────────┐
│ Semantic Elements (ควรใช้ก่อน)    │
│ <header>, <nav>, <main>, etc.   │
├─────────────────────────────────┤
│ Generic Elements (ใช้เมื่อจำเป็น)  │
│ <div>, <span>                   │
└─────────────────────────────────┘
```

---

## 1. `<div>` Element - กล่องบล็อก

### คำอธิบาย

`<div>` (Division) เป็น **block-level element** ที่:

- **แสดงผลเป็นบล็อก** (ขึ้นบรรทัดใหม่)
- **ไม่มีความหมายเฉพาะ**
- **ใช้จัดกลุ่มเนื้อหา**
- **เป็นภาชนะสำหรับ CSS layout**

### คุณสมบัติพื้นฐาน

```css
div {
  display: block; /* แสดงเป็นบล็อก */
  width: 100%; /* กว้างเต็มพื้นที่ */
  margin: 0; /* ไม่มี margin เริ่มต้น */
  padding: 0; /* ไม่มี padding เริ่มต้น */
}
```

### ไวยากรณ์

```html
<div>
  <!-- เนื้อหาใดๆ -->
</div>

<div class="container">
  <!-- เนื้อหาที่มี class -->
</div>

<div id="unique-section">
  <!-- เนื้อหาที่มี id -->
</div>
```

---

## 2. การใช้งาน `<div>` อย่างถูกต้อง

### 2.1 Layout Container

```html
<!-- กล่องหลักของหน้าเว็บ -->
<div class="container">
  <div class="header">
    <h1>ชื่อเว็บไซต์</h1>
  </div>

  <div class="content">
    <div class="main-content">
      <h2>เนื้อหาหลัก</h2>
      <p>เนื้อหาของบทความ...</p>
    </div>

    <div class="sidebar">
      <h3>แถบข้าง</h3>
      <p>เนื้อหาเสริม...</p>
    </div>
  </div>

  <div class="footer">
    <p>&copy; 2024 เว็บไซต์</p>
  </div>
</div>
```

### 2.2 Grid System

```html
<!-- ระบบ Grid แบบ 12 คอลัมน์ -->
<div class="row">
  <div class="col-md-8">
    <h2>เนื้อหาหลัก (8 คอลัมน์)</h2>
    <p>เนื้อหาของบทความ...</p>
  </div>

  <div class="col-md-4">
    <h3>แถบข้าง (4 คอลัมน์)</h3>
    <ul>
      <li>ลิงก์ 1</li>
      <li>ลิงก์ 2</li>
    </ul>
  </div>
</div>

<!-- แถวที่สอง -->
<div class="row">
  <div class="col-md-4">คอลัมน์ 1</div>
  <div class="col-md-4">คอลัมน์ 2</div>
  <div class="col-md-4">คอลัมน์ 3</div>
</div>
```

### 2.3 Card Components

```html
<!-- การ์ดแสดงข้อมูล -->
<div class="card">
  <div class="card-header">
    <h3 class="card-title">หัวข้อการ์ด</h3>
  </div>

  <div class="card-body">
    <p class="card-text">เนื้อหาในการ์ด...</p>
    <div class="card-actions">
      <button class="btn btn-primary">ดูเพิ่มเติม</button>
      <button class="btn btn-secondary">แชร์</button>
    </div>
  </div>

  <div class="card-footer">
    <small class="text-muted">อัปเดตล่าสุด: 5 นาทีที่แล้ว</small>
  </div>
</div>
```

### 2.4 Form Grouping

```html
<!-- จัดกลุ่มฟิลด์ในแบบฟอร์ม -->
<form>
  <div class="form-group">
    <label for="firstName">ชื่อ:</label>
    <input type="text" id="firstName" name="firstName" class="form-control" />
  </div>

  <div class="form-group">
    <label for="lastName">นามสกุล:</label>
    <input type="text" id="lastName" name="lastName" class="form-control" />
  </div>

  <div class="form-group">
    <label for="email">อีเมล:</label>
    <input type="email" id="email" name="email" class="form-control" />
  </div>

  <div class="form-actions">
    <button type="submit" class="btn btn-primary">ส่งข้อมูล</button>
    <button type="reset" class="btn btn-secondary">ล้างข้อมูล</button>
  </div>
</form>
```

### 2.5 Media Objects

```html
<!-- วัตถุสื่อแบบผสม -->
<div class="media">
  <div class="media-object">
    <img src="avatar.jpg" alt="รูปโปรไฟล์" class="avatar" />
  </div>

  <div class="media-body">
    <h4 class="media-heading">จอห์น โด</h4>
    <p>นี่คือข้อความจากผู้ใช้ รวมถึงเนื้อหาที่ยาวและมีรายละเอียด...</p>

    <div class="media-meta">
      <span class="timestamp">2 ชั่วโมงที่แล้ว</span>
      <span class="actions">
        <a href="#">ตอบกลับ</a>
        <a href="#">ถูกใจ</a>
      </span>
    </div>
  </div>
</div>
```

---

## 3. `<span>` Element - อินไลน์ทั่วไป

### คำอธิบาย

`<span>` เป็น **inline element** ที่:

- **แสดงผลในบรรทัดเดียวกัน**
- **ไม่มีความหมายเฉพาะ**
- **ใช้จัดรูปแบบข้อความ**
- **เป็นภาชนะสำหรับ styling แบบจุดเจาะจง**

### คุณสมบัติพื้นฐาน

```css
span {
  display: inline; /* แสดงในบรรทัดเดียวกัน */
  width: auto; /* ความกว้างตามเนื้อหา */
  height: auto; /* ความสูงตามเนื้อหา */
}
```

### ไวยากรณ์

```html
<span>ข้อความ</span>

<span class="highlight">ข้อความที่ไฮไลต์</span>

<span id="special-text">ข้อความพิเศษ</span>
```

---

## 4. การใช้งาน `<span>` อย่างถูกต้อง

### 4.1 Text Styling

```html
<!-- การจัดรูปแบบข้อความ -->
<p>
  นี่คือข้อความปกติ แต่ <span class="highlight">ข้อความนี้ถูกไฮไลต์</span> และ
  <span class="bold">ข้อความนี้เป็นตัวหนา</span>
</p>

<p>
  ราคา: <span class="price">฿1,299</span> (ลดจาก
  <span class="original-price">฿1,599</span>)
</p>

<p>สถานะ: <span class="status status-active">ใช้งานได้</span></p>
```

### 4.2 Icon และ Labels

```html
<!-- ไอคอนและป้ายกำกับ -->
<p><span class="icon">📧</span> อีเมล: contact@example.com</p>

<p><span class="icon">📞</span> โทรศัพท์: 02-123-4567</p>

<h2>บทความใหม่ <span class="badge badge-new">ใหม่</span></h2>

<button class="btn">
  <span class="icon">💾</span>
  <span class="text">บันทึก</span>
</button>
```

### 4.3 Data Attributes

```html
<!-- แสดงข้อมูลที่มีหน่วย -->
<p>อุณหภูมิ: <span class="temperature" data-unit="celsius">25</span>°C</p>

<p>น้ำหนัก: <span class="weight" data-unit="kg">75</span> กิโลกรัม</p>

<p>เวลา: <span class="time" data-format="24h">14:30</span></p>
```

### 4.4 Form Elements

```html
<!-- ข้อความในแบบฟอร์ม -->
<label for="password"> รหัสผ่าน <span class="required">*</span> </label>
<input type="password" id="password" name="password" />
<span class="help-text">รหัสผ่านต้องมีอย่างน้อย 8 ตัวอักษร</span>

<div class="form-group">
  <label>
    <input type="checkbox" name="agree" />
    ฉันยอมรับ <span class="link-text">ข้อกำหนดการใช้งาน</span>
  </label>
</div>
```

### 4.5 Breadcrumb Navigation

```html
<!-- เส้นทางนำทาง -->
<nav class="breadcrumb">
  <span class="breadcrumb-item">
    <a href="/">หน้าแรก</a>
  </span>
  <span class="breadcrumb-separator">/</span>
  <span class="breadcrumb-item">
    <a href="/products">สินค้า</a>
  </span>
  <span class="breadcrumb-separator">/</span>
  <span class="breadcrumb-item current"> โทรศัพท์มือถือ </span>
</nav>
```

---

## 5. การเปรียบเทียบ `<div>` vs `<span>`

| คุณสมบัติ                 | `<div>`           | `<span>`                        |
| ------------------------- | ----------------- | ------------------------------- |
| **Display Type**          | Block             | Inline                          |
| **การขึ้นบรรทัดใหม่**     | ใช่               | ไม่ใช่                          |
| **ความกว้างเริ่มต้น**     | 100%              | ตามเนื้อหา                      |
| **สามารถมี width/height** | ใช่               | ไม่ได้ (เว้นแต่เปลี่ยน display) |
| **ใช้สำหรับ**             | Layout, Container | Text styling, Inline elements   |

### ตัวอย่างการเปรียบเทียบ

```html
<!-- div - Block level -->
<div class="block-example">
  <p>บล็อกที่ 1</p>
</div>
<div class="block-example">
  <p>บล็อกที่ 2</p>
</div>
<!-- ผลลัพธ์: แต่ละ div จะขึ้นบรรทัดใหม่ -->

<!-- span - Inline level -->
<p>
  <span class="inline-example">อินไลน์ที่ 1</span>
  <span class="inline-example">อินไลน์ที่ 2</span>
</p>
<!-- ผลลัพธ์: span ทั้งสองจะอยู่ในบรรทัดเดียวกัน -->
```

---

## 6. เมื่อไหร่ควรใช้ Semantic Elements แทน

### ❌ ไม่ควรใช้ `<div>` เมื่อมี Semantic Element

```html
<!-- ผิด - ใช้ div แทน semantic elements -->
<div class="header">
  <div class="navigation">
    <div class="menu-item"><a href="/">หน้าแรก</a></div>
  </div>
</div>
<div class="main-content">
  <div class="article">
    <div class="article-header">หัวข้อบทความ</div>
  </div>
</div>

<!-- ถูก - ใช้ semantic elements -->
<header>
  <nav>
    <ul>
      <li><a href="/">หน้าแรก</a></li>
    </ul>
  </nav>
</header>
<main>
  <article>
    <header>
      <h1>หัวข้อบทความ</h1>
    </header>
  </article>
</main>
```

### ✅ ใช้ `<div>` เมื่อจำเป็นสำหรับ Layout

```html
<!-- เหมาะสม - ใช้ div สำหรับ layout ที่ไม่มี semantic meaning -->
<section class="products">
  <h2>สินค้าของเรา</h2>

  <!-- Grid container -->
  <div class="product-grid">
    <div class="product-item">
      <h3>สินค้า 1</h3>
      <p>รายละเอียด...</p>
    </div>

    <div class="product-item">
      <h3>สินค้า 2</h3>
      <p>รายละเอียด...</p>
    </div>
  </div>
</section>
```

---

## 7. CSS Styling สำหรับ `<div>` และ `<span>`

### CSS Framework Patterns

```css
/* Container และ Layout */
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 15px;
}

.row {
  display: flex;
  flex-wrap: wrap;
  margin: 0 -15px;
}

.col {
  flex: 1;
  padding: 0 15px;
}

/* Card Component */
.card {
  background: white;
  border: 1px solid #dee2e6;
  border-radius: 0.375rem;
  overflow: hidden;
  box-shadow: 0 0.125rem 0.25rem rgba(0, 0, 0, 0.075);
}

.card-header {
  padding: 1rem;
  background-color: #f8f9fa;
  border-bottom: 1px solid #dee2e6;
}

.card-body {
  padding: 1rem;
}

/* Span Styling */
.highlight {
  background-color: #fff3cd;
  padding: 0.125rem 0.25rem;
  border-radius: 0.125rem;
}

.badge {
  display: inline-block;
  padding: 0.25rem 0.5rem;
  font-size: 0.75rem;
  font-weight: 700;
  line-height: 1;
  text-align: center;
  white-space: nowrap;
  border-radius: 0.375rem;
}

.badge-new {
  color: #fff;
  background-color: #dc3545;
}

.required {
  color: #dc3545;
  font-weight: bold;
}
```

---

## 8. JavaScript และ Generic Elements

### การจัดการ DOM

```javascript
// สร้าง div elements แบบ dynamic
function createCard(title, content) {
  const card = document.createElement('div');
  card.className = 'card';

  const cardHeader = document.createElement('div');
  cardHeader.className = 'card-header';
  cardHeader.innerHTML = `<h3>${title}</h3>`;

  const cardBody = document.createElement('div');
  cardBody.className = 'card-body';
  cardBody.innerHTML = `<p>${content}</p>`;

  card.appendChild(cardHeader);
  card.appendChild(cardBody);

  return card;
}

// เพิ่มการ์ดใหม่
const container = document.querySelector('.card-container');
const newCard = createCard('หัวข้อใหม่', 'เนื้อหาของการ์ด');
container.appendChild(newCard);
```

### Event Delegation

```javascript
// ใช้ event delegation กับ div container
document
  .querySelector('.button-container')
  .addEventListener('click', function (e) {
    if (e.target.classList.contains('btn')) {
      console.log('ปุ่มถูกคลิก:', e.target.textContent);
    }
  });

// จัดการ span elements
document.querySelectorAll('.highlight').forEach((span) => {
  span.addEventListener('mouseover', function () {
    this.style.backgroundColor = '#ffeb3b';
  });

  span.addEventListener('mouseout', function () {
    this.style.backgroundColor = '#fff3cd';
  });
});
```

---

## 9. Accessibility (การเข้าถึง)

### ARIA Attributes สำหรับ Generic Elements

```html
<!-- เพิ่ม role และ aria-label สำหรับ div ที่มีหน้าที่พิเศษ -->
<div role="button" aria-label="ปิดหน้าต่าง" tabindex="0" class="close-button">
  <span aria-hidden="true">&times;</span>
</div>

<div role="alert" aria-live="polite" class="notification">
  <span class="icon" aria-hidden="true">⚠️</span>
  <span class="message">กรุณาตรวจสอบข้อมูลให้ถูกต้อง</span>
</div>

<!-- การจัดกลุ่มที่มีความหมาย -->
<div role="group" aria-labelledby="form-title">
  <h3 id="form-title">ข้อมูลส่วนตัว</h3>
  <!-- form fields -->
</div>
```

### Focus Management

```css
/* ทำให้ div สามารถ focus ได้ */
.focusable-div {
  outline: none;
}

.focusable-div:focus {
  outline: 2px solid #007bff;
  outline-offset: 2px;
}

/* Skip links */
.skip-link {
  position: absolute;
  top: -40px;
  left: 6px;
  background: #000;
  color: #fff;
  padding: 8px;
  text-decoration: none;
  z-index: 1000;
}

.skip-link:focus {
  top: 6px;
}
```

---

## 10. แนวทางปฏิบัติที่ดี

### ✅ ควรทำ

```html
<!-- ใช้ class names ที่มีความหมาย -->
<div class="user-profile">
  <div class="avatar-container">
    <img src="avatar.jpg" alt="รูปโปรไฟล์" />
  </div>
  <div class="user-info">
    <span class="username">johndoe</span>
    <span class="user-role">ผู้ดูแลระบบ</span>
  </div>
</div>

<!-- ใช้ BEM naming convention -->
<div class="card">
  <div class="card__header">
    <h3 class="card__title">หัวข้อ</h3>
  </div>
  <div class="card__body">
    <p class="card__text">เนื้อหา</p>
    <span class="card__badge card__badge--new">ใหม่</span>
  </div>
</div>
```

### ❌ ไม่ควรทำ

```html
<!-- หลีกเลี่ยง class names ที่ไม่มีความหมาย -->
<div class="box1">
  <div class="red-text">
    <span class="big">ข้อความ</span>
  </div>
</div>

<!-- หลีกเลี่ยงการซ้อน div เกินความจำเป็น -->
<div class="container">
  <div class="wrapper">
    <div class="inner">
      <div class="content">
        <p>เนื้อหา</p>
        <!-- div เกินความจำเป็น -->
      </div>
    </div>
  </div>
</div>
```

---

## สรุป

### `<div>` - Block Container

**ใช้เมื่อ:**

- จำเป็นต้องจัดกลุ่มเนื้อหาแบบบล็อก
- สร้าง layout และ grid system
- ไม่มี semantic element ที่เหมาะสม
- ต้องการ container สำหรับ CSS/JavaScript

**หลีกเลี่ยงเมื่อ:**

- มี semantic element ที่เหมาะสมกว่า
- ใช้เพื่อจัดรูปแบบเท่านั้น (ควรใช้ CSS)

### `<span>` - Inline Container

**ใช้เมื่อ:**

- จัดรูปแบบข้อความแบบจุดเจาะจง
- เพิ่มไอคอนหรือป้ายกำกับ
- ต้องการ wrapper สำหรับข้อความ
- สร้าง inline components

**หลีกเลี่ยงเมื่อ:**

- มี semantic element ที่เหมาะสมกว่า (`<strong>`, `<em>`, `<code>`)
- ใช้เพื่อสร้าง layout (ควรใช้ `<div>`)

### หลักการสำคัญ

1. **Semantic First**: ใช้ semantic elements ก่อนเสมอ
2. **Meaningful Names**: ตั้งชื่อ class ที่มีความหมาย
3. **Minimal Markup**: หลีกเลี่ยงการซ้อนที่ไม่จำเป็น
4. **Accessibility**: เพิ่ม ARIA attributes เมื่อจำเป็น

Generic elements เป็นเครื่องมือที่ทรงพลัง แต่ควรใช้อย่างระมัดระวังและมีเหตุผล เพื่อให้ HTML มีความหมายและเข้าถึงได้ง่าย
