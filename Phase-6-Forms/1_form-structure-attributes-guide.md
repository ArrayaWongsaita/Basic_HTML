# Phase 6: ฟอร์ม (Forms) - โครงสร้างและ Attributes

## 1. ภาพรวม HTML Forms

HTML Forms เป็นส่วนสำคัญที่ช่วยให้ผู้ใช้สามารถส่งข้อมูลไปยัง Server ได้ ประกอบด้วย:

- **Form Container**: `<form>` element ที่ครอบคลุมทั้งฟอร์ม
- **Form Controls**: Input fields, buttons, select boxes, textarea
- **Labels**: คำอธิบายสำหรับแต่ละ control
- **Validation**: การตรวจสอบข้อมูล

## 2. ป้าย (Labels) และการเชื่อมโยง

### 2.1 `<label>` Element และ `for` Attribute

`<label>` เป็น element สำคัญที่ใช้สร้างป้ายชื่อสำหรับ form controls โดยใช้ `for` attribute เชื่อมโยงกับ `id` ของ input

**Syntax:**

```html
<label for="input-id">ข้อความป้าย</label>
<input type="text" id="input-id" name="fieldname" />
```

### 2.2 ประโยชน์ของการใช้ Label

1. **Accessibility**: ช่วย Screen Reader อ่านป้ายให้ผู้พิการทางสายตา
2. **UX**: คลิกที่ label จะโฟกัสไปที่ input ที่เชื่อมโยง
3. **SEO**: ช่วยให้ Search Engine เข้าใจโครงสร้างฟอร์ม
4. **Validation**: ช่วยในการแสดง error message

### 2.3 วิธีการเชื่อมโยง Label กับ Input

#### วิธีที่ 1: ใช้ `for` และ `id` (แนะนำ)

```html
<label for="username">ชื่อผู้ใช้:</label>
<input type="text" id="username" name="username" required />

<label for="email">อีเมล:</label>
<input type="email" id="email" name="email" required />

<label for="password">รหัสผ่าน:</label>
<input type="password" id="password" name="password" required />
```

#### วิธีที่ 2: ซ้อน Input ใน Label

```html
<label>
  ชื่อผู้ใช้:
  <input type="text" name="username" required />
</label>

<label>
  อีเมล:
  <input type="email" name="email" required />
</label>
```

### 2.4 ตัวอย่างการใช้งานแบบละเอียด

#### ฟอร์มข้อมูลส่วนตัว

```html
<form action="/profile" method="POST">
  <div class="form-group">
    <label for="firstName">ชื่อจริง *</label>
    <input
      type="text"
      id="firstName"
      name="firstName"
      placeholder="กรุณาใส่ชื่อจริง"
      autocomplete="given-name"
      required
    />
  </div>

  <div class="form-group">
    <label for="lastName">นามสกุล *</label>
    <input
      type="text"
      id="lastName"
      name="lastName"
      placeholder="กรุณาใส่นามสกุล"
      autocomplete="family-name"
      required
    />
  </div>

  <div class="form-group">
    <label for="birthDate">วันเกิด</label>
    <input type="date" id="birthDate" name="birthDate" autocomplete="bday" />
  </div>

  <div class="form-group">
    <label for="gender">เพศ</label>
    <select id="gender" name="gender">
      <option value="">-- เลือกเพศ --</option>
      <option value="male">ชาย</option>
      <option value="female">หญิง</option>
      <option value="other">อื่น ๆ</option>
    </select>
  </div>

  <button type="submit">บันทึกข้อมูล</button>
</form>
```

#### การใช้กับ Checkbox และ Radio

```html
<form action="/preferences" method="POST">
  <fieldset>
    <legend>ความสนใจ (เลือกได้หลายข้อ)</legend>

    <div class="checkbox-group">
      <input
        type="checkbox"
        id="interest-tech"
        name="interests"
        value="technology"
      />
      <label for="interest-tech">เทคโนโลยี</label>
    </div>

    <div class="checkbox-group">
      <input
        type="checkbox"
        id="interest-sports"
        name="interests"
        value="sports"
      />
      <label for="interest-sports">กีฬา</label>
    </div>

    <div class="checkbox-group">
      <input
        type="checkbox"
        id="interest-music"
        name="interests"
        value="music"
      />
      <label for="interest-music">ดนตรี</label>
    </div>
  </fieldset>

  <fieldset>
    <legend>ระดับการศึกษา (เลือกข้อใดข้อหนึ่ง)</legend>

    <div class="radio-group">
      <input type="radio" id="edu-high" name="education" value="high-school" />
      <label for="edu-high">มัธยมศึกษา</label>
    </div>

    <div class="radio-group">
      <input type="radio" id="edu-bachelor" name="education" value="bachelor" />
      <label for="edu-bachelor">ปริญญาตรี</label>
    </div>

    <div class="radio-group">
      <input type="radio" id="edu-master" name="education" value="master" />
      <label for="edu-master">ปริญญาโท</label>
    </div>

    <div class="radio-group">
      <input
        type="radio"
        id="edu-doctorate"
        name="education"
        value="doctorate"
      />
      <label for="edu-doctorate">ปริญญาเอก</label>
    </div>
  </fieldset>

  <button type="submit">บันทึกความสนใช</button>
</form>
```

### 2.5 เทคนิคขั้นสูงกับ Label

#### การใช้ Label กับ Textarea

```html
<div class="form-group">
  <label for="message">ข้อความ *</label>
  <textarea
    id="message"
    name="message"
    rows="5"
    cols="50"
    placeholder="กรุณาใส่ข้อความของท่าน..."
    required
  ></textarea>
</div>
```

#### การใช้ Label กับ File Input

```html
<div class="form-group">
  <label for="profile-picture">รูปโปรไฟล์</label>
  <input
    type="file"
    id="profile-picture"
    name="profilePicture"
    accept="image/*"
    multiple
  />
  <small>รองรับไฟล์: JPG, PNG, GIF (ขนาดไม่เกิน 5MB)</small>
</div>
```

#### การใช้ Label กับ Range Input

```html
<div class="form-group">
  <label for="age-range">ช่วงอายุ: <span id="age-display">25</span> ปี</label>
  <input
    type="range"
    id="age-range"
    name="age"
    min="18"
    max="65"
    value="25"
    oninput="document.getElementById('age-display').textContent = this.value"
  />
</div>
```

### 2.6 Best Practices สำหรับ Label

#### ✅ ควรทำ

```html
<!-- เชื่อมโยงที่ชัดเจน -->
<label for="email">อีเมล *</label>
<input type="email" id="email" name="email" required />

<!-- ใช้ข้อความที่ชัดเจน -->
<label for="phone">เบอร์โทรศัพท์ (10 หลัก)</label>
<input type="tel" id="phone" name="phone" pattern="[0-9]{10}" />

<!-- บอกข้อมูลที่จำเป็น -->
<label for="password">รหัสผ่าน * (อย่างน้อย 8 ตัวอักษร)</label>
<input type="password" id="password" name="password" minlength="8" required />
```

#### ❌ หลีกเลี่ยง

```html
<!-- ไม่มี for attribute -->
<label>ชื่อผู้ใช้</label>
<input type="text" id="username" name="username" />

<!-- id ไม่ตรงกับ for -->
<label for="user-name">ชื่อผู้ใช้</label>
<input type="text" id="username" name="username" />

<!-- Label ที่ไม่ชัดเจน -->
<label for="field1">ข้อมูล</label>
<input type="text" id="field1" name="field1" />
```

### 2.7 การจัดรูปแบบ Label ด้วย CSS

```css
/* Basic label styling */
label {
  display: block;
  font-weight: bold;
  margin-bottom: 5px;
  color: #333;
}

/* Required field indicator */
label.required::after {
  content: ' *';
  color: red;
}

/* Label for checkbox/radio */
.checkbox-group label,
.radio-group label {
  display: inline;
  font-weight: normal;
  margin-left: 8px;
  cursor: pointer;
}

/* Hover effect */
label:hover {
  color: #007bff;
}

/* Focus state when associated input is focused */
input:focus + label,
label:has(input:focus) {
  color: #007bff;
}
```

### 2.8 ตัวอย่างฟอร์มสมบูรณ์

```html
<form action="/contact" method="POST" class="contact-form">
  <h2>ติดต่อเรา</h2>

  <div class="form-row">
    <div class="form-group">
      <label for="contact-name" class="required">ชื่อ-นามสกุล</label>
      <input
        type="text"
        id="contact-name"
        name="fullName"
        placeholder="กรุณาใส่ชื่อ-นามสกุล"
        autocomplete="name"
        required
      />
    </div>

    <div class="form-group">
      <label for="contact-email" class="required">อีเมล</label>
      <input
        type="email"
        id="contact-email"
        name="email"
        placeholder="example@email.com"
        autocomplete="email"
        required
      />
    </div>
  </div>

  <div class="form-group">
    <label for="contact-phone">เบอร์โทรศัพท์</label>
    <input
      type="tel"
      id="contact-phone"
      name="phone"
      placeholder="08X-XXX-XXXX"
      autocomplete="tel"
    />
  </div>

  <div class="form-group">
    <label for="contact-subject" class="required">หัวข้อ</label>
    <select id="contact-subject" name="subject" required>
      <option value="">-- เลือกหัวข้อ --</option>
      <option value="general">สอบถามทั่วไป</option>
      <option value="support">ขอความช่วยเหลือ</option>
      <option value="feedback">ข้อเสนอแนะ</option>
      <option value="complaint">ร้องเรียน</option>
    </select>
  </div>

  <div class="form-group">
    <label for="contact-message" class="required">ข้อความ</label>
    <textarea
      id="contact-message"
      name="message"
      rows="6"
      placeholder="กรุณาใส่ข้อความของท่าน..."
      required
    ></textarea>
  </div>

  <div class="form-group">
    <label for="contact-file">แนบไฟล์ (ถ้ามี)</label>
    <input
      type="file"
      id="contact-file"
      name="attachment"
      accept=".pdf,.doc,.docx,.jpg,.png"
      multiple
    />
    <small>รองรับไฟล์: PDF, DOC, DOCX, JPG, PNG (ขนาดไม่เกิน 10MB)</small>
  </div>

  <div class="form-group">
    <div class="checkbox-group">
      <input
        type="checkbox"
        id="contact-newsletter"
        name="newsletter"
        value="yes"
      />
      <label for="contact-newsletter">ต้องการรับข่าวสารจากเรา</label>
    </div>
  </div>

  <div class="form-group">
    <div class="checkbox-group">
      <input
        type="checkbox"
        id="contact-agree"
        name="agree"
        value="yes"
        required
      />
      <label for="contact-agree" class="required">
        ยอมรับ <a href="/terms" target="_blank">เงื่อนไขการใช้งาน</a>
      </label>
    </div>
  </div>

  <div class="form-actions">
    <button type="reset">ล้างข้อมูล</button>
    <button type="submit">ส่งข้อความ</button>
  </div>
</form>
```

## 3. โครงสร้าง `<form>` Element

### Syntax พื้นฐาน

```html
<form action="URL" method="POST/GET" autocomplete="on/off" novalidate>
  <!-- Form Controls -->
</form>
```

### ตัวอย่างพื้นฐาน

```html
<form action="/submit-data" method="POST">
  <label for="username">ชื่อผู้ใช้:</label>
  <input type="text" id="username" name="username" required />

  <label for="email">อีเมล:</label>
  <input type="email" id="email" name="email" required />

  <button type="submit">ส่งข้อมูล</button>
</form>
```

## 3. Attributes สำคัญของ `<form>`

### 3.1 `action` Attribute

กำหนดปลายทางที่จะส่งข้อมูลไป

**Syntax:**

```html
<form action="URL"></form>
```

**ตัวอย่าง:**

```html
<!-- ส่งไปยัง URL เฉพาะ -->
<form action="https://example.com/process-form">
  <!-- controls -->
</form>

<!-- ส่งไปยังไฟล์ในเซิร์ฟเวอร์เดียวกัน -->
<form action="/api/submit">
  <!-- controls -->
</form>

<!-- ส่งไปยังหน้าเดียวกัน (ค่าเริ่มต้น) -->
<form action="">
  <!-- controls -->
</form>

<!-- ไม่ส่งไปไหน (ใช้ JavaScript จัดการ) -->
<form action="#" onsubmit="handleSubmit(event)">
  <!-- controls -->
</form>
```

**กรณีการใช้งาน:**

```html
<!-- ฟอร์มสมัครสมาชิก -->
<form action="/register" method="POST">
  <input type="text" name="username" placeholder="ชื่อผู้ใช้" />
  <input type="email" name="email" placeholder="อีเมล" />
  <input type="password" name="password" placeholder="รหัสผ่าน" />
  <button type="submit">สมัครสมาชิก</button>
</form>

<!-- ฟอร์มค้นหา -->
<form action="/search" method="GET">
  <input type="search" name="q" placeholder="ค้นหา..." />
  <button type="submit">ค้นหา</button>
</form>
```

### 3.2 `method` Attribute

กำหนดวิธีการส่งข้อมูล

**ค่าที่ใช้ได้:**

- `GET` (ค่าเริ่มต้น)
- `POST`
- `PUT`
- `DELETE`
- `PATCH`

#### GET Method

```html
<form action="/search" method="GET">
  <input type="text" name="keyword" placeholder="คำค้นหา" />
  <input type="text" name="category" placeholder="หมวดหมู่" />
  <button type="submit">ค้นหา</button>
</form>
```

**ลักษณะการส่งข้อมูล:**

- ข้อมูลแสดงใน URL: `/search?keyword=html&category=tutorial`
- จำกัดขนาดข้อมูล (~2048 characters)
- ข้อมูลมองเห็นได้ใน URL
- เหมาะสำหรับการค้นหา, การกรอง

#### POST Method

```html
<form action="/login" method="POST">
  <input type="email" name="email" placeholder="อีเมล" />
  <input type="password" name="password" placeholder="รหัสผ่าน" />
  <button type="submit">เข้าสู่ระบบ</button>
</form>
```

**ลักษณะการส่งข้อมูล:**

- ข้อมูลส่งใน Request Body
- ไม่จำกัดขนาดข้อมูล
- ข้อมูลไม่แสดงใน URL
- เหมาะสำหรับการส่งข้อมูลสำคัญ

#### เปรียบเทียบ GET vs POST

```html
<!-- GET - สำหรับดึงข้อมูล -->
<form method="GET" action="/products">
  <select name="sort">
    <option value="price">เรียงตามราคา</option>
    <option value="name">เรียงตามชื่อ</option>
  </select>
  <button type="submit">กรอง</button>
</form>

<!-- POST - สำหรับส่งข้อมูล -->
<form method="POST" action="/contact">
  <textarea name="message" placeholder="ข้อความ"></textarea>
  <input type="file" name="attachment" />
  <button type="submit">ส่งข้อความ</button>
</form>
```

### 3.3 `autocomplete` Attribute

ควบคุมการทำงานของ Browser Autocomplete

**ค่าที่ใช้ได้:**

- `on` (ค่าเริ่มต้น) - เปิดใช้งาน autocomplete
- `off` - ปิดใช้งาน autocomplete

#### การใช้ในระดับ Form

```html
<!-- ปิด autocomplete ทั้งฟอร์ม -->
<form action="/secure-form" method="POST" autocomplete="off">
  <input type="text" name="credit-card" placeholder="หมายเลขบัตรเครดิต" />
  <input type="text" name="cvv" placeholder="CVV" />
  <button type="submit">ชำระเงิน</button>
</form>

<!-- เปิด autocomplete (ค่าเริ่มต้น) -->
<form action="/profile" method="POST" autocomplete="on">
  <input type="text" name="name" placeholder="ชื่อ" />
  <input type="email" name="email" placeholder="อีเมล" />
  <button type="submit">บันทึก</button>
</form>
```

#### การใช้ในระดับ Input (ละเอียดกว่า)

```html
<form action="/checkout" method="POST">
  <!-- ใช้ autocomplete values เฉพาะ -->
  <input
    type="text"
    name="fname"
    autocomplete="given-name"
    placeholder="ชื่อ"
  />
  <input
    type="text"
    name="lname"
    autocomplete="family-name"
    placeholder="นามสกุล"
  />
  <input type="email" name="email" autocomplete="email" placeholder="อีเมล" />
  <input type="tel" name="phone" autocomplete="tel" placeholder="เบอร์โทร" />

  <!-- ข้อมูลที่อยู่ -->
  <input
    type="text"
    name="address"
    autocomplete="street-address"
    placeholder="ที่อยู่"
  />
  <input
    type="text"
    name="city"
    autocomplete="address-level2"
    placeholder="เมือง"
  />
  <input
    type="text"
    name="postal"
    autocomplete="postal-code"
    placeholder="รหัสไปรษณีย์"
  />

  <!-- ข้อมูลการชำระเงิน -->
  <input
    type="text"
    name="cc-name"
    autocomplete="cc-name"
    placeholder="ชื่อบนบัตร"
  />
  <input
    type="text"
    name="cc-number"
    autocomplete="cc-number"
    placeholder="หมายเลขบัตร"
  />
  <input type="text" name="cc-exp" autocomplete="cc-exp" placeholder="MM/YY" />

  <button type="submit">ส่งคำสั่งซื้อ</button>
</form>
```

**ค่า autocomplete ที่ใช้บ่อย:**

- `name`, `given-name`, `family-name`
- `email`, `tel`, `url`
- `street-address`, `address-level1`, `address-level2`, `postal-code`
- `cc-name`, `cc-number`, `cc-exp`, `cc-csc`
- `username`, `current-password`, `new-password`

### 3.4 `novalidate` Attribute

ปิดการตรวจสอบข้อมูลของ Browser

```html
<!-- ฟอร์มปกติ - มีการตรวจสอบ -->
<form action="/submit" method="POST">
  <input type="email" name="email" required placeholder="อีเมล" />
  <input type="url" name="website" placeholder="เว็บไซต์" />
  <button type="submit">ส่ง</button>
</form>

<!-- ฟอร์มที่ปิดการตรวจสอบ -->
<form action="/submit" method="POST" novalidate>
  <input type="email" name="email" required placeholder="อีเมล" />
  <input type="url" name="website" placeholder="เว็บไซต์" />
  <button type="submit">ส่ง (ไม่ตรวจสอบ)</button>
</form>
```

**กรณีการใช้งาน novalidate:**

```html
<!-- ฟอร์มที่ใช้ Custom Validation -->
<form action="/custom-validate" method="POST" novalidate id="customForm">
  <div class="field">
    <input type="email" name="email" id="email" required />
    <span class="error-message" id="email-error"></span>
  </div>

  <div class="field">
    <input type="password" name="password" id="password" required />
    <span class="error-message" id="password-error"></span>
  </div>

  <button type="submit">เข้าสู่ระบบ</button>
</form>

<script>
  document
    .getElementById('customForm')
    .addEventListener('submit', function (e) {
      e.preventDefault();
      // Custom validation logic
      validateForm();
    });
</script>
```

## 4. ตัวอย่างแบบครบครัน

### ฟอร์มสมัครสมาชิก

```html
<form
  action="/register"
  method="POST"
  autocomplete="on"
  class="registration-form"
>
  <fieldset>
    <legend>ข้อมูลส่วนตัว</legend>

    <div class="form-group">
      <label for="firstName">ชื่อ *</label>
      <input
        type="text"
        id="firstName"
        name="firstName"
        autocomplete="given-name"
        required
      />
    </div>

    <div class="form-group">
      <label for="lastName">นามสกุล *</label>
      <input
        type="text"
        id="lastName"
        name="lastName"
        autocomplete="family-name"
        required
      />
    </div>

    <div class="form-group">
      <label for="email">อีเมล *</label>
      <input
        type="email"
        id="email"
        name="email"
        autocomplete="email"
        required
      />
    </div>

    <div class="form-group">
      <label for="phone">เบอร์โทรศัพท์</label>
      <input type="tel" id="phone" name="phone" autocomplete="tel" />
    </div>
  </fieldset>

  <fieldset>
    <legend>ข้อมูลบัญชี</legend>

    <div class="form-group">
      <label for="username">ชื่อผู้ใช้ *</label>
      <input
        type="text"
        id="username"
        name="username"
        autocomplete="username"
        required
      />
    </div>

    <div class="form-group">
      <label for="password">รหัสผ่าน *</label>
      <input
        type="password"
        id="password"
        name="password"
        autocomplete="new-password"
        required
      />
    </div>

    <div class="form-group">
      <label for="confirmPassword">ยืนยันรหัสผ่าน *</label>
      <input
        type="password"
        id="confirmPassword"
        name="confirmPassword"
        autocomplete="new-password"
        required
      />
    </div>
  </fieldset>

  <div class="form-actions">
    <button type="reset">ล้างข้อมูล</button>
    <button type="submit">สมัครสมาชิก</button>
  </div>
</form>
```

### ฟอร์มค้นหาขั้นสูง

```html
<form action="/search" method="GET" class="search-form">
  <div class="search-main">
    <label for="query">คำค้นหา</label>
    <input
      type="search"
      id="query"
      name="q"
      placeholder="ใส่คำที่ต้องการค้นหา..."
      autocomplete="off"
    />
  </div>

  <details class="advanced-options">
    <summary>ตัวเลือกขั้นสูง</summary>

    <div class="form-row">
      <div class="form-group">
        <label for="category">หมวดหมู่</label>
        <select id="category" name="category">
          <option value="">ทั้งหมด</option>
          <option value="electronics">อิเล็กทรอนิกส์</option>
          <option value="books">หังสือ</option>
          <option value="clothing">เสื้อผ้า</option>
        </select>
      </div>

      <div class="form-group">
        <label for="sort">เรียงลำดับ</label>
        <select id="sort" name="sort">
          <option value="relevance">ความเกี่ยวข้อง</option>
          <option value="price-low">ราคาต่ำ-สูง</option>
          <option value="price-high">ราคาสูง-ต่ำ</option>
          <option value="newest">ใหม่ล่าสุด</option>
        </select>
      </div>
    </div>

    <div class="form-row">
      <div class="form-group">
        <label for="min-price">ราคาต่ำสุด</label>
        <input type="number" id="min-price" name="min_price" min="0" step="1" />
      </div>

      <div class="form-group">
        <label for="max-price">ราคาสูงสุด</label>
        <input type="number" id="max-price" name="max_price" min="0" step="1" />
      </div>
    </div>
  </details>

  <button type="submit">ค้นหา</button>
</form>
```

## 5. Best Practices

### 5.1 การเลือกใช้ Method

```html
<!-- ✅ ใช้ GET สำหรับการค้นหา/กรอง -->
<form method="GET" action="/products">
  <input type="search" name="q" />
  <select name="category"></select>
</form>

<!-- ✅ ใช้ POST สำหรับส่งข้อมูล -->
<form method="POST" action="/contact">
  <textarea name="message"></textarea>
  <input type="file" name="attachment" />
</form>

<!-- ❌ หลีกเลี่ยง GET กับข้อมูลสำคัญ -->
<form method="GET" action="/login">
  <input type="password" name="password" />
  <!-- ปรากฏใน URL! -->
</form>
```

### 5.2 การใช้ Autocomplete อย่างเหมาะสม

```html
<!-- ✅ เปิด autocomplete สำหรับข้อมูลทั่วไป -->
<form autocomplete="on">
  <input type="text" name="name" autocomplete="name" />
  <input type="email" name="email" autocomplete="email" />
</form>

<!-- ✅ ปิด autocomplete สำหรับข้อมูลสำคัญ -->
<form autocomplete="off">
  <input type="text" name="credit-card" />
  <input type="text" name="ssn" />
</form>
```

### 5.3 การจัดการ Validation

```html
<!-- ✅ ใช้ built-in validation -->
<form action="/submit" method="POST">
  <input type="email" required />
  <input type="url" />
  <button type="submit">ส่ง</button>
</form>

<!-- ✅ ใช้ custom validation -->
<form action="/submit" method="POST" novalidate>
  <input type="email" id="email" required />
  <button type="submit">ส่ง</button>
</form>
```

---

**สรุป**: การเข้าใจและใช้ attributes ของ `<form>` อย่างถูกต้องจะช่วยให้สร้างฟอร์มที่มีประสิทธิภาพ ปลอดภัย และใช้งานง่าย
