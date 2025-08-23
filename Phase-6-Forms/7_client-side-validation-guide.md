# Client-side Validation พื้นฐาน

## 1. ภาพรวม Client-side Validation

Client-side validation เป็นการตรวจสอบข้อมูลที่ผู้ใช้กรอกในฟอร์มฝั่ง browser ก่อนส่งไปยัง server เพื่อ:

- **ปรับปรุง UX**: ให้ feedback ทันทีโดยไม่ต้องรอส่งไปยัง server
- **ลดโหลด Server**: กรองข้อมูลผิดพลาดก่อนส่ง
- **ประหยัด Bandwidth**: ไม่ต้องส่งข้อมูลผิดไป-กลับ

**หมายเหตุสำคัญ**: Client-side validation **ไม่สามารถแทนที่** server-side validation ได้ เพราะผู้ใช้สามารถปิดการทำงานหรือแก้ไขได้

## 2. HTML5 Built-in Validation

### 2.1 `required` Attribute - ฟิลด์บังคับ

#### การใช้งานพื้นฐาน

```html
<!-- Text input บังคับ -->
<form>
  <div class="form-group">
    <label for="username">ชื่อผู้ใช้ *</label>
    <input type="text" id="username" name="username" required />
  </div>

  <div class="form-group">
    <label for="email">อีเมล *</label>
    <input type="email" id="email" name="email" required />
  </div>

  <button type="submit">ส่งข้อมูล</button>
</form>
```

#### การใช้กับ Element ต่างๆ

```html
<form class="required-examples">
  <!-- Input fields -->
  <div class="form-group">
    <label for="name">ชื่อ-นามสกุล *</label>
    <input
      type="text"
      id="name"
      name="name"
      required
      placeholder="กรุณาใส่ชื่อ-นามสกุล"
    />
  </div>

  <!-- Email -->
  <div class="form-group">
    <label for="email">อีเมล *</label>
    <input type="email" id="email" name="email" required />
  </div>

  <!-- Password -->
  <div class="form-group">
    <label for="password">รหัสผ่าน *</label>
    <input type="password" id="password" name="password" required />
  </div>

  <!-- Number -->
  <div class="form-group">
    <label for="age">อายุ *</label>
    <input type="number" id="age" name="age" min="1" max="120" required />
  </div>

  <!-- Date -->
  <div class="form-group">
    <label for="birth-date">วันเกิด *</label>
    <input type="date" id="birth-date" name="birthDate" required />
  </div>

  <!-- Textarea -->
  <div class="form-group">
    <label for="description">คำอธิบาย *</label>
    <textarea
      id="description"
      name="description"
      required
      placeholder="กรุณาใส่คำอธิบาย"
    ></textarea>
  </div>

  <!-- Select -->
  <div class="form-group">
    <label for="country">ประเทศ *</label>
    <select id="country" name="country" required>
      <option value="">-- เลือกประเทศ --</option>
      <option value="TH">ไทย</option>
      <option value="US">สหรัฐอเมริกา</option>
      <option value="JP">ญี่ปุ่น</option>
    </select>
  </div>

  <!-- Radio buttons -->
  <fieldset>
    <legend>เพศ *</legend>
    <label
      ><input type="radio" name="gender" value="male" required /> ชาย</label
    >
    <label
      ><input type="radio" name="gender" value="female" required /> หญิง</label
    >
    <label
      ><input type="radio" name="gender" value="other" required /> อื่นๆ</label
    >
  </fieldset>

  <!-- Checkbox -->
  <div class="form-group">
    <label>
      <input type="checkbox" name="agree" required />
      ยอมรับเงื่อนไขการใช้งาน *
    </label>
  </div>

  <button type="submit">ส่งข้อมูล</button>
</form>
```

#### Custom Required Messages

```html
<form>
  <div class="form-group">
    <label for="username">ชื่อผู้ใช้ *</label>
    <input
      type="text"
      id="username"
      name="username"
      required
      title="กรุณาใส่ชื่อผู้ใช้"
    />
  </div>

  <div class="form-group">
    <label for="email">อีเมล *</label>
    <input
      type="email"
      id="email"
      name="email"
      required
      title="กรุณาใส่อีเมลที่ถูกต้อง"
    />
  </div>

  <button type="submit">ส่งข้อมูล</button>
</form>

<script>
  // Custom validation messages
  document.getElementById('username').addEventListener('invalid', function (e) {
    if (this.validity.valueMissing) {
      this.setCustomValidity('กรุณาใส่ชื่อผู้ใช้');
    }
  });

  document.getElementById('email').addEventListener('invalid', function (e) {
    if (this.validity.valueMissing) {
      this.setCustomValidity('กรุณาใส่อีเมล');
    } else if (this.validity.typeMismatch) {
      this.setCustomValidity('กรุณาใส่อีเมลในรูปแบบที่ถูกต้อง');
    }
  });

  // ล้าง custom message เมื่อผู้ใช้พิมพ์
  document.querySelectorAll('input').forEach((input) => {
    input.addEventListener('input', function () {
      this.setCustomValidity('');
    });
  });
</script>
```

### 2.2 Input Types และ Validation

#### `type="email"` - การตรวจสอบอีเมล

```html
<form class="email-validation">
  <div class="form-group">
    <label for="primary-email">อีเมลหลัก *</label>
    <input
      type="email"
      id="primary-email"
      name="primaryEmail"
      required
      placeholder="example@domain.com"
    />
  </div>

  <!-- Multiple emails -->
  <div class="form-group">
    <label for="cc-emails">อีเมล CC (คั่นด้วยเครื่องหมายจุลภาค)</label>
    <input
      type="email"
      id="cc-emails"
      name="ccEmails"
      multiple
      placeholder="email1@domain.com, email2@domain.com"
    />
  </div>

  <!-- Email with pattern -->
  <div class="form-group">
    <label for="work-email">อีเมลบริษัท (เฉพาะ @company.com)</label>
    <input
      type="email"
      id="work-email"
      name="workEmail"
      pattern="[a-zA-Z0-9._%+-]+@company\.com$"
      title="ต้องเป็นอีเมลของบริษัท (@company.com)"
      placeholder="yourname@company.com"
    />
  </div>

  <button type="submit">ส่งข้อมูล</button>
</form>
```

#### `type="url"` - การตรวจสอบ URL

```html
<form class="url-validation">
  <div class="form-group">
    <label for="website">เว็บไซต์ *</label>
    <input
      type="url"
      id="website"
      name="website"
      required
      placeholder="https://example.com"
    />
  </div>

  <!-- URL with pattern -->
  <div class="form-group">
    <label for="facebook">Facebook Profile</label>
    <input
      type="url"
      id="facebook"
      name="facebook"
      pattern="https://www\.facebook\.com/.*"
      title="ต้องเป็น URL ของ Facebook"
      placeholder="https://www.facebook.com/username"
    />
  </div>

  <!-- Social media URLs -->
  <div class="form-group">
    <label for="linkedin">LinkedIn Profile</label>
    <input
      type="url"
      id="linkedin"
      name="linkedin"
      pattern="https://www\.linkedin\.com/in/.*"
      placeholder="https://www.linkedin.com/in/username"
    />
  </div>

  <button type="submit">บันทึก</button>
</form>
```

#### `type="tel"` - หมายเลขโทรศัพท์

```html
<form class="tel-validation">
  <div class="form-group">
    <label for="phone">เบอร์โทรศัพท์ *</label>
    <input
      type="tel"
      id="phone"
      name="phone"
      required
      pattern="[0-9]{10}"
      title="กรุณาใส่เบอร์โทร 10 หลัก"
      placeholder="0812345678"
    />
  </div>

  <!-- International format -->
  <div class="form-group">
    <label for="intl-phone">เบอร์โทรสากล</label>
    <input
      type="tel"
      id="intl-phone"
      name="intlPhone"
      pattern="^\+[1-9]\d{1,14}$"
      title="รูปแบบ: +66812345678"
      placeholder="+66812345678"
    />
  </div>

  <!-- Thai mobile -->
  <div class="form-group">
    <label for="mobile">มือถือ (08X, 09X)</label>
    <input
      type="tel"
      id="mobile"
      name="mobile"
      pattern="0[89][0-9]{8}"
      title="เบอร์มือถือไทย ขึ้นต้นด้วย 08 หรือ 09"
      placeholder="081234567"
    />
  </div>

  <button type="submit">บันทึก</button>
</form>
```

#### `type="number"` - ตัวเลข

```html
<form class="number-validation">
  <div class="form-group">
    <label for="age">อายุ *</label>
    <input
      type="number"
      id="age"
      name="age"
      required
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
      max="1000000"
      step="0.01"
      placeholder="100.50"
    />
  </div>

  <div class="form-group">
    <label for="percentage">เปอร์เซ็นต์ (0-100)</label>
    <input
      type="number"
      id="percentage"
      name="percentage"
      min="0"
      max="100"
      step="0.1"
      placeholder="50.5"
    />
  </div>

  <!-- Custom validation -->
  <div class="form-group">
    <label for="even-number">เลขคู่</label>
    <input
      type="number"
      id="even-number"
      name="evenNumber"
      step="2"
      min="0"
      title="กรุณาใส่เลขคู่"
      placeholder="2, 4, 6, 8..."
    />
  </div>

  <button type="submit">คำนวณ</button>
</form>
```

### 2.3 `pattern` Attribute - การกำหนดรูปแบบ

#### รูปแบบพื้นฐาน

```html
<form class="pattern-examples">
  <!-- รหัสนักเรียน -->
  <div class="form-group">
    <label for="student-id">รหัสนักเรียน (6 หลัก)</label>
    <input
      type="text"
      id="student-id"
      name="studentId"
      pattern="[0-9]{6}"
      title="รหัสนักเรียน 6 หลัก เช่น 123456"
      placeholder="123456"
    />
  </div>

  <!-- รหัสประจำตัวประชาชน -->
  <div class="form-group">
    <label for="id-card">เลขประจำตัวประชาชน</label>
    <input
      type="text"
      id="id-card"
      name="idCard"
      pattern="[0-9]{13}"
      title="เลขประจำตัว 13 หลัก"
      placeholder="1234567890123"
      maxlength="13"
    />
  </div>

  <!-- รหัสไปรษณีย์ -->
  <div class="form-group">
    <label for="postal-code">รหัสไปรษณีย์</label>
    <input
      type="text"
      id="postal-code"
      name="postalCode"
      pattern="[0-9]{5}"
      title="รหัสไปรษณีย์ 5 หลัก"
      placeholder="10110"
      maxlength="5"
    />
  </div>

  <!-- ป้ายทะเบียนรถ -->
  <div class="form-group">
    <label for="license-plate">ป้ายทะเบียนรถ</label>
    <input
      type="text"
      id="license-plate"
      name="licensePlate"
      pattern="[ก-ฮ]{1,2}[0-9]{1,4}"
      title="รูปแบบ: กข1234 หรือ 1กข2345"
      placeholder="กข1234"
    />
  </div>

  <button type="submit">ตรวจสอบ</button>
</form>
```

#### รูปแบบขั้นสูง

```html
<form class="advanced-patterns">
  <!-- รหัสผ่านแข็งแรง -->
  <div class="form-group">
    <label for="strong-password">รหัสผ่านแข็งแรง</label>
    <input
      type="password"
      id="strong-password"
      name="password"
      pattern="^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$"
      title="อย่างน้อย 8 ตัว มีตัวพิมพ์เล็ก พิมพ์ใหญ่ ตัวเลข และอักขระพิเศษ"
    />
  </div>

  <!-- ชื่อผู้ใช้ -->
  <div class="form-group">
    <label for="username">ชื่อผู้ใช้</label>
    <input
      type="text"
      id="username"
      name="username"
      pattern="^[a-zA-Z0-9_]{3,20}$"
      title="3-20 ตัวอักษร ใช้ได้เฉพาะ a-z, A-Z, 0-9, _"
      placeholder="user123"
    />
  </div>

  <!-- เลขบัญชีธนาคาร -->
  <div class="form-group">
    <label for="bank-account">เลขบัญชีธนาคาร</label>
    <input
      type="text"
      id="bank-account"
      name="bankAccount"
      pattern="[0-9]{3}-[0-9]{1}-[0-9]{5}-[0-9]{1}"
      title="รูปแบบ: XXX-X-XXXXX-X"
      placeholder="123-4-56789-0"
    />
  </div>

  <!-- ISBN -->
  <div class="form-group">
    <label for="isbn">ISBN</label>
    <input
      type="text"
      id="isbn"
      name="isbn"
      pattern="^(?:ISBN(?:-1[03])?:? )?(?=[0-9X]{10}$|(?=(?:[0-9]+[- ]){3})[- 0-9X]{13}$|97[89][0-9]{10}$|(?=(?:[0-9]+[- ]){4})[- 0-9]{17}$)(?:97[89][- ]?)?[0-9]{1,5}[- ]?[0-9]+[- ]?[0-9]+[- ]?[0-9X]$"
      title="รูปแบบ ISBN ที่ถูกต้อง"
      placeholder="978-0-123456-78-9"
    />
  </div>

  <!-- IP Address -->
  <div class="form-group">
    <label for="ip-address">IP Address</label>
    <input
      type="text"
      id="ip-address"
      name="ipAddress"
      pattern="^(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$"
      title="รูปแบบ IP Address เช่น 192.168.1.1"
      placeholder="192.168.1.1"
    />
  </div>

  <button type="submit">ตรวจสอบ</button>
</form>
```

## 3. การใช้งานขั้นสูง

### 3.1 การตรวจสอบแบบ Real-time

```html
<form class="realtime-validation" novalidate>
  <div class="form-group">
    <label for="username">ชื่อผู้ใช้</label>
    <input
      type="text"
      id="username"
      name="username"
      pattern="^[a-zA-Z0-9_]{3,20}$"
      required
    />
    <div class="validation-message" id="username-validation"></div>
  </div>

  <div class="form-group">
    <label for="email">อีเมล</label>
    <input type="email" id="email" name="email" required />
    <div class="validation-message" id="email-validation"></div>
  </div>

  <div class="form-group">
    <label for="password">รหัสผ่าน</label>
    <input
      type="password"
      id="password"
      name="password"
      pattern="^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$"
      required
    />
    <div class="validation-message" id="password-validation"></div>
    <div class="password-strength">
      <div class="strength-meter">
        <div class="strength-fill" id="strength-fill"></div>
      </div>
      <span id="strength-text">อ่อนแอ</span>
    </div>
  </div>

  <div class="form-group">
    <label for="confirm-password">ยืนยันรหัสผ่าน</label>
    <input
      type="password"
      id="confirm-password"
      name="confirmPassword"
      required
    />
    <div class="validation-message" id="confirm-validation"></div>
  </div>

  <button type="submit" id="submit-btn" disabled>สมัครสมาชิก</button>
</form>

<style>
  .validation-message {
    font-size: 0.875rem;
    margin-top: 0.25rem;
    min-height: 1.25rem;
  }

  .validation-message.valid {
    color: #10b981;
  }

  .validation-message.invalid {
    color: #ef4444;
  }

  .validation-message.checking {
    color: #f59e0b;
  }

  .password-strength {
    margin-top: 0.5rem;
  }

  .strength-meter {
    width: 100%;
    height: 8px;
    background-color: #e5e7eb;
    border-radius: 4px;
    overflow: hidden;
  }

  .strength-fill {
    height: 100%;
    transition: width 0.3s ease, background-color 0.3s ease;
    width: 0%;
    background-color: #ef4444;
  }

  .form-group {
    margin-bottom: 1rem;
  }

  input:valid {
    border-color: #10b981;
  }

  input:invalid:not(:placeholder-shown) {
    border-color: #ef4444;
  }
</style>

<script>
  const form = document.querySelector('.realtime-validation');
  const inputs = form.querySelectorAll('input');
  const submitBtn = document.getElementById('submit-btn');

  // Validation rules
  const validationRules = {
    username: {
      required: true,
      pattern: /^[a-zA-Z0-9_]{3,20}$/,
      messages: {
        required: 'กรุณาใส่ชื่อผู้ใช้',
        pattern: 'ชื่อผู้ใช้ต้องมี 3-20 ตัวอักษร (a-z, A-Z, 0-9, _)',
        valid: 'ชื่อผู้ใช้ถูกต้อง',
      },
    },
    email: {
      required: true,
      type: 'email',
      messages: {
        required: 'กรุณาใส่อีเมล',
        type: 'รูปแบบอีเมลไม่ถูกต้อง',
        valid: 'อีเมลถูกต้อง',
      },
    },
    password: {
      required: true,
      pattern:
        /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/,
      messages: {
        required: 'กรุณาใส่รหัสผ่าน',
        pattern:
          'รหัสผ่านต้องมีอย่างน้อย 8 ตัว มีตัวพิมพ์เล็ก พิมพ์ใหญ่ ตัวเลข และอักขระพิเศษ',
        valid: 'รหัสผ่านแข็งแรง',
      },
    },
  };

  // Real-time validation
  inputs.forEach((input) => {
    input.addEventListener('input', function () {
      validateField(this);
      updateSubmitButton();
    });

    input.addEventListener('blur', function () {
      validateField(this);
    });
  });

  function validateField(field) {
    const name = field.name;
    const value = field.value;
    const messageEl = document.getElementById(name + '-validation');
    const rules = validationRules[name];

    if (!rules) return;

    // ตรวจสอบ required
    if (rules.required && !value.trim()) {
      showValidationMessage(messageEl, rules.messages.required, 'invalid');
      return false;
    }

    // ตรวจสอบ pattern
    if (rules.pattern && value && !rules.pattern.test(value)) {
      showValidationMessage(messageEl, rules.messages.pattern, 'invalid');
      return false;
    }

    // ตรวจสอบ email
    if (rules.type === 'email' && value && !isValidEmail(value)) {
      showValidationMessage(messageEl, rules.messages.type, 'invalid');
      return false;
    }

    // ตรวจสอบการยืนยันรหัสผ่าน
    if (name === 'confirmPassword') {
      return validatePasswordConfirm();
    }

    // ถูกต้อง
    if (value) {
      showValidationMessage(messageEl, rules.messages.valid, 'valid');

      // อัปเดต password strength
      if (name === 'password') {
        updatePasswordStrength(value);
      }
    } else {
      showValidationMessage(messageEl, '', '');
    }

    return true;
  }

  function validatePasswordConfirm() {
    const password = document.getElementById('password').value;
    const confirmPassword = document.getElementById('confirm-password').value;
    const messageEl = document.getElementById('confirm-validation');

    if (!confirmPassword) {
      showValidationMessage(messageEl, '', '');
      return false;
    }

    if (password !== confirmPassword) {
      showValidationMessage(messageEl, 'รหัสผ่านไม่ตรงกัน', 'invalid');
      return false;
    }

    showValidationMessage(messageEl, 'รหัสผ่านตรงกัน', 'valid');
    return true;
  }

  function showValidationMessage(element, message, type) {
    element.textContent = message;
    element.className = 'validation-message' + (type ? ' ' + type : '');
  }

  function isValidEmail(email) {
    const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return emailPattern.test(email);
  }

  function updatePasswordStrength(password) {
    const strengthFill = document.getElementById('strength-fill');
    const strengthText = document.getElementById('strength-text');

    let score = 0;
    let feedback = 'อ่อนแอ';
    let color = '#ef4444';

    // ตรวจสอบเงื่อนไขต่างๆ
    if (password.length >= 8) score++;
    if (/[a-z]/.test(password)) score++;
    if (/[A-Z]/.test(password)) score++;
    if (/[0-9]/.test(password)) score++;
    if (/[@$!%*?&]/.test(password)) score++;

    // กำหนดระดับความแข็งแรง
    switch (score) {
      case 0:
      case 1:
        feedback = 'อ่อนแอ';
        color = '#ef4444';
        break;
      case 2:
        feedback = 'ปานกลาง';
        color = '#f59e0b';
        break;
      case 3:
        feedback = 'ดี';
        color = '#10b981';
        break;
      case 4:
      case 5:
        feedback = 'แข็งแรง';
        color = '#059669';
        break;
    }

    strengthFill.style.width = score * 20 + '%';
    strengthFill.style.backgroundColor = color;
    strengthText.textContent = feedback;
  }

  function updateSubmitButton() {
    const allValid = Array.from(inputs).every((input) => {
      const name = input.name;
      if (name === 'confirmPassword') {
        return validatePasswordConfirm();
      }
      return input.validity.valid && input.value.trim() !== '';
    });

    submitBtn.disabled = !allValid;
  }

  // ตรวจสอบเมื่อส่งฟอร์ม
  form.addEventListener('submit', function (e) {
    e.preventDefault();

    let allValid = true;
    inputs.forEach((input) => {
      if (!validateField(input)) {
        allValid = false;
      }
    });

    if (allValid) {
      alert('ข้อมูลถูกต้อง! พร้อมส่งไปยัง server');
      // ส่งข้อมูลไปยัง server
    } else {
      alert('กรุณาแก้ไขข้อมูลที่ผิดพลาด');
    }
  });
</script>
```

### 3.2 Custom Validation API

```html
<form class="custom-validation-api" novalidate>
  <div class="form-group">
    <label for="username-check">ชื่อผู้ใช้</label>
    <input type="text" id="username-check" name="username" required />
    <div class="validation-status" id="username-status"></div>
  </div>

  <div class="form-group">
    <label for="age-group">กลุ่มอายุ</label>
    <select id="age-group" name="ageGroup" required>
      <option value="">-- เลือกกลุ่มอายุ --</option>
      <option value="child">เด็ก (0-12 ปี)</option>
      <option value="teen">วัยรุ่น (13-19 ปี)</option>
      <option value="adult">ผู้ใหญ่ (20-59 ปี)</option>
      <option value="senior">ผู้สูงอายุ (60+ ปี)</option>
    </select>
  </div>

  <div class="form-group">
    <label for="birth-year">ปีเกิด</label>
    <input
      type="number"
      id="birth-year"
      name="birthYear"
      min="1920"
      max="2024"
      required
    />
  </div>

  <button type="submit">ตรวจสอบ</button>
</form>

<script>
  // Custom validation functions
  function validateUsername(username) {
    const errors = [];

    if (username.length < 3) {
      errors.push('ชื่อผู้ใช้ต้องมีอย่างน้อย 3 ตัวอักษร');
    }

    if (username.length > 20) {
      errors.push('ชื่อผู้ใช้ต้องไม่เกิน 20 ตัวอักษร');
    }

    if (!/^[a-zA-Z0-9_]+$/.test(username)) {
      errors.push('ใช้ได้เฉพาะ a-z, A-Z, 0-9, และ _');
    }

    if (/^[0-9]/.test(username)) {
      errors.push('ไม่สามารถขึ้นต้นด้วยตัวเลข');
    }

    const reserved = ['admin', 'root', 'user', 'test'];
    if (reserved.includes(username.toLowerCase())) {
      errors.push('ชื่อผู้ใช้นี้ถูกสงวนไว้');
    }

    return errors;
  }

  function validateAgeConsistency(ageGroup, birthYear) {
    const currentYear = new Date().getFullYear();
    const age = currentYear - birthYear;

    const ageRanges = {
      child: [0, 12],
      teen: [13, 19],
      adult: [20, 59],
      senior: [60, 120],
    };

    const [minAge, maxAge] = ageRanges[ageGroup] || [0, 0];

    if (age < minAge || age > maxAge) {
      return `อายุ ${age} ปี ไม่ตรงกับกลุ่มอายุที่เลือก`;
    }

    return null;
  }

  // Event listeners
  const usernameInput = document.getElementById('username-check');
  const ageGroupSelect = document.getElementById('age-group');
  const birthYearInput = document.getElementById('birth-year');
  const form = document.querySelector('.custom-validation-api');

  usernameInput.addEventListener('input', function () {
    const errors = validateUsername(this.value);
    const statusEl = document.getElementById('username-status');

    // ล้าง custom validity
    this.setCustomValidity('');

    if (errors.length > 0) {
      this.setCustomValidity(errors[0]);
      statusEl.innerHTML = errors
        .map((error) => `<div class="error">❌ ${error}</div>`)
        .join('');
      statusEl.className = 'validation-status invalid';
    } else if (this.value) {
      statusEl.innerHTML = '<div class="success">✅ ชื่อผู้ใช้ถูกต้อง</div>';
      statusEl.className = 'validation-status valid';
    } else {
      statusEl.innerHTML = '';
      statusEl.className = 'validation-status';
    }
  });

  // ตรวจสอบความสอดคล้องของอายุ
  function checkAgeConsistency() {
    const ageGroup = ageGroupSelect.value;
    const birthYear = parseInt(birthYearInput.value);

    if (ageGroup && birthYear) {
      const error = validateAgeConsistency(ageGroup, birthYear);

      if (error) {
        birthYearInput.setCustomValidity(error);
      } else {
        birthYearInput.setCustomValidity('');
      }
    }
  }

  ageGroupSelect.addEventListener('change', checkAgeConsistency);
  birthYearInput.addEventListener('input', checkAgeConsistency);

  form.addEventListener('submit', function (e) {
    e.preventDefault();

    // ตรวจสอบความถูกต้องของฟอร์ม
    const isValid = this.checkValidity();

    if (isValid) {
      alert('ข้อมูลทั้งหมดถูกต้อง!');
    } else {
      // แสดง validation errors
      const invalidFields = this.querySelectorAll(':invalid');
      invalidFields[0]?.focus();
    }
  });
</script>

<style>
  .validation-status {
    margin-top: 0.25rem;
    font-size: 0.875rem;
  }

  .validation-status .error {
    color: #ef4444;
    margin: 0.125rem 0;
  }

  .validation-status .success {
    color: #10b981;
    margin: 0.125rem 0;
  }

  input:invalid {
    border-color: #ef4444;
    box-shadow: 0 0 0 1px #ef4444;
  }

  input:valid:not(:placeholder-shown) {
    border-color: #10b981;
  }
</style>
```

## 4. การจัดการ Error Messages

### 4.1 Error Styling และ Accessibility

```html
<form class="accessible-validation" novalidate>
  <div class="form-group">
    <label for="required-field">ฟิลด์บังคับ *</label>
    <input
      type="text"
      id="required-field"
      name="requiredField"
      required
      aria-describedby="required-field-error"
    />
    <div
      id="required-field-error"
      class="error-message"
      role="alert"
      aria-live="polite"
    ></div>
  </div>

  <div class="form-group">
    <label for="email-field">อีเมล *</label>
    <input
      type="email"
      id="email-field"
      name="email"
      required
      aria-describedby="email-field-error email-field-help"
    />
    <div id="email-field-help" class="help-text">เราจะไม่แชร์อีเมลของคุณ</div>
    <div
      id="email-field-error"
      class="error-message"
      role="alert"
      aria-live="polite"
    ></div>
  </div>

  <div class="form-group">
    <label for="pattern-field">รหัสสินค้า (A-Z + 3 หลัก)</label>
    <input
      type="text"
      id="pattern-field"
      name="productCode"
      pattern="[A-Z]{2}[0-9]{3}"
      title="รูปแบบ: AB123"
      aria-describedby="pattern-field-error pattern-field-help"
    />
    <div id="pattern-field-help" class="help-text">ตัวอย่าง: AB123, XY789</div>
    <div
      id="pattern-field-error"
      class="error-message"
      role="alert"
      aria-live="polite"
    ></div>
  </div>

  <button type="submit">ส่งข้อมูล</button>
</form>

<style>
  .form-group {
    margin-bottom: 1.5rem;
    position: relative;
  }

  label {
    display: block;
    font-weight: 600;
    margin-bottom: 0.5rem;
    color: #374151;
  }

  input {
    width: 100%;
    padding: 0.75rem;
    border: 2px solid #d1d5db;
    border-radius: 0.375rem;
    font-size: 1rem;
    transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
  }

  input:focus {
    outline: none;
    border-color: #3b82f6;
    box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
  }

  input:invalid:not(:placeholder-shown) {
    border-color: #ef4444;
    box-shadow: 0 0 0 3px rgba(239, 68, 68, 0.1);
  }

  input:valid:not(:placeholder-shown) {
    border-color: #10b981;
  }

  .error-message {
    color: #ef4444;
    font-size: 0.875rem;
    margin-top: 0.25rem;
    min-height: 1.25rem;
    display: flex;
    align-items: center;
  }

  .error-message:not(:empty)::before {
    content: '⚠️';
    margin-right: 0.5rem;
  }

  .help-text {
    color: #6b7280;
    font-size: 0.875rem;
    margin-top: 0.25rem;
  }

  .help-text::before {
    content: '💡';
    margin-right: 0.5rem;
  }

  /* Animation for error messages */
  .error-message {
    opacity: 0;
    transform: translateY(-0.5rem);
    transition: opacity 0.2s ease-in-out, transform 0.2s ease-in-out;
  }

  .error-message:not(:empty) {
    opacity: 1;
    transform: translateY(0);
  }
</style>

<script>
  const form = document.querySelector('.accessible-validation');
  const inputs = form.querySelectorAll('input');

  // Error messages
  const errorMessages = {
    required: 'กรุณากรอกข้อมูลในช่องนี้',
    email: 'กรุณาใส่อีเมลในรูปแบบที่ถูกต้อง',
    pattern: 'รูปแบบข้อมูลไม่ถูกต้อง กรุณาตรวจสอบอีกครั้ง',
  };

  // Real-time validation
  inputs.forEach((input) => {
    input.addEventListener('blur', () => validateInput(input));
    input.addEventListener('input', () => {
      if (input.classList.contains('was-validated')) {
        validateInput(input);
      }
    });
  });

  function validateInput(input) {
    const errorElement = document.getElementById(input.id + '-error');
    const validity = input.validity;

    input.classList.add('was-validated');

    let errorMessage = '';

    if (validity.valueMissing) {
      errorMessage = errorMessages.required;
    } else if (validity.typeMismatch) {
      errorMessage = errorMessages.email;
    } else if (validity.patternMismatch) {
      errorMessage = input.title || errorMessages.pattern;
    } else if (!validity.valid) {
      errorMessage = 'ข้อมูลไม่ถูกต้อง';
    }

    errorElement.textContent = errorMessage;

    // อัปเดต aria-invalid
    input.setAttribute('aria-invalid', !validity.valid);

    return validity.valid;
  }

  // Form submission
  form.addEventListener('submit', function (e) {
    e.preventDefault();

    let allValid = true;

    inputs.forEach((input) => {
      if (!validateInput(input)) {
        allValid = false;
      }
    });

    if (allValid) {
      alert('ข้อมูลทั้งหมดถูกต้อง! พร้อมส่งไปยัง server');
    } else {
      // โฟกัสไปที่ฟิลด์แรกที่ผิด
      const firstInvalid = form.querySelector(':invalid');
      if (firstInvalid) {
        firstInvalid.focus();
        // เลื่อนไปที่ฟิลด์ที่ผิด
        firstInvalid.scrollIntoView({
          behavior: 'smooth',
          block: 'center',
        });
      }
    }
  });
</script>
```

## 5. Best Practices

### 5.1 การเลือกใช้ Validation

```html
<!-- ✅ ใช้ HTML5 validation กับ progressive enhancement -->
<input
  type="email"
  required
  pattern="[^@\s]+@[^@\s]+\.[^@\s]+"
  title="กรุณาใส่อีเมลที่ถูกต้อง"
/>

<!-- ✅ ใช้ custom validation สำหรับกรณีซับซ้อน -->
<input type="text" required data-custom-validation="username" />

<!-- ❌ หลีกเลี่ยงการใช้ JavaScript อย่างเดียว -->
<input type="text" onblur="validateEmail(this)" />
<!-- ไม่มี fallback -->
```

### 5.2 UX ที่ดี

```html
<!-- ✅ ให้ feedback ที่ชัดเจน -->
<input
  type="password"
  required
  aria-describedby="password-help password-error"
/>
<div id="password-help">อย่างน้อย 8 ตัวอักษร</div>
<div id="password-error" role="alert"></div>

<!-- ✅ ไม่ validate จนกว่าผู้ใช้จะเสร็จสิ้นการพิมพ์ -->
<input type="email" required onblur="validate()" oninput="clearError()" />
```

### 5.3 Accessibility

```html
<!-- ✅ ใช้ ARIA attributes -->
<input
  type="text"
  required
  aria-invalid="false"
  aria-describedby="field-error"
  aria-required="true"
/>
<div id="field-error" role="alert" aria-live="polite"></div>

<!-- ✅ ใช้ semantic HTML -->
<fieldset>
  <legend>ข้อมูลบังคับ</legend>
  <input type="text" required />
</fieldset>
```

---

**สรุป**: Client-side validation ช่วยปรับปรุง UX แต่ต้องใช้ร่วมกับ server-side validation เสมอ การใช้ HTML5 built-in validation ร่วมกับ JavaScript จะให้ผลลัพธ์ที่ดีที่สุด
