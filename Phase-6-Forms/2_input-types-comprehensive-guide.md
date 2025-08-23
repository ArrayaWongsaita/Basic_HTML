# ช่องกรอกข้อมูล: `<input>` Element และ Types ต่างๆ

## 1. ภาพรวม `<input>` Element

`<input>` เป็น element หลักสำหรับรับข้อมูลจากผู้ใช้ในฟอร์ม มีหลากหลาย type ที่เหมาะกับข้อมูลประเภทต่างๆ

**Syntax พื้นฐาน:**

```html
<input type="type" name="name" id="id" attributes... />
```

**Attributes พื้นฐาน:**

- `type`: ประเภทของ input
- `name`: ชื่อสำหรับส่งข้อมูล
- `id`: ใช้เชื่อมโยงกับ label
- `value`: ค่าเริ่มต้น
- `placeholder`: ข้อความแนะนำ
- `required`: บังคับกรอก
- `disabled`: ปิดการใช้งาน
- `readonly`: อ่านได้อย่างเดียว

## 2. Input Types แบบละเอียด

### 2.1 `type="text"` - ข้อความทั่วไป

**การใช้งาน:** รับข้อความทั่วไป เช่น ชื่อ, ที่อยู่, คำอธิบาย

```html
<div class="form-group">
  <label for="fullname">ชื่อ-นามสกุล *</label>
  <input
    type="text"
    id="fullname"
    name="fullname"
    placeholder="กรุณาใส่ชื่อ-นามสกุล"
    maxlength="100"
    autocomplete="name"
    required
  />
</div>

<div class="form-group">
  <label for="company">ชื่อบริษัท</label>
  <input
    type="text"
    id="company"
    name="company"
    placeholder="ชื่อบริษัท (ถ้ามี)"
    autocomplete="organization"
  />
</div>
```

**Attributes เฉพาะ:**

- `maxlength`: จำกัดจำนวนตัวอักษร
- `minlength`: ความยาวต่ำสุด
- `pattern`: รูปแบบที่ต้องการ (Regular Expression)
- `size`: ขนาดของ input box

```html
<!-- ตัวอย่างการใช้ pattern -->
<label for="student-id">รหัสนักเรียน (6 หลัก)</label>
<input
  type="text"
  id="student-id"
  name="studentId"
  pattern="[0-9]{6}"
  placeholder="123456"
  title="รหัสนักเรียน 6 หลัก"
  required
/>
```

### 2.2 `type="email"` - อีเมล

**การใช้งาน:** รับอีเมลแอดเดรส มีการตรวจสอบรูปแบบอัตโนมัติ

```html
<div class="form-group">
  <label for="email">อีเมล *</label>
  <input
    type="email"
    id="email"
    name="email"
    placeholder="example@email.com"
    autocomplete="email"
    required
  />
</div>

<!-- รองรับหลายอีเมล -->
<div class="form-group">
  <label for="cc-emails">อีเมลผู้รับสำเนา</label>
  <input
    type="email"
    id="cc-emails"
    name="ccEmails"
    placeholder="email1@domain.com, email2@domain.com"
    multiple
  />
</div>
```

**Attributes เฉพาะ:**

- `multiple`: รับหลายอีเมล (คั่นด้วยเครื่องหมายจุลภาค)

### 2.3 `type="password"` - รหัสผ่าน

**การใช้งาน:** รับรหัสผ่าน ข้อความจะถูกซ่อน

```html
<div class="form-group">
  <label for="password">รหัสผ่าน *</label>
  <input
    type="password"
    id="password"
    name="password"
    placeholder="อย่างน้อย 8 ตัวอักษร"
    minlength="8"
    autocomplete="current-password"
    required
  />
</div>

<div class="form-group">
  <label for="new-password">รหัสผ่านใหม่ *</label>
  <input
    type="password"
    id="new-password"
    name="newPassword"
    minlength="8"
    pattern="^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[a-zA-Z\d@$!%*?&]{8,}$"
    title="รหัสผ่านต้องมีตัวพิมพ์เล็ก พิมพ์ใหญ่ และตัวเลข อย่างน้อย 8 ตัวอักษร"
    autocomplete="new-password"
    required
  />
</div>
```

**เทคนิคเพิ่มเติม:**

```html
<!-- ปุ่มแสดง/ซ่อนรหัสผ่าน -->
<div class="password-field">
  <input type="password" id="pwd" name="password" required />
  <button
    type="button"
    onclick="togglePassword()"
    aria-label="แสดง/ซ่อนรหัสผ่าน"
  >
    👁️
  </button>
</div>

<script>
  function togglePassword() {
    const passwordField = document.getElementById('pwd');
    const type = passwordField.type === 'password' ? 'text' : 'password';
    passwordField.type = type;
  }
</script>
```

### 2.4 `type="number"` - ตัวเลข

**การใช้งาน:** รับค่าตัวเลข มีปุ่มเพิ่ม/ลดค่า

```html
<div class="form-group">
  <label for="age">อายุ</label>
  <input
    type="number"
    id="age"
    name="age"
    min="1"
    max="120"
    step="1"
    placeholder="25"
  />
</div>

<div class="form-group">
  <label for="price">ราคา (บาท)</label>
  <input
    type="number"
    id="price"
    name="price"
    min="0"
    step="0.01"
    placeholder="0.00"
  />
</div>

<div class="form-group">
  <label for="quantity">จำนวน</label>
  <input
    type="number"
    id="quantity"
    name="quantity"
    min="1"
    max="999"
    value="1"
    required
  />
</div>
```

**Attributes เฉพาะ:**

- `min`: ค่าต่ำสุด
- `max`: ค่าสูงสุด
- `step`: ขั้นของการเพิ่ม/ลด

### 2.5 `type="date"` - วันที่

**การใช้งาน:** เลือกวันที่ แสดง Date Picker

```html
<div class="form-group">
  <label for="birth-date">วันเกิด</label>
  <input
    type="date"
    id="birth-date"
    name="birthDate"
    min="1900-01-01"
    max="2024-12-31"
    autocomplete="bday"
  />
</div>

<div class="form-group">
  <label for="event-date">วันที่จัดงาน *</label>
  <input
    type="date"
    id="event-date"
    name="eventDate"
    min="2024-01-01"
    required
  />
</div>
```

**Input Types วันที่อื่นๆ:**

```html
<!-- เวลา -->
<label for="meeting-time">เวลาประชุม</label>
<input
  type="time"
  id="meeting-time"
  name="meetingTime"
  min="09:00"
  max="18:00"
/>

<!-- วันที่และเวลา -->
<label for="appointment">นัดหมาย</label>
<input type="datetime-local" id="appointment" name="appointment" />

<!-- เดือน -->
<label for="start-month">เดือนเริ่มต้น</label>
<input type="month" id="start-month" name="startMonth" />

<!-- สัปดาห์ -->
<label for="week">สัปดาห์</label>
<input type="week" id="week" name="week" />
```

### 2.6 `type="file"` - อัปโหลดไฟล์

**การใช้งาน:** เลือกและอัปโหลดไฟล์

```html
<div class="form-group">
  <label for="profile-pic">รูปโปรไฟล์</label>
  <input
    type="file"
    id="profile-pic"
    name="profilePicture"
    accept="image/*"
    capture="user"
  />
  <small>รองรับ: JPG, PNG, GIF (ไม่เกิน 5MB)</small>
</div>

<div class="form-group">
  <label for="documents">เอกสารประกอบ</label>
  <input
    type="file"
    id="documents"
    name="documents"
    accept=".pdf,.doc,.docx"
    multiple
  />
</div>

<div class="form-group">
  <label for="video">วิดีโอ</label>
  <input
    type="file"
    id="video"
    name="video"
    accept="video/*"
    capture="environment"
  />
</div>
```

**Attributes เฉพาะ:**

- `accept`: ประเภทไฟล์ที่รับ
- `multiple`: เลือกหลายไฟล์
- `capture`: ใช้กล้อง/ไมโครโฟน

**ตัวอย่าง JavaScript การจัดการไฟล์:**

```html
<input
  type="file"
  id="file-input"
  onchange="handleFileSelect(event)"
  multiple
/>
<div id="file-list"></div>

<script>
  function handleFileSelect(event) {
    const files = event.target.files;
    const fileList = document.getElementById('file-list');

    fileList.innerHTML = '';

    for (let i = 0; i < files.length; i++) {
      const file = files[i];
      const div = document.createElement('div');
      div.innerHTML = `
      <p>ชื่อไฟล์: ${file.name}</p>
      <p>ขนาด: ${(file.size / 1024 / 1024).toFixed(2)} MB</p>
      <p>ประเภท: ${file.type}</p>
    `;
      fileList.appendChild(div);
    }
  }
</script>
```

### 2.7 `type="checkbox"` - ช่องเลือก

**การใช้งาน:** เลือกได้หลายตัวเลือก

```html
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
      checked
    />
    <label for="interest-music">ดนตรี</label>
  </div>
</fieldset>

<!-- เงื่อนไขการใช้งาน -->
<div class="checkbox-group">
  <input type="checkbox" id="terms" name="agreeTerms" value="yes" required />
  <label for="terms"> ยอมรับ <a href="/terms">เงื่อนไขการใช้งาน</a> * </label>
</div>
```

**JavaScript สำหรับ Checkbox:**

```html
<div class="checkbox-actions">
  <button type="button" onclick="selectAll()">เลือกทั้งหมด</button>
  <button type="button" onclick="selectNone()">ไม่เลือกทั้งหมด</button>
</div>

<script>
  function selectAll() {
    const checkboxes = document.querySelectorAll('input[name="interests"]');
    checkboxes.forEach((cb) => (cb.checked = true));
  }

  function selectNone() {
    const checkboxes = document.querySelectorAll('input[name="interests"]');
    checkboxes.forEach((cb) => (cb.checked = false));
  }
</script>
```

### 2.8 `type="radio"` - ปุ่มวิทยุ

**การใช้งาน:** เลือกได้เพียงตัวเลือกเดียวต่อกลุ่ม

```html
<fieldset>
  <legend>เพศ *</legend>

  <div class="radio-group">
    <input type="radio" id="gender-male" name="gender" value="male" required />
    <label for="gender-male">ชาย</label>
  </div>

  <div class="radio-group">
    <input
      type="radio"
      id="gender-female"
      name="gender"
      value="female"
      required
    />
    <label for="gender-female">หญิง</label>
  </div>

  <div class="radio-group">
    <input
      type="radio"
      id="gender-other"
      name="gender"
      value="other"
      required
    />
    <label for="gender-other">อื่นๆ</label>
  </div>
</fieldset>

<fieldset>
  <legend>ระดับความพึงพอใจ</legend>

  <div class="radio-group">
    <input type="radio" id="satisfaction-1" name="satisfaction" value="1" />
    <label for="satisfaction-1">😞 ไม่พึงพอใจมาก</label>
  </div>

  <div class="radio-group">
    <input type="radio" id="satisfaction-2" name="satisfaction" value="2" />
    <label for="satisfaction-2">😐 ไม่พึงพอใจ</label>
  </div>

  <div class="radio-group">
    <input
      type="radio"
      id="satisfaction-3"
      name="satisfaction"
      value="3"
      checked
    />
    <label for="satisfaction-3">😊 พึงพอใจ</label>
  </div>

  <div class="radio-group">
    <input type="radio" id="satisfaction-4" name="satisfaction" value="4" />
    <label for="satisfaction-4">😁 พึงพอใจมาก</label>
  </div>
</fieldset>
```

### 2.9 `type="hidden"` - ข้อมูลซ่อน

**การใช้งาน:** ส่งข้อมูลที่ไม่ต้องการให้ผู้ใช้เห็นหรือแก้ไข

```html
<form action="/submit" method="POST">
  <!-- ข้อมูลที่ผู้ใช้เห็น -->
  <label for="username">ชื่อผู้ใช้</label>
  <input type="text" id="username" name="username" required />

  <!-- ข้อมูลซ่อน -->
  <input type="hidden" name="userId" value="12345" />
  <input type="hidden" name="formVersion" value="2.1" />
  <input type="hidden" name="timestamp" value="" />
  <input type="hidden" name="csrfToken" value="abc123xyz" />

  <button type="submit">ส่งข้อมูล</button>
</form>

<script>
  // ตั้งค่า timestamp เมื่อโหลดหน้า
  document.querySelector('input[name="timestamp"]').value =
    new Date().toISOString();
</script>
```

### 2.10 `type="submit"` - ปุ่มส่งข้อมูล

**การใช้งาน:** ปุ่มสำหรับส่งฟอร์ม

```html
<!-- ปุ่มส่งพื้นฐาน -->
<input type="submit" value="ส่งข้อมูล" />

<!-- ปุ่มส่งแบบกำหนดเอง -->
<input
  type="submit"
  value="สมัครสมาชิก"
  class="btn btn-primary"
  formaction="/register"
  formmethod="POST"
/>

<!-- ปุ่มส่งหลายแบบ -->
<form action="/post" method="POST">
  <textarea name="content" placeholder="เขียนโพสต์..."></textarea>

  <input type="submit" value="บันทึกร่าง" formaction="/save-draft" />
  <input type="submit" value="เผยแพร่" formaction="/publish" />
  <input type="submit" value="ตั้งเวลาเผยแพร่" formaction="/schedule" />
</form>
```

**Attributes เฉพาะ:**

- `formaction`: เปลี่ยน action ของฟอร์ม
- `formmethod`: เปลี่ยน method ของฟอร์ม
- `formnovalidate`: ข้าม validation
- `formtarget`: เปลี่ยน target

### 2.11 `type="search"` - ค้นหา

**การใช้งาน:** สำหรับการค้นหา มีปุ่มล้างข้อมูลใน browser บางตัว

```html
<form action="/search" method="GET" class="search-form">
  <div class="search-box">
    <label for="search-query" class="sr-only">ค้นหา</label>
    <input
      type="search"
      id="search-query"
      name="q"
      placeholder="ค้นหาสินค้า, บทความ, หรือบริการ..."
      autocomplete="off"
      results="5"
      autosave="search-history"
    />
    <button type="submit">🔍</button>
  </div>

  <!-- ตัวกรองการค้นหา -->
  <div class="search-filters">
    <input
      type="search"
      name="category"
      placeholder="หมวดหมู่"
      list="categories"
    />
    <datalist id="categories">
      <option value="อิเล็กทรอนิกส์"></option>
      <option value="เสื้อผ้า"></option>
      <option value="อาหาร"></option>
      <option value="หนังสือ"></option>
    </datalist>
  </div>
</form>
```

### 2.12 `type="url"` - URL

**การใช้งาน:** รับลิงก์ URL มีการตรวจสอบรูปแบบ

```html
<div class="form-group">
  <label for="website">เว็บไซต์</label>
  <input
    type="url"
    id="website"
    name="website"
    placeholder="https://example.com"
    pattern="https://.*"
    title="URL ต้องขึ้นต้นด้วย https://"
  />
</div>

<div class="form-group">
  <label for="social-links">โซเชียลมีเดีย</label>
  <input
    type="url"
    id="facebook"
    name="facebook"
    placeholder="https://facebook.com/username"
  />
  <input
    type="url"
    id="twitter"
    name="twitter"
    placeholder="https://twitter.com/username"
  />
  <input
    type="url"
    id="linkedin"
    name="linkedin"
    placeholder="https://linkedin.com/in/username"
  />
</div>
```

### 2.13 `type="range"` - ช่วงค่า

**การใช้งาน:** เลือกค่าจากช่วงที่กำหนด แสดงเป็น slider

```html
<div class="form-group">
  <label for="volume">ระดับเสียง: <span id="volume-value">50</span>%</label>
  <input
    type="range"
    id="volume"
    name="volume"
    min="0"
    max="100"
    value="50"
    step="5"
    oninput="updateVolumeDisplay(this.value)"
  />
</div>

<div class="form-group">
  <label for="price-range"
    >ช่วงราคา: <span id="price-display">500-5000</span> บาท</label
  >
  <input
    type="range"
    id="price-min"
    name="priceMin"
    min="0"
    max="10000"
    value="500"
    step="100"
    oninput="updatePriceRange()"
  />
  <input
    type="range"
    id="price-max"
    name="priceMax"
    min="0"
    max="10000"
    value="5000"
    step="100"
    oninput="updatePriceRange()"
  />
</div>

<div class="form-group">
  <label for="rating">คะแนน: <span id="rating-text">3</span> ⭐</label>
  <input
    type="range"
    id="rating"
    name="rating"
    min="1"
    max="5"
    value="3"
    oninput="updateRating(this.value)"
  />
</div>

<script>
  function updateVolumeDisplay(value) {
    document.getElementById('volume-value').textContent = value;
  }

  function updatePriceRange() {
    const min = document.getElementById('price-min').value;
    const max = document.getElementById('price-max').value;
    document.getElementById('price-display').textContent = `${min}-${max}`;
  }

  function updateRating(value) {
    const stars = '⭐'.repeat(value);
    document.getElementById('rating-text').textContent = value;
  }
</script>
```

### 2.14 `type="color"` - เลือกสี

**การใช้งาน:** เลือกสี แสดง Color Picker

```html
<div class="form-group">
  <label for="favorite-color">สีที่ชอบ</label>
  <input
    type="color"
    id="favorite-color"
    name="favoriteColor"
    value="#ff0000"
  />
</div>

<div class="form-group">
  <label for="theme-color">สีธีม</label>
  <input
    type="color"
    id="theme-color"
    name="themeColor"
    value="#007bff"
    onchange="updateTheme(this.value)"
  />
</div>

<!-- ตัวอย่างการใช้กับ CSS Variables -->
<div class="color-customizer">
  <h3>กำหนดสีเว็บไซต์</h3>

  <div class="color-option">
    <label for="primary-color">สีหลัก</label>
    <input
      type="color"
      id="primary-color"
      value="#007bff"
      onchange="setCSSVariable('--primary-color', this.value)"
    />
  </div>

  <div class="color-option">
    <label for="secondary-color">สีรอง</label>
    <input
      type="color"
      id="secondary-color"
      value="#6c757d"
      onchange="setCSSVariable('--secondary-color', this.value)"
    />
  </div>

  <div class="color-option">
    <label for="background-color">สีพื้นหลัง</label>
    <input
      type="color"
      id="background-color"
      value="#f8f9fa"
      onchange="setCSSVariable('--bg-color', this.value)"
    />
  </div>
</div>

<script>
  function setCSSVariable(property, value) {
    document.documentElement.style.setProperty(property, value);
  }

  function updateTheme(color) {
    // เปลี่ยนธีมตามสีที่เลือก
    document.body.style.accentColor = color;
  }
</script>
```

## 3. Attributes ทั่วไปสำหรับ Input

### 3.1 Validation Attributes

```html
<!-- required - บังคับกรอก -->
<input type="text" name="name" required />

<!-- pattern - รูปแบบที่ต้องการ -->
<input type="text" name="phone" pattern="[0-9]{10}" title="เบอร์โทร 10 หลัก" />

<!-- min/max - ค่าต่ำสุด/สูงสุด -->
<input type="number" name="age" min="18" max="99" />

<!-- minlength/maxlength - ความยาวข้อความ -->
<input type="text" name="username" minlength="3" maxlength="20" />

<!-- step - ขั้นของตัวเลข -->
<input type="number" name="price" step="0.01" />
```

### 3.2 Accessibility Attributes

```html
<!-- aria-label - คำอธิบายสำหรับ screen reader -->
<input type="search" aria-label="ค้นหาในเว็บไซต์" />

<!-- aria-describedby - อ้างอิงคำอธิบายเพิ่มเติม -->
<input type="password" aria-describedby="pwd-help" />
<div id="pwd-help">รหัสผ่านต้องมีอย่างน้อย 8 ตัวอักษร</div>

<!-- title - tooltip -->
<input type="text" title="กรุณาใส่ชื่อจริงของท่าน" />
```

### 3.3 Form Attributes

```html
<!-- form - เชื่อมโยงกับฟอร์มที่ไม่ได้อยู่ใน -->
<input type="text" name="external" form="my-form" />

<!-- formaction - เปลี่ยน action เฉพาะ input -->
<input type="submit" value="บันทึก" formaction="/save" />

<!-- formmethod - เปลี่ยน method เฉพาะ input -->
<input type="submit" value="ลบ" formmethod="DELETE" />
```

## 4. ตัวอย่างฟอร์มครบครัน

```html
<form
  action="/submit-application"
  method="POST"
  enctype="multipart/form-data"
  class="application-form"
>
  <h2>ใบสมัครงาน</h2>

  <!-- ข้อมูลส่วนตัว -->
  <fieldset>
    <legend>ข้อมูลส่วนตัว</legend>

    <div class="form-row">
      <div class="form-group">
        <label for="first-name">ชื่อ *</label>
        <input
          type="text"
          id="first-name"
          name="firstName"
          required
          autocomplete="given-name"
        />
      </div>

      <div class="form-group">
        <label for="last-name">นามสกุล *</label>
        <input
          type="text"
          id="last-name"
          name="lastName"
          required
          autocomplete="family-name"
        />
      </div>
    </div>

    <div class="form-group">
      <label for="email">อีเมล *</label>
      <input
        type="email"
        id="email"
        name="email"
        required
        autocomplete="email"
      />
    </div>

    <div class="form-group">
      <label for="phone">เบอร์โทรศัพท์ *</label>
      <input
        type="tel"
        id="phone"
        name="phone"
        pattern="[0-9]{10}"
        title="เบอร์โทร 10 หลัก"
        required
        autocomplete="tel"
      />
    </div>

    <div class="form-row">
      <div class="form-group">
        <label for="birth-date">วันเกิด</label>
        <input
          type="date"
          id="birth-date"
          name="birthDate"
          max="2006-12-31"
          autocomplete="bday"
        />
      </div>

      <div class="form-group">
        <label for="age">อายุ</label>
        <input type="number" id="age" name="age" min="18" max="65" />
      </div>
    </div>

    <fieldset class="gender-fieldset">
      <legend>เพศ</legend>
      <div class="radio-group">
        <input type="radio" id="male" name="gender" value="male" />
        <label for="male">ชาย</label>
      </div>
      <div class="radio-group">
        <input type="radio" id="female" name="gender" value="female" />
        <label for="female">หญิง</label>
      </div>
    </fieldset>
  </fieldset>

  <!-- ข้อมูลการศึกษา -->
  <fieldset>
    <legend>ข้อมูลการศึกษา</legend>

    <div class="form-group">
      <label for="university">มหาวิทยาลัย</label>
      <input
        type="text"
        id="university"
        name="university"
        autocomplete="organization"
      />
    </div>

    <div class="form-row">
      <div class="form-group">
        <label for="gpa">เกรดเฉลี่ย</label>
        <input
          type="number"
          id="gpa"
          name="gpa"
          min="0"
          max="4"
          step="0.01"
          placeholder="3.50"
        />
      </div>

      <div class="form-group">
        <label for="graduation-year">ปีที่จบ</label>
        <input
          type="number"
          id="graduation-year"
          name="graduationYear"
          min="1990"
          max="2024"
        />
      </div>
    </div>
  </fieldset>

  <!-- ทักษะและความสามารถ -->
  <fieldset>
    <legend>ทักษะและความสามารถ</legend>

    <div class="form-group">
      <label>ทักษะด้านคอมพิวเตอร์ (เลือกได้หลายข้อ)</label>
      <div class="checkbox-grid">
        <div class="checkbox-group">
          <input type="checkbox" id="skill-html" name="skills" value="html" />
          <label for="skill-html">HTML/CSS</label>
        </div>
        <div class="checkbox-group">
          <input
            type="checkbox"
            id="skill-js"
            name="skills"
            value="javascript"
          />
          <label for="skill-js">JavaScript</label>
        </div>
        <div class="checkbox-group">
          <input
            type="checkbox"
            id="skill-python"
            name="skills"
            value="python"
          />
          <label for="skill-python">Python</label>
        </div>
        <div class="checkbox-group">
          <input type="checkbox" id="skill-java" name="skills" value="java" />
          <label for="skill-java">Java</label>
        </div>
      </div>
    </div>

    <div class="form-group">
      <label for="english-level"
        >ระดับภาษาอังกฤษ: <span id="english-display">3</span>/5</label
      >
      <input
        type="range"
        id="english-level"
        name="englishLevel"
        min="1"
        max="5"
        value="3"
        oninput="document.getElementById('english-display').textContent = this.value"
      />
    </div>
  </fieldset>

  <!-- ไฟล์แนบ -->
  <fieldset>
    <legend>เอกสารประกอบ</legend>

    <div class="form-group">
      <label for="resume">ไฟล์เรซูเม่ *</label>
      <input
        type="file"
        id="resume"
        name="resume"
        accept=".pdf,.doc,.docx"
        required
      />
    </div>

    <div class="form-group">
      <label for="portfolio">ผลงาน (ถ้ามี)</label>
      <input
        type="file"
        id="portfolio"
        name="portfolio"
        accept=".pdf,.zip"
        multiple
      />
    </div>

    <div class="form-group">
      <label for="photo">รูปถ่าย</label>
      <input type="file" id="photo" name="photo" accept="image/*" />
    </div>
  </fieldset>

  <!-- ข้อมูลเพิ่มเติม -->
  <fieldset>
    <legend>ข้อมูลเพิ่มเติม</legend>

    <div class="form-group">
      <label for="website">เว็บไซต์/Portfolio</label>
      <input
        type="url"
        id="website"
        name="website"
        placeholder="https://yourportfolio.com"
      />
    </div>

    <div class="form-group">
      <label for="expected-salary">เงินเดือนที่คาดหวัง (บาท)</label>
      <input
        type="number"
        id="expected-salary"
        name="expectedSalary"
        min="0"
        step="1000"
      />
    </div>

    <div class="form-group">
      <label for="start-date">วันที่สามารถเริ่มงานได้</label>
      <input type="date" id="start-date" name="startDate" min="2024-01-01" />
    </div>
  </fieldset>

  <!-- การยืนยัน -->
  <div class="form-group">
    <div class="checkbox-group">
      <input
        type="checkbox"
        id="confirm-info"
        name="confirmInfo"
        value="yes"
        required
      />
      <label for="confirm-info"
        >ข้าพเจ้ายืนยันว่าข้อมูลที่ให้ไว้ข้างต้นเป็นความจริง *</label
      >
    </div>
  </div>

  <div class="form-group">
    <div class="checkbox-group">
      <input type="checkbox" id="newsletter" name="newsletter" value="yes" />
      <label for="newsletter">ต้องการรับข่าวสารจากบริษัท</label>
    </div>
  </div>

  <!-- ข้อมูลซ่อน -->
  <input type="hidden" name="source" value="website" />
  <input type="hidden" name="position" value="developer" />
  <input type="hidden" name="timestamp" value="" />

  <!-- ปุ่มส่ง -->
  <div class="form-actions">
    <input type="reset" value="ล้างข้อมูล" class="btn btn-secondary" />
    <input type="submit" value="ส่งใบสมัคร" class="btn btn-primary" />
  </div>
</form>

<script>
  // ตั้งค่า timestamp
  document.querySelector('input[name="timestamp"]').value =
    new Date().toISOString();

  // คำนวณอายุจากวันเกิด
  document.getElementById('birth-date').addEventListener('change', function () {
    const birthDate = new Date(this.value);
    const today = new Date();
    const age = Math.floor(
      (today - birthDate) / (365.25 * 24 * 60 * 60 * 1000)
    );
    document.getElementById('age').value = age;
  });
</script>
```

## 5. Best Practices

### 5.1 การเลือกใช้ Input Type

```html
<!-- ✅ ใช้ type ที่เหมาะสม -->
<input type="email" name="email" />
<!-- สำหรับอีเมล -->
<input type="tel" name="phone" />
<!-- สำหรับเบอร์โทร -->
<input type="url" name="website" />
<!-- สำหรับ URL -->
<input type="number" name="age" />
<!-- สำหรับตัวเลข -->

<!-- ❌ หลีกเลี่ยง type="text" สำหรับทุกอย่าง -->
<input type="text" name="email" />
<!-- ไม่มี validation -->
<input type="text" name="phone" />
<!-- ไม่มี keyboard ที่เหมาะสม -->
```

### 5.2 การใช้ Placeholder และ Label

```html
<!-- ✅ ใช้ทั้ง label และ placeholder -->
<label for="email">อีเมล *</label>
<input type="email" id="email" placeholder="example@email.com" required />

<!-- ❌ ใช้แค่ placeholder -->
<input type="email" placeholder="อีเมล *" required />
```

### 5.3 การจัดกลุ่มและ Validation

```html
<!-- ✅ จัดกลุ่มและมี validation ที่ชัดเจน -->
<fieldset>
  <legend>ข้อมูลการติดต่อ</legend>
  <input type="email" name="email" required aria-describedby="email-help" />
  <div id="email-help">เราจะใช้อีเมลนี้ติดต่อท่าน</div>
</fieldset>
```

---

**สรุป**: การเลือกใช้ input type ที่เหมาะสมจะช่วยให้ฟอร์มมีประสิทธิภาพ มีการตรวจสอบข้อมูลที่ดี และใช้งานง่ายบนอุปกรณ์ต่างๆ
