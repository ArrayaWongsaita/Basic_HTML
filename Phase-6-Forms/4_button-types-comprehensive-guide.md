# ปุ่ม: `<button>` Element และ Types ต่างๆ

## 1. ภาพรวม `<button>` Element

`<button>` เป็น element สำหรับสร้างปุ่มที่ผู้ใช้สามารถคลิกได้ มีความยืดหยุ่นมากกว่า `<input type="submit">` เพราะสามารถใส่เนื้อหาที่ซับซ้อนได้

**Syntax พื้นฐาน:**

```html
<button type="button|submit|reset" attributes...>
  เนื้อหาปุ่ม (ข้อความ, รูปภาพ, ไอคอน)
</button>
```

**ความแตกต่างระหว่าง `<button>` และ `<input>`:**

- `<button>`: สามารถใส่เนื้อหาได้หลากหลาย (HTML, ไอคอน, รูปภาพ)
- `<input>`: ใส่ได้แค่ข้อความธรรมดาใน value attribute

## 2. Button Types แบบละเอียด

### 2.1 `type="button"` - ปุ่มทั่วไป

**การใช้งาน:** ปุ่มที่ไม่มีพฤติกรรมเริ่มต้น ต้องใช้ JavaScript จัดการ

```html
<!-- ปุ่มพื้นฐาน -->
<button type="button">คลิกที่นี่</button>

<!-- ปุ่มที่มีไอคอน -->
<button type="button" onclick="toggleMenu()">☰ เมนู</button>

<!-- ปุ่มที่มี HTML ข้างใน -->
<button type="button" class="btn-with-icon">
  <span class="icon">📱</span>
  <span class="text">โทรติดต่อ</span>
</button>

<!-- ปุ่มที่มีรูปภาพ -->
<button type="button" class="social-btn">
  <img src="facebook-icon.png" alt="Facebook" width="20" height="20" />
  เข้าสู่ระบบด้วย Facebook
</button>
```

#### ตัวอย่างการใช้งานกับ JavaScript

```html
<div class="calculator">
  <div class="display">
    <input type="text" id="calc-display" readonly />
  </div>

  <div class="buttons">
    <!-- ปุ่มตัวเลข -->
    <button type="button" onclick="addToDisplay('7')">7</button>
    <button type="button" onclick="addToDisplay('8')">8</button>
    <button type="button" onclick="addToDisplay('9')">9</button>
    <button type="button" onclick="addToDisplay('/')" class="operator">
      ÷
    </button>

    <button type="button" onclick="addToDisplay('4')">4</button>
    <button type="button" onclick="addToDisplay('5')">5</button>
    <button type="button" onclick="addToDisplay('6')">6</button>
    <button type="button" onclick="addToDisplay('*')" class="operator">
      ×
    </button>

    <button type="button" onclick="addToDisplay('1')">1</button>
    <button type="button" onclick="addToDisplay('2')">2</button>
    <button type="button" onclick="addToDisplay('3')">3</button>
    <button type="button" onclick="addToDisplay('-')" class="operator">
      -
    </button>

    <button type="button" onclick="addToDisplay('0')">0</button>
    <button type="button" onclick="addToDisplay('.')">.</button>
    <button type="button" onclick="calculate()" class="equals">=</button>
    <button type="button" onclick="addToDisplay('+')" class="operator">
      +
    </button>

    <!-- ปุ่มล้าง -->
    <button type="button" onclick="clearDisplay()" class="clear">C</button>
    <button type="button" onclick="deleteLast()" class="delete">⌫</button>
  </div>
</div>

<script>
  function addToDisplay(value) {
    document.getElementById('calc-display').value += value;
  }

  function clearDisplay() {
    document.getElementById('calc-display').value = '';
  }

  function deleteLast() {
    const display = document.getElementById('calc-display');
    display.value = display.value.slice(0, -1);
  }

  function calculate() {
    const display = document.getElementById('calc-display');
    try {
      display.value = eval(display.value);
    } catch (error) {
      display.value = 'Error';
    }
  }
</script>
```

#### ปุ่มสำหรับควบคุม UI

```html
<div class="media-player">
  <div class="controls">
    <button type="button" onclick="previousTrack()" title="เพลงก่อนหน้า">
      ⏮️
    </button>

    <button
      type="button"
      id="playPauseBtn"
      onclick="togglePlay()"
      title="เล่น/หยุด"
    >
      ▶️
    </button>

    <button type="button" onclick="nextTrack()" title="เพลงถัดไป">⏭️</button>

    <button
      type="button"
      onclick="toggleMute()"
      id="muteBtn"
      title="เปิด/ปิดเสียง"
    >
      🔊
    </button>
  </div>

  <div class="volume-control">
    <button type="button" onclick="volumeDown()">🔉</button>
    <input type="range" id="volumeSlider" min="0" max="100" value="50" />
    <button type="button" onclick="volumeUp()">🔊</button>
  </div>
</div>

<script>
  let isPlaying = false;
  let isMuted = false;

  function togglePlay() {
    const btn = document.getElementById('playPauseBtn');
    if (isPlaying) {
      btn.textContent = '▶️';
      btn.title = 'เล่น';
      // หยุดเพลง
    } else {
      btn.textContent = '⏸️';
      btn.title = 'หยุด';
      // เล่นเพลง
    }
    isPlaying = !isPlaying;
  }

  function toggleMute() {
    const btn = document.getElementById('muteBtn');
    if (isMuted) {
      btn.textContent = '🔊';
      btn.title = 'ปิดเสียง';
    } else {
      btn.textContent = '🔇';
      btn.title = 'เปิดเสียง';
    }
    isMuted = !isMuted;
  }

  function volumeUp() {
    const slider = document.getElementById('volumeSlider');
    slider.value = Math.min(100, parseInt(slider.value) + 10);
  }

  function volumeDown() {
    const slider = document.getElementById('volumeSlider');
    slider.value = Math.max(0, parseInt(slider.value) - 10);
  }
</script>
```

### 2.2 `type="submit"` - ปุ่มส่งฟอร์ม

**การใช้งาน:** ส่งข้อมูลฟอร์มไปยัง server เมื่อคลิก

```html
<!-- ปุ่มส่งพื้นฐาน -->
<form action="/submit" method="POST">
  <input type="text" name="username" placeholder="ชื่อผู้ใช้" required />
  <input type="password" name="password" placeholder="รหัสผ่าน" required />

  <button type="submit">เข้าสู่ระบบ</button>
</form>

<!-- ปุ่มส่งที่มีไอคอน -->
<form action="/contact" method="POST">
  <textarea name="message" placeholder="ข้อความ" required></textarea>

  <button type="submit" class="btn-primary">📤 ส่งข้อความ</button>
</form>

<!-- ปุ่มส่งแบบมีสถานะ -->
<form action="/newsletter" method="POST" id="newsletterForm">
  <input type="email" name="email" placeholder="อีเมลของคุณ" required />

  <button type="submit" id="subscribeBtn">
    <span class="btn-text">สมัครรับข่าวสาร</span>
    <span class="btn-loading" style="display: none;">
      <span class="spinner"></span> กำลังส่ง...
    </span>
  </button>
</form>

<script>
  document
    .getElementById('newsletterForm')
    .addEventListener('submit', function (e) {
      const btn = document.getElementById('subscribeBtn');
      const btnText = btn.querySelector('.btn-text');
      const btnLoading = btn.querySelector('.btn-loading');

      // แสดงสถานะกำลังโหลด
      btnText.style.display = 'none';
      btnLoading.style.display = 'inline';
      btn.disabled = true;

      // จำลองการส่งข้อมูล
      setTimeout(() => {
        btnText.style.display = 'inline';
        btnLoading.style.display = 'none';
        btn.disabled = false;
        btn.innerHTML = '✅ สมัครสำเร็จ';
        btn.style.backgroundColor = 'green';
      }, 3000);
    });
</script>
```

#### ปุ่มส่งแบบต่างๆ ในฟอร์มเดียว

```html
<form action="/post" method="POST" class="post-form">
  <div class="form-group">
    <label for="title">หัวข้อ</label>
    <input type="text" id="title" name="title" required />
  </div>

  <div class="form-group">
    <label for="content">เนื้อหา</label>
    <textarea id="content" name="content" rows="10" required></textarea>
  </div>

  <div class="form-group">
    <label for="category">หมวดหมู่</label>
    <select id="category" name="category">
      <option value="news">ข่าว</option>
      <option value="blog">บล็อก</option>
      <option value="tutorial">บทความ</option>
    </select>
  </div>

  <div class="form-actions">
    <!-- ปุ่มบันทึกร่าง -->
    <button type="submit" name="action" value="draft" class="btn btn-secondary">
      💾 บันทึกร่าง
    </button>

    <!-- ปุ่มเผยแพร่ -->
    <button type="submit" name="action" value="publish" class="btn btn-primary">
      🌐 เผยแพร่
    </button>

    <!-- ปุ่มตั้งเวลาเผยแพร่ -->
    <button type="submit" name="action" value="schedule" class="btn btn-info">
      ⏰ ตั้งเวลาเผยแพร่
    </button>

    <!-- ปุ่มพรีวิว -->
    <button
      type="submit"
      name="action"
      value="preview"
      formtarget="_blank"
      class="btn btn-outline"
    >
      👁️ พรีวิว
    </button>
  </div>
</form>
```

#### Form Validation กับ Submit Button

```html
<form action="/register" method="POST" id="registrationForm" novalidate>
  <div class="form-group">
    <label for="username">ชื่อผู้ใช้ *</label>
    <input
      type="text"
      id="username"
      name="username"
      required
      minlength="3"
      maxlength="20"
    />
    <div class="error-message" id="username-error"></div>
  </div>

  <div class="form-group">
    <label for="email">อีเมล *</label>
    <input type="email" id="email" name="email" required />
    <div class="error-message" id="email-error"></div>
  </div>

  <div class="form-group">
    <label for="password">รหัสผ่าน *</label>
    <input
      type="password"
      id="password"
      name="password"
      required
      minlength="8"
    />
    <div class="error-message" id="password-error"></div>
  </div>

  <div class="form-group">
    <label for="confirmPassword">ยืนยันรหัสผ่าน *</label>
    <input
      type="password"
      id="confirmPassword"
      name="confirmPassword"
      required
    />
    <div class="error-message" id="confirm-error"></div>
  </div>

  <button type="submit" id="submitBtn" disabled>สมัครสมาชิก</button>
</form>

<script>
  const form = document.getElementById('registrationForm');
  const submitBtn = document.getElementById('submitBtn');
  const inputs = form.querySelectorAll('input[required]');

  // ตรวจสอบการกรอกข้อมูล
  function validateForm() {
    let isValid = true;

    inputs.forEach((input) => {
      const errorDiv = document.getElementById(input.id + '-error');
      errorDiv.textContent = '';

      if (!input.value.trim()) {
        errorDiv.textContent = 'กรุณากรอกข้อมูลนี้';
        isValid = false;
      } else if (input.type === 'email' && !isValidEmail(input.value)) {
        errorDiv.textContent = 'รูปแบบอีเมลไม่ถูกต้อง';
        isValid = false;
      } else if (input.id === 'password' && input.value.length < 8) {
        errorDiv.textContent = 'รหัสผ่านต้องมีอย่างน้อย 8 ตัวอักษร';
        isValid = false;
      } else if (
        input.id === 'confirmPassword' &&
        input.value !== document.getElementById('password').value
      ) {
        errorDiv.textContent = 'รหัสผ่านไม่ตรงกัน';
        isValid = false;
      }
    });

    // เปิด/ปิดปุ่มส่ง
    submitBtn.disabled = !isValid;

    return isValid;
  }

  function isValidEmail(email) {
    return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
  }

  // ตรวจสอบแบบ real-time
  inputs.forEach((input) => {
    input.addEventListener('input', validateForm);
    input.addEventListener('blur', validateForm);
  });

  // ตรวจสอบก่อนส่ง
  form.addEventListener('submit', function (e) {
    if (!validateForm()) {
      e.preventDefault();
      alert('กรุณาแก้ไขข้อมูลที่ผิดพลาด');
    }
  });
</script>
```

### 2.3 `type="reset"` - ปุ่มรีเซ็ต

**การใช้งาน:** ล้างข้อมูลในฟอร์มกลับเป็นค่าเริ่มต้น

```html
<!-- ปุ่มรีเซ็ตพื้นฐาน -->
<form action="/contact" method="POST">
  <input type="text" name="name" placeholder="ชื่อ" value="" />
  <input type="email" name="email" placeholder="อีเมล" value="" />
  <textarea name="message" placeholder="ข้อความ"></textarea>

  <button type="reset">ล้างข้อมูล</button>
  <button type="submit">ส่งข้อมูล</button>
</form>

<!-- ปุ่มรีเซ็ตที่มีการยืนยัน -->
<form action="/application" method="POST" id="applicationForm">
  <fieldset>
    <legend>ข้อมูลส่วนตัว</legend>
    <input type="text" name="firstName" placeholder="ชื่อ" required />
    <input type="text" name="lastName" placeholder="นามสกุล" required />
    <input type="email" name="email" placeholder="อีเมล" required />
    <input type="tel" name="phone" placeholder="เบอร์โทร" />
  </fieldset>

  <fieldset>
    <legend>ข้อมูลการสมัคร</legend>
    <select name="position" required>
      <option value="">-- เลือกตำแหน่ง --</option>
      <option value="developer">นักพัฒนา</option>
      <option value="designer">นักออกแบบ</option>
      <option value="manager">ผู้จัดการ</option>
    </select>
    <textarea name="experience" placeholder="ประสบการณ์การทำงาน"></textarea>
  </fieldset>

  <div class="form-actions">
    <button
      type="reset"
      onclick="return confirmReset()"
      class="btn btn-warning"
    >
      🗑️ ล้างข้อมูลทั้งหมด
    </button>
    <button type="submit" class="btn btn-primary">📝 ส่งใบสมัคร</button>
  </div>
</form>

<script>
  function confirmReset() {
    return confirm(
      'คุณแน่ใจหรือไม่ที่จะล้างข้อมูลทั้งหมด? การกระทำนี้ไม่สามารถยกเลิกได้'
    );
  }

  // แสดงการแจ้งเตือนเมื่อรีเซ็ต
  document
    .getElementById('applicationForm')
    .addEventListener('reset', function () {
      setTimeout(() => {
        alert('ข้อมูลถูกล้างเรียบร้อยแล้ว');
      }, 100);
    });
</script>
```

#### Custom Reset กับ Local Storage

```html
<form id="autoSaveForm">
  <div class="form-header">
    <h3>แบบฟอร์มบันทึกอัตโนมัติ</h3>
    <small>ข้อมูลจะถูกบันทึกอัตโนมัติระหว่างการพิมพ์</small>
  </div>

  <div class="form-group">
    <label for="title">หัวข้อ</label>
    <input type="text" id="title" name="title" placeholder="หัวข้อของคุณ" />
  </div>

  <div class="form-group">
    <label for="content">เนื้อหา</label>
    <textarea
      id="content"
      name="content"
      rows="10"
      placeholder="เขียนเนื้อหาที่นี่..."
    ></textarea>
  </div>

  <div class="form-group">
    <label for="tags">แท็ก</label>
    <input
      type="text"
      id="tags"
      name="tags"
      placeholder="แท็ก1, แท็ก2, แท็ก3"
    />
  </div>

  <div class="form-status">
    <span id="saveStatus">ยังไม่ได้บันทึก</span>
  </div>

  <div class="form-actions">
    <button type="button" onclick="clearAllData()" class="btn btn-danger">
      🗑️ ล้างข้อมูลและหน่วยความจำ
    </button>
    <button type="reset" onclick="resetToSaved()" class="btn btn-secondary">
      ↺ กลับเป็นข้อมูลที่บันทึกล่าสุด
    </button>
    <button type="submit" class="btn btn-primary">💾 บันทึกและส่ง</button>
  </div>
</form>

<script>
  const formElements = ['title', 'content', 'tags'];
  const statusSpan = document.getElementById('saveStatus');

  // โหลดข้อมูลจาก Local Storage
  function loadSavedData() {
    formElements.forEach((fieldName) => {
      const saved = localStorage.getItem(`autoSave_${fieldName}`);
      if (saved) {
        document.getElementById(fieldName).value = saved;
      }
    });
    updateStatus('โหลดข้อมูลจากหน่วยความจำแล้ว');
  }

  // บันทึกข้อมูลลง Local Storage
  function saveData() {
    formElements.forEach((fieldName) => {
      const value = document.getElementById(fieldName).value;
      localStorage.setItem(`autoSave_${fieldName}`, value);
    });
    localStorage.setItem('autoSave_timestamp', new Date().toISOString());
    updateStatus('บันทึกอัตโนมัติ: ' + new Date().toLocaleTimeString());
  }

  // ล้างข้อมูลทั้งหมด
  function clearAllData() {
    if (
      confirm(
        'คุณต้องการล้างข้อมูลทั้งหมดรวมถึงที่บันทึกไว้ในหน่วยความจำหรือไม่?'
      )
    ) {
      // ล้างฟอร์ม
      document.getElementById('autoSaveForm').reset();

      // ล้าง Local Storage
      formElements.forEach((fieldName) => {
        localStorage.removeItem(`autoSave_${fieldName}`);
      });
      localStorage.removeItem('autoSave_timestamp');

      updateStatus('ล้างข้อมูลทั้งหมดแล้ว');
    }
  }

  // รีเซ็ตเป็นข้อมูลที่บันทึกล่าสุด
  function resetToSaved() {
    const timestamp = localStorage.getItem('autoSave_timestamp');
    if (timestamp) {
      loadSavedData();
      updateStatus(
        'กลับเป็นข้อมูลที่บันทึกล่าสุด: ' + new Date(timestamp).toLocaleString()
      );
    } else {
      document.getElementById('autoSaveForm').reset();
      updateStatus('ไม่มีข้อมูลที่บันทึกไว้');
    }
  }

  function updateStatus(message) {
    statusSpan.textContent = message;
    statusSpan.style.color = 'green';
    setTimeout(() => {
      statusSpan.style.color = '';
    }, 3000);
  }

  // Auto-save ทุก 2 วินาที
  formElements.forEach((fieldName) => {
    document.getElementById(fieldName).addEventListener('input', () => {
      clearTimeout(window.autoSaveTimer);
      window.autoSaveTimer = setTimeout(saveData, 2000);
    });
  });

  // โหลดข้อมูลเมื่อเริ่มต้น
  window.addEventListener('load', loadSavedData);
</script>
```

## 3. Attributes สำคัญของ `<button>`

### 3.1 Form-related Attributes

```html
<form action="/submit" method="POST" id="mainForm">
  <input type="text" name="username" required />
  <input type="password" name="password" required />
</form>

<!-- ปุ่มที่อยู่นอกฟอร์ม -->
<button type="submit" form="mainForm">ส่งข้อมูล</button>

<!-- ปุ่มที่เปลี่ยน action -->
<button type="submit" form="mainForm" formaction="/login">เข้าสู่ระบบ</button>
<button type="submit" form="mainForm" formaction="/register">
  สมัครสมาชิก
</button>

<!-- ปุ่มที่เปลี่ยน method -->
<button type="submit" form="mainForm" formmethod="GET">ค้นหา</button>

<!-- ปุ่มที่ข้าม validation -->
<button type="submit" form="mainForm" formnovalidate>บันทึกร่าง</button>

<!-- ปุ่มที่เปิดในหน้าใหม่ -->
<button type="submit" form="mainForm" formtarget="_blank">
  ส่งและเปิดในแท็บใหม่
</button>
```

### 3.2 Accessibility Attributes

```html
<!-- ปุ่มสำหรับ Screen Reader -->
<button type="button" aria-label="ปิดหน้าต่าง" onclick="closeModal()">✕</button>

<!-- ปุ่มที่มีคำอธิบาย -->
<button type="button" aria-describedby="help-text" onclick="showHelp()">
  ❓ ช่วยเหลือ
</button>
<div id="help-text" hidden>คลิกเพื่อดูวิธีการใช้งาน</div>

<!-- ปุ่มที่มีสถานะ -->
<button type="button" aria-pressed="false" onclick="toggleNotifications(this)">
  🔔 การแจ้งเตือน
</button>

<script>
  function toggleNotifications(btn) {
    const pressed = btn.getAttribute('aria-pressed') === 'true';
    btn.setAttribute('aria-pressed', !pressed);
    btn.textContent = pressed ? '🔔 การแจ้งเตือน' : '🔕 ปิดการแจ้งเตือน';
  }
</script>
```

### 3.3 State Attributes

```html
<!-- ปุ่มที่ปิดการใช้งาน -->
<button type="submit" disabled>ไม่สามารถส่งได้</button>

<!-- ปุ่มที่เปิด/ปิดตามเงื่อนไข -->
<form id="termsForm">
  <label>
    <input type="checkbox" id="agreeTerms" onchange="toggleSubmit()" />
    ยอมรับเงื่อนไขการใช้งาน
  </label>

  <button type="submit" id="submitBtn" disabled>ส่งข้อมูล</button>
</form>

<script>
  function toggleSubmit() {
    const checkbox = document.getElementById('agreeTerms');
    const submitBtn = document.getElementById('submitBtn');
    submitBtn.disabled = !checkbox.checked;
  }
</script>
```

## 4. ตัวอย่างการใช้งานขั้นสูง

### 4.1 Multi-step Form กับ Navigation Buttons

```html
<form id="multiStepForm" action="/submit" method="POST">
  <!-- Progress Bar -->
  <div class="progress-bar">
    <div class="step active" data-step="1">1. ข้อมูลส่วนตัว</div>
    <div class="step" data-step="2">2. ข้อมูลการติดต่อ</div>
    <div class="step" data-step="3">3. ความสนใจ</div>
    <div class="step" data-step="4">4. ยืนยันข้อมูล</div>
  </div>

  <!-- Step 1: ข้อมูลส่วนตัว -->
  <div class="form-step" id="step1">
    <h3>ข้อมูลส่วนตัว</h3>
    <div class="form-group">
      <label for="firstName">ชื่อ *</label>
      <input type="text" id="firstName" name="firstName" required />
    </div>
    <div class="form-group">
      <label for="lastName">นามสกุล *</label>
      <input type="text" id="lastName" name="lastName" required />
    </div>
    <div class="form-group">
      <label for="birthDate">วันเกิด</label>
      <input type="date" id="birthDate" name="birthDate" />
    </div>
  </div>

  <!-- Step 2: ข้อมูลการติดต่อ -->
  <div class="form-step" id="step2" style="display: none;">
    <h3>ข้อมูลการติดต่อ</h3>
    <div class="form-group">
      <label for="email">อีเมล *</label>
      <input type="email" id="email" name="email" required />
    </div>
    <div class="form-group">
      <label for="phone">เบอร์โทรศัพท์</label>
      <input type="tel" id="phone" name="phone" />
    </div>
    <div class="form-group">
      <label for="address">ที่อยู่</label>
      <textarea id="address" name="address" rows="3"></textarea>
    </div>
  </div>

  <!-- Step 3: ความสนใจ -->
  <div class="form-step" id="step3" style="display: none;">
    <h3>ความสนใจ</h3>
    <div class="form-group">
      <label>หัวข้อที่สนใจ (เลือกได้หลายข้อ)</label>
      <div class="checkbox-grid">
        <label
          ><input type="checkbox" name="interests" value="technology" />
          เทคโนโลยี</label
        >
        <label
          ><input type="checkbox" name="interests" value="sports" /> กีฬา</label
        >
        <label
          ><input type="checkbox" name="interests" value="music" /> ดนตรี</label
        >
        <label
          ><input type="checkbox" name="interests" value="travel" />
          การเดินทาง</label
        >
      </div>
    </div>
  </div>

  <!-- Step 4: ยืนยันข้อมูล -->
  <div class="form-step" id="step4" style="display: none;">
    <h3>ยืนยันข้อมูล</h3>
    <div id="summaryData"></div>
    <div class="form-group">
      <label>
        <input type="checkbox" id="confirmData" required />
        ข้าพเจ้ายืนยันว่าข้อมูลที่ให้ไว้ถูกต้อง
      </label>
    </div>
  </div>

  <!-- Navigation Buttons -->
  <div class="form-navigation">
    <button
      type="button"
      id="prevBtn"
      onclick="changeStep(-1)"
      style="display: none;"
    >
      ← ย้อนกลับ
    </button>

    <div class="step-info">
      ขั้นตอนที่ <span id="currentStepNum">1</span> จาก 4
    </div>

    <button type="button" id="nextBtn" onclick="changeStep(1)">ถัดไป →</button>

    <button type="submit" id="submitBtn" style="display: none;">
      ส่งข้อมูล
    </button>
  </div>
</form>

<script>
  let currentStep = 1;
  const totalSteps = 4;

  function changeStep(direction) {
    // ตรวจสอบข้อมูลก่อนไปขั้นตอนถัดไป
    if (direction === 1 && !validateCurrentStep()) {
      return;
    }

    // ซ่อนขั้นตอนปัจจุบัน
    document.getElementById(`step${currentStep}`).style.display = 'none';
    document
      .querySelector(`.step[data-step="${currentStep}"]`)
      .classList.remove('active');

    // เปลี่ยนขั้นตอน
    currentStep += direction;

    // แสดงขั้นตอนใหม่
    document.getElementById(`step${currentStep}`).style.display = 'block';
    document
      .querySelector(`.step[data-step="${currentStep}"]`)
      .classList.add('active');

    // อัปเดตปุ่ม
    updateNavigationButtons();

    // แสดงสรุปข้อมูลในขั้นตอนสุดท้าย
    if (currentStep === totalSteps) {
      showSummary();
    }
  }

  function updateNavigationButtons() {
    const prevBtn = document.getElementById('prevBtn');
    const nextBtn = document.getElementById('nextBtn');
    const submitBtn = document.getElementById('submitBtn');
    const stepNum = document.getElementById('currentStepNum');

    stepNum.textContent = currentStep;

    // ปุ่มย้อนกลับ
    prevBtn.style.display = currentStep === 1 ? 'none' : 'inline-block';

    // ปุ่มถัดไป/ส่ง
    if (currentStep === totalSteps) {
      nextBtn.style.display = 'none';
      submitBtn.style.display = 'inline-block';
    } else {
      nextBtn.style.display = 'inline-block';
      submitBtn.style.display = 'none';
    }
  }

  function validateCurrentStep() {
    const currentStepDiv = document.getElementById(`step${currentStep}`);
    const requiredInputs = currentStepDiv.querySelectorAll('[required]');

    for (let input of requiredInputs) {
      if (!input.value.trim()) {
        alert(`กรุณากรอก${input.previousElementSibling.textContent}`);
        input.focus();
        return false;
      }
    }

    return true;
  }

  function showSummary() {
    const summaryDiv = document.getElementById('summaryData');
    const formData = new FormData(document.getElementById('multiStepForm'));

    let summary = '<div class="summary-section">';
    summary += '<h4>ข้อมูลส่วนตัว</h4>';
    summary += `<p>ชื่อ: ${formData.get('firstName')} ${formData.get(
      'lastName'
    )}</p>`;
    summary += `<p>วันเกิด: ${formData.get('birthDate') || 'ไม่ระบุ'}</p>`;

    summary += '<h4>ข้อมูลการติดต่อ</h4>';
    summary += `<p>อีเมล: ${formData.get('email')}</p>`;
    summary += `<p>เบอร์โทร: ${formData.get('phone') || 'ไม่ระบุ'}</p>`;
    summary += `<p>ที่อยู่: ${formData.get('address') || 'ไม่ระบุ'}</p>`;

    const interests = formData.getAll('interests');
    summary += '<h4>ความสนใจ</h4>';
    summary += `<p>${
      interests.length > 0 ? interests.join(', ') : 'ไม่ได้เลือก'
    }</p>`;
    summary += '</div>';

    summaryDiv.innerHTML = summary;
  }
</script>
```

### 4.2 Dynamic Button States

```html
<div class="action-panel">
  <h3>การจัดการไฟล์</h3>

  <div class="file-upload">
    <input
      type="file"
      id="fileInput"
      multiple
      onchange="handleFileSelect(event)"
    />
    <button
      type="button"
      onclick="document.getElementById('fileInput').click()"
      class="btn btn-primary"
    >
      📁 เลือกไฟล์
    </button>
  </div>

  <div class="file-list" id="fileList"></div>

  <div class="action-buttons">
    <button type="button" id="selectAllBtn" onclick="selectAllFiles()" disabled>
      ☑️ เลือกทั้งหมด
    </button>

    <button
      type="button"
      id="deselectAllBtn"
      onclick="deselectAllFiles()"
      disabled
    >
      ☐ ไม่เลือกทั้งหมด
    </button>

    <button
      type="button"
      id="deleteSelectedBtn"
      onclick="deleteSelected()"
      class="btn btn-danger"
      disabled
    >
      🗑️ ลบที่เลือก
    </button>

    <button
      type="button"
      id="uploadBtn"
      onclick="uploadFiles()"
      class="btn btn-success"
      disabled
    >
      ⬆️ อัปโหลด
    </button>
  </div>

  <div class="upload-progress" id="uploadProgress" style="display: none;">
    <div class="progress-bar">
      <div class="progress-fill" id="progressFill"></div>
    </div>
    <div class="progress-text" id="progressText">0%</div>
    <button type="button" onclick="cancelUpload()" class="btn btn-secondary">
      ยกเลิก
    </button>
  </div>
</div>

<script>
  let selectedFiles = [];
  let selectedFileIds = new Set();

  function handleFileSelect(event) {
    const files = Array.from(event.target.files);
    selectedFiles = selectedFiles.concat(files);
    renderFileList();
    updateButtonStates();
  }

  function renderFileList() {
    const fileList = document.getElementById('fileList');
    fileList.innerHTML = '';

    selectedFiles.forEach((file, index) => {
      const fileItem = document.createElement('div');
      fileItem.className = 'file-item';
      fileItem.innerHTML = `
      <label>
        <input type="checkbox" value="${index}" onchange="updateSelection()">
        <span class="file-name">${file.name}</span>
        <span class="file-size">(${formatFileSize(file.size)})</span>
      </label>
      <button type="button" onclick="removeFile(${index})" class="btn btn-small">✕</button>
    `;
      fileList.appendChild(fileItem);
    });
  }

  function updateSelection() {
    const checkboxes = document.querySelectorAll(
      '.file-item input[type="checkbox"]'
    );
    selectedFileIds.clear();

    checkboxes.forEach((checkbox) => {
      if (checkbox.checked) {
        selectedFileIds.add(parseInt(checkbox.value));
      }
    });

    updateButtonStates();
  }

  function updateButtonStates() {
    const hasFiles = selectedFiles.length > 0;
    const hasSelected = selectedFileIds.size > 0;
    const allSelected =
      selectedFileIds.size === selectedFiles.length && hasFiles;

    // ปุ่มเลือก/ไม่เลือกทั้งหมด
    document.getElementById('selectAllBtn').disabled = !hasFiles || allSelected;
    document.getElementById('deselectAllBtn').disabled = !hasSelected;

    // ปุ่มลบและอัปโหลด
    document.getElementById('deleteSelectedBtn').disabled = !hasSelected;
    document.getElementById('uploadBtn').disabled = !hasFiles;

    // อัปเดตข้อความปุ่ม
    const uploadBtn = document.getElementById('uploadBtn');
    uploadBtn.textContent = `⬆️ อัปโหลด (${selectedFiles.length} ไฟล์)`;

    const deleteBtn = document.getElementById('deleteSelectedBtn');
    deleteBtn.textContent = hasSelected
      ? `🗑️ ลบที่เลือก (${selectedFileIds.size})`
      : '🗑️ ลบที่เลือก';
  }

  function selectAllFiles() {
    const checkboxes = document.querySelectorAll(
      '.file-item input[type="checkbox"]'
    );
    checkboxes.forEach((checkbox) => (checkbox.checked = true));
    updateSelection();
  }

  function deselectAllFiles() {
    const checkboxes = document.querySelectorAll(
      '.file-item input[type="checkbox"]'
    );
    checkboxes.forEach((checkbox) => (checkbox.checked = false));
    updateSelection();
  }

  function removeFile(index) {
    selectedFiles.splice(index, 1);
    renderFileList();
    updateButtonStates();
  }

  function deleteSelected() {
    if (confirm(`คุณต้องการลบ ${selectedFileIds.size} ไฟล์ที่เลือกหรือไม่?`)) {
      // ลบไฟล์ที่เลือก (เรียงจากมากไปน้อยเพื่อไม่ให้ index เปลี่ยน)
      const sortedIds = Array.from(selectedFileIds).sort((a, b) => b - a);
      sortedIds.forEach((id) => selectedFiles.splice(id, 1));

      selectedFileIds.clear();
      renderFileList();
      updateButtonStates();
    }
  }

  let uploadCancelled = false;

  function uploadFiles() {
    if (selectedFiles.length === 0) return;

    // แสดง progress bar
    document.getElementById('uploadProgress').style.display = 'block';
    document.getElementById('uploadBtn').disabled = true;

    uploadCancelled = false;
    simulateUpload();
  }

  function simulateUpload() {
    let progress = 0;
    const progressFill = document.getElementById('progressFill');
    const progressText = document.getElementById('progressText');

    const interval = setInterval(() => {
      if (uploadCancelled) {
        clearInterval(interval);
        document.getElementById('uploadProgress').style.display = 'none';
        document.getElementById('uploadBtn').disabled = false;
        return;
      }

      progress += Math.random() * 10;
      if (progress >= 100) {
        progress = 100;
        clearInterval(interval);

        // อัปโหลดเสร็จ
        setTimeout(() => {
          document.getElementById('uploadProgress').style.display = 'none';
          alert('อัปโหลดเสร็จสิ้น!');
          selectedFiles = [];
          selectedFileIds.clear();
          renderFileList();
          updateButtonStates();
        }, 500);
      }

      progressFill.style.width = progress + '%';
      progressText.textContent = Math.round(progress) + '%';
    }, 200);
  }

  function cancelUpload() {
    if (confirm('คุณต้องการยกเลิกการอัปโหลดหรือไม่?')) {
      uploadCancelled = true;
    }
  }

  function formatFileSize(bytes) {
    if (bytes === 0) return '0 Bytes';
    const k = 1024;
    const sizes = ['Bytes', 'KB', 'MB', 'GB'];
    const i = Math.floor(Math.log(bytes) / Math.log(k));
    return parseFloat((bytes / Math.pow(k, i)).toFixed(2)) + ' ' + sizes[i];
  }
</script>
```

## 5. Best Practices

### 5.1 การเลือกใช้ Button Type

```html
<!-- ✅ ใช้ type ที่เหมาะสม -->
<button type="button" onclick="showModal()">เปิดหน้าต่าง</button>
<!-- ไม่ส่งฟอร์ม -->
<button type="submit">ส่งข้อมูล</button>
<!-- ส่งฟอร์ม -->
<button type="reset">ล้างข้อมูล</button>
<!-- รีเซ็ตฟอร์ม -->

<!-- ❌ หลีกเลี่ยง -->
<button onclick="submitForm()">ส่งข้อมูล</button>
<!-- ไม่ระบุ type อาจทำงานไม่ถูกต้อง -->
```

### 5.2 Accessibility และ UX

```html
<!-- ✅ ควรทำ -->
<button type="button" aria-label="ปิดหน้าต่าง" title="คลิกเพื่อปิดหน้าต่าง">
  ✕
</button>

<!-- ✅ ใช้ loading state -->
<button type="submit" id="submitBtn">
  <span class="btn-text">ส่งข้อมูล</span>
  <span class="btn-loading" style="display: none;">กำลังส่ง...</span>
</button>

<!-- ❌ หลีกเลี่ยง -->
<button>✕</button>
<!-- ไม่มีคำอธิบาย -->
<button type="submit" onclick="this.disabled=true">ส่ง</button>
<!-- ปิดการใช้งานแบบง่ายเกินไป -->
```

### 5.3 การจัดกลุ่มและการจัดเรียง

```html
<!-- ✅ จัดกลุ่มปุ่มที่เกี่ยวข้อง -->
<div class="form-actions">
  <button type="reset" class="btn btn-secondary">ยกเลิก</button>
  <button type="submit" class="btn btn-primary">บันทึก</button>
</div>

<!-- ✅ เรียงลำดับตามความสำคัญ -->
<div class="modal-footer">
  <button type="button" class="btn btn-secondary" data-dismiss="modal">
    ปิด
  </button>
  <button type="button" class="btn btn-danger">ลบ</button>
  <button type="button" class="btn btn-primary">ยืนยัน</button>
</div>
```

---

**สรุป**: การใช้ `<button>` อย่างถูกต้องกับ type ที่เหมาะสม จะช่วยให้ฟอร์มทำงานได้อย่างมีประสิทธิภาพ มี UX ที่ดี และรองรับ Accessibility
