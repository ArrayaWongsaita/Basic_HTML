# การจัดกลุ่มฟอร์ม: `<fieldset>` และ `<legend>`

## 1. ภาพรวม Form Grouping

การจัดกลุ่มข้อมูลในฟอร์มเป็นสิ่งสำคัญสำหรับ UX และ Accessibility โดย `<fieldset>` และ `<legend>` เป็น elements หลักที่ใช้จัดกลุ่มและให้ชื่อกลุ่มของ form controls

**ประโยชน์ของการใช้ fieldset:**

- จัดกลุ่มข้อมูลที่เกี่ยวข้องกัน
- ช่วย Screen Reader ในการอ่านเนื้อหา
- ปรับปรุง UX ด้วยการจัดระเบียบ
- ควบคุมการเปิด/ปิดกลุ่มข้อมูล

## 2. `<fieldset>` Element

### 2.1 ภาพรวม `<fieldset>`

`<fieldset>` ใช้จัดกลุ่ม form controls ที่เกี่ยวข้องกันและแสดงเส้นขอบรอบกลุ่ม

**Syntax พื้นฐาน:**

```html
<fieldset>
  <legend>ชื่อกลุ่ม</legend>
  <!-- Form controls -->
</fieldset>
```

### 2.2 Attributes สำคัญของ `<fieldset>`

#### `disabled` Attribute

```html
<!-- ปิดการใช้งานทั้งกลุ่ม -->
<fieldset disabled>
  <legend>ข้อมูลที่ไม่สามารถแก้ไขได้</legend>
  <input type="text" name="lockedField1" value="ข้อมูลล็อค" />
  <input type="email" name="lockedField2" value="locked@email.com" />
  <select name="lockedSelect">
    <option value="option1">ตัวเลือก 1</option>
    <option value="option2" selected>ตัวเลือก 2</option>
  </select>
</fieldset>

<!-- การควบคุมแบบมีเงื่อนไข -->
<form id="applicationForm">
  <fieldset>
    <legend>ประเภทการสมัคร</legend>
    <label>
      <input
        type="radio"
        name="applicationType"
        value="student"
        onchange="toggleFieldsets()"
      />
      นักเรียน
    </label>
    <label>
      <input
        type="radio"
        name="applicationType"
        value="teacher"
        onchange="toggleFieldsets()"
      />
      ครู
    </label>
    <label>
      <input
        type="radio"
        name="applicationType"
        value="parent"
        onchange="toggleFieldsets()"
      />
      ผู้ปกครอง
    </label>
  </fieldset>

  <fieldset id="studentInfo" disabled>
    <legend>ข้อมูลนักเรียน</legend>
    <input type="text" name="studentId" placeholder="รหัสนักเรียน" />
    <input type="text" name="grade" placeholder="ชั้นเรียน" />
    <input type="text" name="section" placeholder="ห้อง" />
  </fieldset>

  <fieldset id="teacherInfo" disabled>
    <legend>ข้อมูลครู</legend>
    <input type="text" name="teacherId" placeholder="รหัสครู" />
    <input type="text" name="subject" placeholder="วิชาที่สอน" />
    <input type="text" name="department" placeholder="แผนก" />
  </fieldset>

  <fieldset id="parentInfo" disabled>
    <legend>ข้อมูลผู้ปกครอง</legend>
    <input type="text" name="parentName" placeholder="ชื่อผู้ปกครอง" />
    <input type="text" name="relationship" placeholder="ความสัมพันธ์" />
    <input type="text" name="childName" placeholder="ชื่อบุตร" />
  </fieldset>
</form>

<script>
  function toggleFieldsets() {
    const type = document.querySelector(
      'input[name="applicationType"]:checked'
    )?.value;

    // ปิดทุก fieldset ก่อน
    document.getElementById('studentInfo').disabled = true;
    document.getElementById('teacherInfo').disabled = true;
    document.getElementById('parentInfo').disabled = true;

    // เปิดเฉพาะที่เลือก
    if (type) {
      document.getElementById(type + 'Info').disabled = false;
    }
  }
</script>
```

#### `form` Attribute

```html
<form id="mainForm" action="/submit" method="POST">
  <input type="text" name="username" placeholder="ชื่อผู้ใช้" />
</form>

<!-- fieldset ที่อยู่นอกฟอร์มแต่เชื่อมโยงกัน -->
<fieldset form="mainForm">
  <legend>ข้อมูลเพิ่มเติม</legend>
  <input type="email" name="email" placeholder="อีเมล" />
  <input type="tel" name="phone" placeholder="เบอร์โทร" />
</fieldset>
```

#### `name` Attribute

```html
<fieldset name="personalInfo">
  <legend>ข้อมูลส่วนตัว</legend>
  <input type="text" name="firstName" placeholder="ชื่อ" />
  <input type="text" name="lastName" placeholder="นามสกุล" />
</fieldset>

<script>
  // เข้าถึง fieldset ผ่าน name
  const personalFieldset = document.querySelector(
    'fieldset[name="personalInfo"]'
  );
  console.log(personalFieldset.elements); // รายการ form controls ใน fieldset
</script>
```

## 3. `<legend>` Element

### 3.1 ภาพรวม `<legend>`

`<legend>` ใช้กำหนดชื่อหัวข้อของ `<fieldset>` และต้องเป็น child element แรกของ fieldset เท่านั้น

```html
<fieldset>
  <legend>ข้อมูลการติดต่อ</legend>
  <!-- form controls อื่นๆ -->
</fieldset>
```

### 3.2 การจัดรูปแบบ `<legend>`

#### การใช้ HTML ใน legend

```html
<fieldset>
  <legend>
    <span class="icon">📧</span>
    ข้อมูลการติดต่อ
    <span class="required">*</span>
  </legend>
  <input type="email" name="email" required />
  <input type="tel" name="phone" />
</fieldset>

<fieldset>
  <legend>
    <strong>ข้อมูลที่สำคัญ</strong>
    <br />
    <small>(กรุณากรอกให้ครบถ้วน)</small>
  </legend>
  <input type="text" name="importantData" required />
</fieldset>
```

#### การจัดรูปแบบด้วย CSS

```html
<style>
  .custom-fieldset {
    border: 2px solid #007bff;
    border-radius: 8px;
    padding: 20px;
    margin: 20px 0;
    background-color: #f8f9fa;
  }

  .custom-legend {
    background-color: #007bff;
    color: white;
    padding: 5px 15px;
    border-radius: 5px;
    font-weight: bold;
    border: none;
  }

  .icon-legend {
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 16px;
    color: #333;
    background: linear-gradient(45deg, #f0f0f0, #e0e0e0);
    padding: 8px 16px;
    border-radius: 20px;
    border: 1px solid #ccc;
  }

  .required-indicator {
    color: red;
    font-size: 18px;
  }
</style>

<fieldset class="custom-fieldset">
  <legend class="custom-legend">ข้อมูลผู้ใช้</legend>
  <input type="text" name="username" placeholder="ชื่อผู้ใช้" />
  <input type="password" name="password" placeholder="รหัสผ่าน" />
</fieldset>

<fieldset>
  <legend class="icon-legend">
    <span>👤</span>
    <span>ข้อมูลส่วนตัว</span>
    <span class="required-indicator">*</span>
  </legend>
  <input type="text" name="fullName" placeholder="ชื่อ-นามสกุล" required />
  <input type="date" name="birthDate" />
</fieldset>
```

## 4. ตัวอย่างการใช้งานแบบละเอียด

### 4.1 ฟอร์มสมัครงานแบบครบครัน

```html
<form
  action="/job-application"
  method="POST"
  enctype="multipart/form-data"
  class="job-application"
>
  <h1>ใบสมัครงาน</h1>

  <!-- ข้อมูลส่วนตัว -->
  <fieldset>
    <legend>
      <span class="step-number">1</span>
      ข้อมูลส่วนตัว
      <span class="required">*</span>
    </legend>

    <div class="form-row">
      <div class="form-group">
        <label for="title">คำนำหน้า</label>
        <select id="title" name="title" required>
          <option value="">-- เลือก --</option>
          <option value="mr">นาย</option>
          <option value="mrs">นาง</option>
          <option value="ms">นางสาว</option>
        </select>
      </div>

      <div class="form-group">
        <label for="firstName">ชื่อ *</label>
        <input type="text" id="firstName" name="firstName" required />
      </div>

      <div class="form-group">
        <label for="lastName">นามสกุล *</label>
        <input type="text" id="lastName" name="lastName" required />
      </div>
    </div>

    <div class="form-row">
      <div class="form-group">
        <label for="idCard">เลขประจำตัวประชาชน *</label>
        <input
          type="text"
          id="idCard"
          name="idCard"
          pattern="[0-9]{13}"
          placeholder="1234567890123"
          maxlength="13"
          required
        />
      </div>

      <div class="form-group">
        <label for="birthDate">วันเกิด</label>
        <input type="date" id="birthDate" name="birthDate" />
      </div>
    </div>

    <fieldset class="nested-fieldset">
      <legend>เพศ</legend>
      <div class="radio-group">
        <label
          ><input type="radio" name="gender" value="male" required /> ชาย</label
        >
        <label
          ><input type="radio" name="gender" value="female" required />
          หญิง</label
        >
        <label
          ><input type="radio" name="gender" value="other" required />
          อื่นๆ</label
        >
      </div>
    </fieldset>
  </fieldset>

  <!-- ข้อมูลการติดต่อ -->
  <fieldset>
    <legend>
      <span class="step-number">2</span>
      ข้อมูลการติดต่อ
      <span class="required">*</span>
    </legend>

    <div class="form-group">
      <label for="email">อีเมล *</label>
      <input
        type="email"
        id="email"
        name="email"
        required
        placeholder="example@email.com"
      />
    </div>

    <div class="form-row">
      <div class="form-group">
        <label for="phone">เบอร์โทรศัพท์ *</label>
        <input
          type="tel"
          id="phone"
          name="phone"
          required
          pattern="[0-9]{10}"
          placeholder="0812345678"
        />
      </div>

      <div class="form-group">
        <label for="lineId">Line ID</label>
        <input type="text" id="lineId" name="lineId" placeholder="@lineid" />
      </div>
    </div>

    <div class="form-group">
      <label for="address">ที่อยู่ปัจจุบัน</label>
      <textarea
        id="address"
        name="address"
        rows="3"
        placeholder="บ้านเลขที่ ซอย ถนน แขวง/ตำบล เขต/อำเภอ จังหวัด รหัสไปรษณีย์"
      ></textarea>
    </div>
  </fieldset>

  <!-- ข้อมูลการศึกษา -->
  <fieldset>
    <legend>
      <span class="step-number">3</span>
      ข้อมูลการศึกษา
    </legend>

    <div class="education-entry">
      <h4>การศึกษาสูงสุด</h4>
      <div class="form-row">
        <div class="form-group">
          <label for="education-level">ระดับการศึกษา</label>
          <select id="education-level" name="educationLevel">
            <option value="">-- เลือกระดับการศึกษา --</option>
            <option value="high-school">มัธยมศึกษา</option>
            <option value="diploma">อนุปริญญา/ปวส.</option>
            <option value="bachelor">ปริญญาตรี</option>
            <option value="master">ปริญญาโท</option>
            <option value="doctoral">ปริญญาเอก</option>
          </select>
        </div>

        <div class="form-group">
          <label for="major">สาขาวิชา</label>
          <input
            type="text"
            id="major"
            name="major"
            placeholder="เช่น วิศวกรรมคอมพิวเตอร์"
          />
        </div>
      </div>

      <div class="form-row">
        <div class="form-group">
          <label for="university">สถาบันการศึกษา</label>
          <input
            type="text"
            id="university"
            name="university"
            placeholder="ชื่อมหาวิทยาลัย/วิทยาลัย"
          />
        </div>

        <div class="form-group">
          <label for="gpa">เกรดเฉลี่ย (GPA)</label>
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
          <label for="graduation-year">ปีที่จบการศึกษา</label>
          <input
            type="number"
            id="graduation-year"
            name="graduationYear"
            min="1990"
            max="2030"
            placeholder="2567"
          />
        </div>
      </div>
    </div>
  </fieldset>

  <!-- ประสบการณ์การทำงาน -->
  <fieldset>
    <legend>
      <span class="step-number">4</span>
      ประสบการณ์การทำงาน
    </legend>

    <div class="form-group">
      <label>มีประสบการณ์การทำงานหรือไม่?</label>
      <div class="radio-group">
        <label
          ><input
            type="radio"
            name="hasExperience"
            value="yes"
            onchange="toggleExperience(true)"
          />
          มี</label
        >
        <label
          ><input
            type="radio"
            name="hasExperience"
            value="no"
            onchange="toggleExperience(false)"
          />
          ไม่มี</label
        >
      </div>
    </div>

    <div id="experienceDetails" style="display: none;">
      <div class="experience-entry">
        <h4>งานล่าสุด</h4>
        <div class="form-row">
          <div class="form-group">
            <label for="company">ชื่อบริษัท</label>
            <input type="text" id="company" name="company" />
          </div>

          <div class="form-group">
            <label for="position">ตำแหน่ง</label>
            <input type="text" id="position" name="position" />
          </div>
        </div>

        <div class="form-row">
          <div class="form-group">
            <label for="work-start">วันที่เริ่มงาน</label>
            <input type="date" id="work-start" name="workStart" />
          </div>

          <div class="form-group">
            <label for="work-end">วันที่ลาออก</label>
            <input type="date" id="work-end" name="workEnd" />
          </div>

          <div class="form-group">
            <label for="salary">เงินเดือนสุดท้าย</label>
            <input
              type="number"
              id="salary"
              name="salary"
              min="0"
              step="1000"
            />
          </div>
        </div>

        <div class="form-group">
          <label for="job-description">หน้าที่รับผิดชอบ</label>
          <textarea
            id="job-description"
            name="jobDescription"
            rows="4"
            placeholder="อธิบายหน้าที่และความรับผิดชอบในงานที่ผ่านมา"
          ></textarea>
        </div>
      </div>
    </div>
  </fieldset>

  <!-- ทักษะและความสามารถ -->
  <fieldset>
    <legend>
      <span class="step-number">5</span>
      ทักษะและความสามารถ
    </legend>

    <div class="form-group">
      <label>ทักษะด้านคอมพิวเตอร์</label>
      <div class="checkbox-grid">
        <label
          ><input
            type="checkbox"
            name="computerSkills"
            value="microsoft-office"
          />
          Microsoft Office</label
        >
        <label
          ><input type="checkbox" name="computerSkills" value="photoshop" />
          Adobe Photoshop</label
        >
        <label
          ><input type="checkbox" name="computerSkills" value="html-css" />
          HTML/CSS</label
        >
        <label
          ><input type="checkbox" name="computerSkills" value="javascript" />
          JavaScript</label
        >
        <label
          ><input type="checkbox" name="computerSkills" value="python" />
          Python</label
        >
        <label
          ><input type="checkbox" name="computerSkills" value="database" />
          ฐานข้อมูล</label
        >
      </div>
    </div>

    <div class="form-group">
      <label>ทักษะด้านภาษา</label>
      <div class="language-skills">
        <div class="language-item">
          <label for="english-level">ภาษาอังกฤษ:</label>
          <select id="english-level" name="englishLevel">
            <option value="">-- เลือกระดับ --</option>
            <option value="basic">พื้นฐาน</option>
            <option value="intermediate">ปานกลาง</option>
            <option value="advanced">ดี</option>
            <option value="native">คล่องแคล่ว</option>
          </select>
        </div>

        <div class="language-item">
          <label for="chinese-level">ภาษาจีน:</label>
          <select id="chinese-level" name="chineseLevel">
            <option value="">-- เลือกระดับ --</option>
            <option value="basic">พื้นฐาน</option>
            <option value="intermediate">ปานกลาง</option>
            <option value="advanced">ดี</option>
            <option value="native">คล่องแคล่ว</option>
          </select>
        </div>
      </div>
    </div>

    <div class="form-group">
      <label for="other-skills">ทักษะอื่นๆ</label>
      <textarea
        id="other-skills"
        name="otherSkills"
        rows="3"
        placeholder="ระบุทักษะ ความสามารถ หรือใบประกาศนียบัตรอื่นๆ ที่มี"
      ></textarea>
    </div>
  </fieldset>

  <!-- ไฟล์เอกสาร -->
  <fieldset>
    <legend>
      <span class="step-number">6</span>
      เอกสารประกอบการสมัคร
    </legend>

    <div class="form-group">
      <label for="resume">เรซูเม่/ประวัติส่วนตัว *</label>
      <input
        type="file"
        id="resume"
        name="resume"
        accept=".pdf,.doc,.docx"
        required
      />
      <small>รองรับไฟล์: PDF, DOC, DOCX (ขนาดไม่เกิน 5MB)</small>
    </div>

    <div class="form-group">
      <label for="portfolio">ผลงาน (Portfolio)</label>
      <input
        type="file"
        id="portfolio"
        name="portfolio"
        accept=".pdf,.zip,.rar"
        multiple
      />
      <small>รองรับไฟล์: PDF, ZIP, RAR (ขนาดไฟล์รวมไม่เกิน 20MB)</small>
    </div>

    <div class="form-group">
      <label for="certificates">ใบประกาศนียบัตร/ใบรับรอง</label>
      <input
        type="file"
        id="certificates"
        name="certificates"
        accept=".pdf,.jpg,.png"
        multiple
      />
      <small>รองรับไฟล์: PDF, JPG, PNG</small>
    </div>
  </fieldset>

  <!-- ข้อมูลเพิ่มเติม -->
  <fieldset>
    <legend>
      <span class="step-number">7</span>
      ข้อมูลเพิ่มเติม
    </legend>

    <div class="form-group">
      <label for="expected-salary">เงินเดือนที่คาดหวัง (บาท)</label>
      <input
        type="number"
        id="expected-salary"
        name="expectedSalary"
        min="0"
        step="1000"
        placeholder="25000"
      />
    </div>

    <div class="form-group">
      <label for="start-date">วันที่สามารถเริ่มงานได้</label>
      <input type="date" id="start-date" name="startDate" min="2024-01-01" />
    </div>

    <div class="form-group">
      <label for="motivation">เหตุผลที่สนใจสมัครงานตำแหน่งนี้</label>
      <textarea
        id="motivation"
        name="motivation"
        rows="5"
        placeholder="อธิบายเหตุผลที่สนใจและแรงจูงใจในการสมัครงานตำแหน่งนี้"
      ></textarea>
    </div>

    <div class="form-group">
      <label for="additional-info">ข้อมูลเพิ่มเติมที่ต้องการแจ้ง</label>
      <textarea
        id="additional-info"
        name="additionalInfo"
        rows="3"
        placeholder="ข้อมูลอื่นๆ ที่คิดว่าจะเป็นประโยชน์ต่อการพิจารณา"
      ></textarea>
    </div>
  </fieldset>

  <!-- การยืนยัน -->
  <fieldset>
    <legend>
      <span class="step-number">8</span>
      การยืนยันข้อมูล
    </legend>

    <div class="confirmation-section">
      <div class="form-group">
        <label class="checkbox-label">
          <input
            type="checkbox"
            name="dataAccuracy"
            value="confirmed"
            required
          />
          ข้าพเจ้ายืนยันว่าข้อมูลที่ให้ไว้ข้างต้นเป็นความจริงทุกประการ
        </label>
      </div>

      <div class="form-group">
        <label class="checkbox-label">
          <input
            type="checkbox"
            name="privacyConsent"
            value="agreed"
            required
          />
          ข้าพเจ้ายินยอมให้บริษัทเก็บรวบรวมและใช้ข้อมูลส่วนบุคคลเพื่อการพิจารณาคัดเลือก
        </label>
      </div>

      <div class="form-group">
        <label class="checkbox-label">
          <input type="checkbox" name="newsletter" value="yes" />
          ต้องการรับข่าวสารและการประชาสัมพันธ์จากบริษัท
        </label>
      </div>
    </div>
  </fieldset>

  <!-- ปุ่มส่ง -->
  <div class="form-actions">
    <button
      type="reset"
      class="btn btn-secondary"
      onclick="return confirm('คุณต้องการล้างข้อมูลทั้งหมดหรือไม่?')"
    >
      ล้างข้อมูล
    </button>
    <button type="submit" class="btn btn-primary">ส่งใบสมัครงาน</button>
  </div>
</form>

<script>
  function toggleExperience(hasExp) {
    const experienceDetails = document.getElementById('experienceDetails');
    experienceDetails.style.display = hasExp ? 'block' : 'none';

    // ตั้งค่า required สำหรับฟิลด์ในส่วนประสบการณ์
    const experienceInputs =
      experienceDetails.querySelectorAll('input, textarea');
    experienceInputs.forEach((input) => {
      input.required = hasExp;
    });
  }
</script>
```

### 4.2 ฟอร์มการสั่งซื้อสินค้า

```html
<form action="/order" method="POST" class="order-form">
  <h1>ใบสั่งซื้อสินค้า</h1>

  <!-- ข้อมูลสินค้า -->
  <fieldset>
    <legend>🛒 รายการสินค้า</legend>

    <div class="product-list" id="productList">
      <div class="product-item">
        <div class="form-row">
          <div class="form-group">
            <label>สินค้า</label>
            <select name="products[0][name]" required>
              <option value="">-- เลือกสินค้า --</option>
              <option value="laptop" data-price="25000">
                Laptop (25,000 บาท)
              </option>
              <option value="mouse" data-price="500">Mouse (500 บาท)</option>
              <option value="keyboard" data-price="1500">
                Keyboard (1,500 บาท)
              </option>
            </select>
          </div>

          <div class="form-group">
            <label>จำนวน</label>
            <input
              type="number"
              name="products[0][quantity]"
              min="1"
              value="1"
              onchange="calculateTotal()"
              required
            />
          </div>

          <div class="form-group">
            <label>ราคาต่อหน่วย</label>
            <input type="number" name="products[0][price]" readonly />
          </div>

          <div class="form-group">
            <label>รวม</label>
            <input type="number" name="products[0][total]" readonly />
          </div>

          <button
            type="button"
            onclick="removeProduct(this)"
            class="btn btn-danger btn-small"
          >
            ลบ
          </button>
        </div>
      </div>
    </div>

    <div class="product-actions">
      <button type="button" onclick="addProduct()" class="btn btn-secondary">
        + เพิ่มสินค้า
      </button>
      <div class="total-price">ยอดรวม: <span id="grandTotal">0</span> บาท</div>
    </div>
  </fieldset>

  <!-- ข้อมูลผู้สั่งซื้อ -->
  <fieldset>
    <legend>👤 ข้อมูลผู้สั่งซื้อ</legend>

    <div class="form-row">
      <div class="form-group">
        <label for="customer-name">ชื่อ-นามสกุล *</label>
        <input type="text" id="customer-name" name="customerName" required />
      </div>

      <div class="form-group">
        <label for="customer-email">อีเมล *</label>
        <input type="email" id="customer-email" name="customerEmail" required />
      </div>

      <div class="form-group">
        <label for="customer-phone">เบอร์โทรศัพท์ *</label>
        <input type="tel" id="customer-phone" name="customerPhone" required />
      </div>
    </div>
  </fieldset>

  <!-- ที่อยู่จัดส่ง -->
  <fieldset>
    <legend>🚚 ที่อยู่จัดส่ง</legend>

    <div class="form-group">
      <label class="checkbox-label">
        <input
          type="checkbox"
          id="sameAsCustomer"
          onchange="copyCustomerInfo()"
        />
        ใช้ข้อมูลเดียวกับผู้สั่งซื้อ
      </label>
    </div>

    <div id="shippingInfo">
      <div class="form-row">
        <div class="form-group">
          <label for="shipping-name">ชื่อผู้รับ *</label>
          <input type="text" id="shipping-name" name="shippingName" required />
        </div>

        <div class="form-group">
          <label for="shipping-phone">เบอร์โทรผู้รับ *</label>
          <input type="tel" id="shipping-phone" name="shippingPhone" required />
        </div>
      </div>

      <div class="form-group">
        <label for="shipping-address">ที่อยู่จัดส่ง *</label>
        <textarea
          id="shipping-address"
          name="shippingAddress"
          rows="3"
          required
          placeholder="บ้านเลขที่ ซอย ถนน แขวง/ตำบล เขต/อำเภอ จังหวัด รหัสไปรษณีย์"
        ></textarea>
      </div>

      <div class="form-group">
        <label for="delivery-note">หมายเหตุการจัดส่ง</label>
        <textarea
          id="delivery-note"
          name="deliveryNote"
          rows="2"
          placeholder="ข้อมูลเพิ่มเติมสำหรับการจัดส่ง เช่น เวลาที่สะดวกรับของ"
        ></textarea>
      </div>
    </div>
  </fieldset>

  <!-- การชำระเงิน -->
  <fieldset>
    <legend>💳 วิธีการชำระเงิน</legend>

    <div class="payment-methods">
      <div class="radio-group">
        <label>
          <input
            type="radio"
            name="paymentMethod"
            value="cash"
            onchange="togglePaymentDetails()"
            required
          />
          เก็บเงินปลายทาง
        </label>
        <label>
          <input
            type="radio"
            name="paymentMethod"
            value="transfer"
            onchange="togglePaymentDetails()"
            required
          />
          โอนเงินผ่านธนาคาร
        </label>
        <label>
          <input
            type="radio"
            name="paymentMethod"
            value="credit"
            onchange="togglePaymentDetails()"
            required
          />
          บัตรเครดิต
        </label>
      </div>
    </div>

    <div id="transferDetails" style="display: none;">
      <h4>ข้อมูลการโอนเงิน</h4>
      <div class="bank-info">
        <p><strong>ธนาคารกรุงเทพ</strong></p>
        <p>เลขที่บัญชี: 123-4-56789-0</p>
        <p>ชื่อบัญชี: บริษัท ABC จำกัด</p>
      </div>

      <div class="form-group">
        <label for="transfer-date">วันที่โอน</label>
        <input type="date" id="transfer-date" name="transferDate" />
      </div>

      <div class="form-group">
        <label for="transfer-time">เวลาที่โอน</label>
        <input type="time" id="transfer-time" name="transferTime" />
      </div>

      <div class="form-group">
        <label for="transfer-amount">จำนวนเงินที่โอน</label>
        <input
          type="number"
          id="transfer-amount"
          name="transferAmount"
          min="0"
          step="0.01"
        />
      </div>
    </div>

    <div id="creditDetails" style="display: none;">
      <h4>ข้อมูลบัตรเครดิต</h4>
      <div class="form-row">
        <div class="form-group">
          <label for="card-number">หมายเลขบัตร</label>
          <input
            type="text"
            id="card-number"
            name="cardNumber"
            pattern="[0-9]{16}"
            placeholder="1234567890123456"
            maxlength="16"
          />
        </div>

        <div class="form-group">
          <label for="expiry">วันหมดอายุ</label>
          <input type="month" id="expiry" name="expiry" />
        </div>

        <div class="form-group">
          <label for="cvv">CVV</label>
          <input
            type="text"
            id="cvv"
            name="cvv"
            pattern="[0-9]{3,4}"
            maxlength="4"
          />
        </div>
      </div>

      <div class="form-group">
        <label for="card-name">ชื่อบนบัตร</label>
        <input
          type="text"
          id="card-name"
          name="cardName"
          placeholder="ตามที่ปรากฏบนบัตร"
        />
      </div>
    </div>
  </fieldset>

  <!-- สรุปคำสั่งซื้อ -->
  <fieldset>
    <legend>📋 สรุปคำสั่งซื้อ</legend>

    <div class="order-summary" id="orderSummary">
      <!-- จะถูกเติมด้วย JavaScript -->
    </div>

    <div class="form-group">
      <label class="checkbox-label">
        <input type="checkbox" name="agreeTerms" required />
        ยอมรับ <a href="/terms" target="_blank">เงื่อนไขการสั่งซื้อ</a> *
      </label>
    </div>
  </fieldset>

  <div class="form-actions">
    <button type="button" onclick="previewOrder()" class="btn btn-secondary">
      ดูตัวอย่างใบสั่งซื้อ
    </button>
    <button type="submit" class="btn btn-primary">ยืนยันการสั่งซื้อ</button>
  </div>
</form>

<script>
  let productCount = 1;

  function addProduct() {
    const productList = document.getElementById('productList');
    const newProduct = document.createElement('div');
    newProduct.className = 'product-item';
    newProduct.innerHTML = `
    <div class="form-row">
      <div class="form-group">
        <label>สินค้า</label>
        <select name="products[${productCount}][name]" required onchange="updatePrice(this)">
          <option value="">-- เลือกสินค้า --</option>
          <option value="laptop" data-price="25000">Laptop (25,000 บาท)</option>
          <option value="mouse" data-price="500">Mouse (500 บาท)</option>
          <option value="keyboard" data-price="1500">Keyboard (1,500 บาท)</option>
        </select>
      </div>

      <div class="form-group">
        <label>จำนวน</label>
        <input type="number" name="products[${productCount}][quantity]" min="1" value="1"
               onchange="calculateTotal()" required>
      </div>

      <div class="form-group">
        <label>ราคาต่อหน่วย</label>
        <input type="number" name="products[${productCount}][price]" readonly>
      </div>

      <div class="form-group">
        <label>รวม</label>
        <input type="number" name="products[${productCount}][total]" readonly>
      </div>

      <button type="button" onclick="removeProduct(this)" class="btn btn-danger btn-small">ลบ</button>
    </div>
  `;

    productList.appendChild(newProduct);
    productCount++;
  }

  function removeProduct(button) {
    if (document.querySelectorAll('.product-item').length > 1) {
      button.closest('.product-item').remove();
      calculateTotal();
    } else {
      alert('ต้องมีสินค้าอย่างน้อย 1 รายการ');
    }
  }

  function updatePrice(select) {
    const price = select.selectedOptions[0]?.dataset.price || 0;
    const row = select.closest('.product-item');
    const priceInput = row.querySelector('input[name*="[price]"]');
    priceInput.value = price;
    calculateTotal();
  }

  function calculateTotal() {
    const productItems = document.querySelectorAll('.product-item');
    let grandTotal = 0;

    productItems.forEach((item) => {
      const price =
        parseFloat(item.querySelector('input[name*="[price]"]').value) || 0;
      const quantity =
        parseFloat(item.querySelector('input[name*="[quantity]"]').value) || 0;
      const total = price * quantity;

      item.querySelector('input[name*="[total]"]').value = total;
      grandTotal += total;
    });

    document.getElementById('grandTotal').textContent =
      grandTotal.toLocaleString();
  }

  function copyCustomerInfo() {
    const sameAsCustomer = document.getElementById('sameAsCustomer').checked;

    if (sameAsCustomer) {
      document.getElementById('shipping-name').value =
        document.getElementById('customer-name').value;
      document.getElementById('shipping-phone').value =
        document.getElementById('customer-phone').value;
    } else {
      document.getElementById('shipping-name').value = '';
      document.getElementById('shipping-phone').value = '';
    }
  }

  function togglePaymentDetails() {
    const paymentMethod = document.querySelector(
      'input[name="paymentMethod"]:checked'
    )?.value;

    document.getElementById('transferDetails').style.display = 'none';
    document.getElementById('creditDetails').style.display = 'none';

    if (paymentMethod === 'transfer') {
      document.getElementById('transferDetails').style.display = 'block';
    } else if (paymentMethod === 'credit') {
      document.getElementById('creditDetails').style.display = 'block';
    }
  }

  // เริ่มต้นการคำนวณ
  document.addEventListener('DOMContentLoaded', function () {
    calculateTotal();
  });
</script>
```

## 5. Best Practices

### 5.1 การจัดกลุ่มที่เหมาะสม

```html
<!-- ✅ ควรทำ - จัดกลุ่มข้อมูลที่เกี่ยวข้อง -->
<fieldset>
  <legend>ข้อมูลการติดต่อ</legend>
  <input type="email" name="email" />
  <input type="tel" name="phone" />
  <input type="text" name="address" />
</fieldset>

<fieldset>
  <legend>ความสนใจ</legend>
  <input type="checkbox" name="interests" value="tech" /> เทคโนโลยี
  <input type="checkbox" name="interests" value="sports" /> กีฬา
</fieldset>

<!-- ❌ หลีกเลี่ยง - ไม่จัดกลุ่ม -->
<form>
  <input type="email" name="email" />
  <input type="checkbox" name="interests" value="tech" /> เทคโนโลยี
  <input type="tel" name="phone" />
  <input type="checkbox" name="interests" value="sports" /> กีฬา
</form>
```

### 5.2 การใช้ legend ที่มีความหมาย

```html
<!-- ✅ ควรทำ -->
<fieldset>
  <legend>ข้อมูลบัตรเครดิต</legend>
  <!-- form controls -->
</fieldset>

<fieldset>
  <legend>เลือกประเภทสมาชิก</legend>
  <!-- radio buttons -->
</fieldset>

<!-- ❌ หลีกเลี่ยง -->
<fieldset>
  <legend>ข้อมูล</legend>
  <!-- ไม่ชัดเจน -->
  <!-- form controls -->
</fieldset>
```

### 5.3 การจัดรูปแบบและ Accessibility

```html
<!-- ✅ รองรับ Accessibility -->
<fieldset>
  <legend>ข้อมูลส่วนตัว (ข้อมูลบังคับ)</legend>
  <label for="name">ชื่อ *</label>
  <input
    type="text"
    id="name"
    name="name"
    required
    aria-describedby="name-help"
  />
  <div id="name-help">กรุณาใส่ชื่อจริงของท่าน</div>
</fieldset>

<!-- ✅ ใช้ CSS สำหรับการจัดรูปแบบ -->
<style>
  fieldset {
    border: 1px solid #ddd;
    border-radius: 4px;
    padding: 16px;
    margin: 16px 0;
  }

  legend {
    padding: 0 8px;
    font-weight: bold;
    color: #333;
  }
</style>
```

---

**สรุป**: การใช้ `<fieldset>` และ `<legend>` อย่างถูกต้องจะช่วยให้ฟอร์มมีโครงสร้างที่ชัดเจน ใช้งานง่าย และรองรับ Accessibility ได้ดี
