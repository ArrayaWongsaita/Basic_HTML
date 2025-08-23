# Form Elements อื่นๆ: `<textarea>`, `<select>`, `<option>`, `<optgroup>`

## 1. `<textarea>` - พื้นที่ข้อความขนาดใหญ่

### 1.1 ภาพรวม `<textarea>`

`<textarea>` ใช้สำหรับรับข้อความที่มีหลายบรรทัด เหมาะสำหรับความคิดเห็น, คำอธิบาย, หรือข้อความยาวๆ

**Syntax พื้นฐาน:**

```html
<textarea name="fieldname" id="id" rows="จำนวนบรรทัด" cols="จำนวนคอลัมน์">
ข้อความเริ่มต้น
</textarea>
```

### 1.2 Attributes สำคัญของ `<textarea>`

#### Attributes ขนาดและรูปลักษณ์

```html
<!-- กำหนดขนาด -->
<label for="description">คำอธิบาย</label>
<textarea
  id="description"
  name="description"
  rows="5"
  cols="50"
  placeholder="กรุณาใส่คำอธิบายรายละเอียด..."
></textarea>

<!-- ใช้ CSS แทน rows/cols (แนะนำ) -->
<textarea
  id="comment"
  name="comment"
  style="width: 100%; height: 120px; resize: vertical;"
  placeholder="แสดงความคิดเห็น..."
></textarea>
```

#### Attributes การควบคุม

```html
<!-- จำกัดความยาว -->
<label for="review">รีวิวสินค้า (ไม่เกิน 500 ตัวอักษร)</label>
<textarea
  id="review"
  name="review"
  maxlength="500"
  rows="6"
  placeholder="แชร์ประสบการณ์การใช้สินค้านี้..."
  required
></textarea>
<div class="char-counter"><span id="char-count">0</span>/500 ตัวอักษร</div>

<script>
  document.getElementById('review').addEventListener('input', function () {
    const count = this.value.length;
    document.getElementById('char-count').textContent = count;

    // เปลี่ยนสีเมื่อใกล้เต็ม
    const counter = document.getElementById('char-count');
    if (count > 450) {
      counter.style.color = 'red';
    } else if (count > 400) {
      counter.style.color = 'orange';
    } else {
      counter.style.color = 'green';
    }
  });
</script>
```

#### Attributes การป้องกันการแก้ไข

```html
<!-- อ่านอย่างเดียว -->
<label for="terms">เงื่อนไขการใช้งาน</label>
<textarea id="terms" name="terms" rows="10" readonly>
นี่คือเงื่อนไขการใช้งานที่ผู้ใช้ไม่สามารถแก้ไขได้
แต่สามารถอ่านและเลือกข้อความได้
</textarea>

<!-- ปิดการใช้งาน -->
<label for="disabled-field">ข้อมูลที่ไม่สามารถแก้ไขได้</label>
<textarea id="disabled-field" name="disabledField" rows="3" disabled>
ข้อมูลนี้ถูกปิดการใช้งาน
</textarea>
```

### 1.3 ตัวอย่างการใช้งาน `<textarea>` แบบละเอียด

#### ฟอร์มติดต่อ

```html
<form action="/contact" method="POST" class="contact-form">
  <div class="form-group">
    <label for="message">ข้อความ *</label>
    <textarea
      id="message"
      name="message"
      rows="8"
      cols="50"
      minlength="10"
      maxlength="1000"
      placeholder="กรุณาใส่ข้อความที่ต้องการสื่อสาร อย่างน้อย 10 ตัวอักษร..."
      required
      aria-describedby="message-help"
    ></textarea>
    <small id="message-help">
      ใส่รายละเอียดให้ครบถ้วนเพื่อให้เราสามารถช่วยเหลือได้อย่างดีที่สุด
    </small>
  </div>

  <div class="form-group">
    <label for="suggestions">ข้อเสนอแนะเพิ่มเติม</label>
    <textarea
      id="suggestions"
      name="suggestions"
      rows="4"
      placeholder="มีข้อเสนอแนะอื่นๆ สำหรับเราไหม?"
    ></textarea>
  </div>
</form>
```

#### Editor ขั้นพื้นฐาน

```html
<div class="text-editor">
  <div class="editor-toolbar">
    <button type="button" onclick="formatText('bold')">B</button>
    <button type="button" onclick="formatText('italic')">I</button>
    <button type="button" onclick="insertText('**ข้อความที่เน้น**')">
      เน้นข้อความ
    </button>
  </div>

  <textarea
    id="editor"
    name="content"
    rows="15"
    cols="80"
    placeholder="เริ่มเขียนเนื้อหาของคุณที่นี่..."
  ></textarea>

  <div class="editor-status">
    คำ: <span id="word-count">0</span> | ตัวอักษร:
    <span id="char-count">0</span> | บรรทัด: <span id="line-count">1</span>
  </div>
</div>

<script>
  const editor = document.getElementById('editor');

  editor.addEventListener('input', updateStats);
  editor.addEventListener('keyup', updateStats);

  function updateStats() {
    const text = editor.value;
    const words = text.trim() === '' ? 0 : text.trim().split(/\s+/).length;
    const chars = text.length;
    const lines = text.split('\n').length;

    document.getElementById('word-count').textContent = words;
    document.getElementById('char-count').textContent = chars;
    document.getElementById('line-count').textContent = lines;
  }

  function insertText(textToInsert) {
    const start = editor.selectionStart;
    const end = editor.selectionEnd;
    const currentText = editor.value;

    editor.value =
      currentText.substring(0, start) +
      textToInsert +
      currentText.substring(end);
    editor.focus();
    editor.setSelectionRange(
      start + textToInsert.length,
      start + textToInsert.length
    );
    updateStats();
  }
</script>
```

## 2. `<select>` - รายการแบบเลือก

### 2.1 ภาพรวม `<select>`

`<select>` ใช้สร้างรายการตัวเลือกแบบ dropdown หรือ listbox เหมาะสำหรับตัวเลือกที่มีจำนวนมาก

**Syntax พื้นฐาน:**

```html
<select name="fieldname" id="id">
  <option value="value1">ตัวเลือกที่ 1</option>
  <option value="value2">ตัวเลือกที่ 2</option>
</select>
```

### 2.2 Attributes สำคัญของ `<select>`

#### การเลือกหลายตัวเลือก

```html
<!-- เลือกได้เพียงตัวเลือกเดียว (ค่าเริ่มต้น) -->
<label for="country">ประเทศ</label>
<select id="country" name="country" required>
  <option value="">-- เลือกประเทศ --</option>
  <option value="TH">ไทย</option>
  <option value="US">สหรัฐอเมริกา</option>
  <option value="JP">ญี่ปุ่น</option>
  <option value="KR">เกาหลีใต้</option>
</select>

<!-- เลือกได้หลายตัวเลือก -->
<label for="languages">ภาษาที่ใช้ได้ (กด Ctrl/Cmd เพื่อเลือกหลายภาษา)</label>
<select id="languages" name="languages" multiple size="5">
  <option value="th">ไทย</option>
  <option value="en">อังกฤษ</option>
  <option value="jp">ญี่ปุ่น</option>
  <option value="kr">เกาหลี</option>
  <option value="cn">จีน</option>
  <option value="fr">ฝรั่งเศส</option>
</select>
```

#### การกำหนดขนาด

```html
<!-- แสดงเป็น listbox -->
<label for="skills">ทักษะ (เลือกได้หลายข้อ)</label>
<select id="skills" name="skills" multiple size="6">
  <option value="html">HTML</option>
  <option value="css">CSS</option>
  <option value="js">JavaScript</option>
  <option value="php">PHP</option>
  <option value="python">Python</option>
  <option value="java">Java</option>
</select>
```

### 2.3 `<option>` - ตัวเลือกแต่ละรายการ

#### Attributes ของ `<option>`

```html
<select id="product" name="product">
  <!-- ตัวเลือกว่าง -->
  <option value="">-- เลือกสินค้า --</option>

  <!-- ตัวเลือกปกติ -->
  <option value="laptop">แล็ปท็อป</option>

  <!-- ตัวเลือกที่เลือกไว้ล่วงหน้า -->
  <option value="smartphone" selected>สมาร์ทโฟน</option>

  <!-- ตัวเลือกที่ปิดการใช้งาน -->
  <option value="tablet" disabled>แท็บเล็ต (สินค้าหมด)</option>

  <!-- ตัวเลือกที่มี label แยกจาก value -->
  <option value="IPHONE15PRO" title="iPhone 15 Pro Max 256GB">
    iPhone 15 Pro - 45,900 บาท
  </option>
</select>
```

#### การจัดกลุ่มสินค้า

```html
<label for="product-category">หมวดสินค้า</label>
<select id="product-category" name="productCategory">
  <option value="">-- เลือกสินค้า --</option>

  <!-- Electronics -->
  <option value="laptop-gaming">แล็ปท็อปเกมมิ่ง</option>
  <option value="laptop-business">แล็ปท็อปธุรกิจ</option>
  <option value="smartphone-android">สมาร์ทโฟน Android</option>
  <option value="smartphone-ios">iPhone</option>

  <!-- Fashion -->
  <option value="clothes-men">เสื้อผ้าผู้ชาย</option>
  <option value="clothes-women">เสื้อผ้าผู้หญิง</option>
  <option value="shoes-sport">รองเท้ากีฬา</option>

  <!-- Home -->
  <option value="furniture">เฟอร์นิเจอร์</option>
  <option value="appliances">เครื่องใช้ไฟฟ้า</option>
</select>
```

### 2.4 `<optgroup>` - การจัดกลุ่มตัวเลือก

`<optgroup>` ใช้จัดกลุ่มตัวเลือกใน `<select>` ให้เป็นหมวดหมู่

```html
<label for="location">สถานที่</label>
<select id="location" name="location">
  <option value="">-- เลือกสถานที่ --</option>

  <optgroup label="ภาคเหนือ">
    <option value="chiang-mai">เชียงใหม่</option>
    <option value="chiang-rai">เชียงราย</option>
    <option value="lampang">ลำปาง</option>
    <option value="phrae">แพร่</option>
  </optgroup>

  <optgroup label="ภาคกลาง">
    <option value="bangkok">กรุงเทพมหานคร</option>
    <option value="nonthaburi">นนทบุรี</option>
    <option value="pathum-thani">ปทุมธานี</option>
    <option value="samut-prakan">สมุทรปราการ</option>
  </optgroup>

  <optgroup label="ภาคอีสาน">
    <option value="nakhon-ratchasima">นครราชสีมา</option>
    <option value="khon-kaen">ขอนแก่น</option>
    <option value="udon-thani">อุดรธานี</option>
    <option value="ubon-ratchathani">อุบลราชธานี</option>
  </optgroup>

  <optgroup label="ภาคใต้">
    <option value="hat-yai">หาดใหญ่</option>
    <option value="phuket">ภูเก็ต</option>
    <option value="krabi">กระบี่</option>
    <option value="surat-thani">สุราษฎร์ธานี</option>
  </optgroup>
</select>
```

### 2.5 ตัวอย่างการใช้งานขั้นสูง

#### Select แบบมีการค้นหา (Custom)

```html
<div class="select-search">
  <label for="university">มหาวิทยาลัย</label>
  <div class="select-wrapper">
    <input
      type="text"
      id="university-search"
      placeholder="ค้นหามหาวิทยาลัย..."
      onkeyup="filterUniversities()"
    />
    <select id="university" name="university" size="8">
      <optgroup label="มหาวิทยาลัยราชภัฏ">
        <option value="rajabhat-bangkok">ราชภัฏพระนคร</option>
        <option value="rajabhat-thonburi">ราชภัฏธนบุรี</option>
        <option value="rajabhat-chandrakasem">ราชภัฏจันทรเกษม</option>
        <option value="rajabhat-suan-dusit">ราชภัฏสวนดุสิต</option>
      </optgroup>

      <optgroup label="มหาวิทยาลัยเอกชน">
        <option value="assumption">มหาวิทยาลัยอัสสัมชัญ</option>
        <option value="bangkok-university">มหาวิทยาลัยกรุงเทพ</option>
        <option value="dhurakij-pundit">มหาวิทยาลัยธุรกิจบัณฑิตย์</option>
        <option value="siam-university">มหาวิทยาลัยสยาม</option>
      </optgroup>

      <optgroup label="มหาวิทยาลัยของรัฐ">
        <option value="chulalongkorn">จุฬาลงกรณ์มหาวิทยาลัย</option>
        <option value="thammasat">มหาวิทยาลัยธรรมศาสตร์</option>
        <option value="kasetsart">มหาวิทยาลัยเกษตรศาสตร์</option>
        <option value="mahidol">มหาวิทยาลัยมหิดล</option>
      </optgroup>
    </select>
  </div>
</div>

<script>
  function filterUniversities() {
    const searchTerm = document
      .getElementById('university-search')
      .value.toLowerCase();
    const select = document.getElementById('university');
    const options = select.querySelectorAll('option');
    const optgroups = select.querySelectorAll('optgroup');

    // ซ่อน/แสดง options
    options.forEach((option) => {
      const text = option.textContent.toLowerCase();
      if (text.includes(searchTerm)) {
        option.style.display = '';
      } else {
        option.style.display = 'none';
      }
    });

    // ซ่อน/แสดง optgroups
    optgroups.forEach((optgroup) => {
      const visibleOptions = optgroup.querySelectorAll(
        'option:not([style*="display: none"])'
      );
      if (visibleOptions.length > 0) {
        optgroup.style.display = '';
      } else {
        optgroup.style.display = 'none';
      }
    });
  }
</script>
```

#### Select แบบพึ่งพาอาศัยกัน (Dependent Dropdowns)

```html
<div class="dependent-selects">
  <div class="form-group">
    <label for="province">จังหวัด</label>
    <select id="province" name="province" onchange="loadDistricts()" required>
      <option value="">-- เลือกจังหวัด --</option>
      <option value="bangkok">กรุงเทพมหานคร</option>
      <option value="chiang-mai">เชียงใหม่</option>
      <option value="phuket">ภูเก็ต</option>
    </select>
  </div>

  <div class="form-group">
    <label for="district">เขต/อำเภอ</label>
    <select
      id="district"
      name="district"
      onchange="loadSubdistricts()"
      disabled
    >
      <option value="">-- เลือกเขต/อำเภอ --</option>
    </select>
  </div>

  <div class="form-group">
    <label for="subdistrict">แขวง/ตำบล</label>
    <select id="subdistrict" name="subdistrict" disabled>
      <option value="">-- เลือกแขวง/ตำบล --</option>
    </select>
  </div>
</div>

<script>
  const locationData = {
    bangkok: {
      'district-1': ['subdistrict-1-1', 'subdistrict-1-2'],
      'district-2': ['subdistrict-2-1', 'subdistrict-2-2'],
    },
    'chiang-mai': {
      muang: ['chang-phueak', 'suthep'],
      'san-sai': ['san-sai', 'mae-jo'],
    },
    phuket: {
      muang: ['patong', 'kathu'],
      thalang: ['choeng-thale', 'sakhu'],
    },
  };

  function loadDistricts() {
    const province = document.getElementById('province').value;
    const districtSelect = document.getElementById('district');
    const subdistrictSelect = document.getElementById('subdistrict');

    // ล้างและปิด district และ subdistrict
    districtSelect.innerHTML = '<option value="">-- เลือกเขต/อำเภอ --</option>';
    subdistrictSelect.innerHTML =
      '<option value="">-- เลือกแขวง/ตำบล --</option>';
    subdistrictSelect.disabled = true;

    if (province && locationData[province]) {
      // เปิดใช้งาน district
      districtSelect.disabled = false;

      // เพิ่ม options สำหรับ district
      Object.keys(locationData[province]).forEach((district) => {
        const option = document.createElement('option');
        option.value = district;
        option.textContent = district
          .replace('-', ' ')
          .replace(/\b\w/g, (l) => l.toUpperCase());
        districtSelect.appendChild(option);
      });
    } else {
      districtSelect.disabled = true;
    }
  }

  function loadSubdistricts() {
    const province = document.getElementById('province').value;
    const district = document.getElementById('district').value;
    const subdistrictSelect = document.getElementById('subdistrict');

    // ล้าง subdistrict
    subdistrictSelect.innerHTML =
      '<option value="">-- เลือกแขวง/ตำบล --</option>';

    if (province && district && locationData[province][district]) {
      // เปิดใช้งาน subdistrict
      subdistrictSelect.disabled = false;

      // เพิ่ม options สำหรับ subdistrict
      locationData[province][district].forEach((subdistrict) => {
        const option = document.createElement('option');
        option.value = subdistrict;
        option.textContent = subdistrict
          .replace('-', ' ')
          .replace(/\b\w/g, (l) => l.toUpperCase());
        subdistrictSelect.appendChild(option);
      });
    } else {
      subdistrictSelect.disabled = true;
    }
  }
</script>
```

## 3. ตัวอย่างฟอร์มครอบคลุม

```html
<form action="/submit-feedback" method="POST" class="feedback-form">
  <h2>แบบฟอร์มการประเมิน</h2>

  <!-- ข้อมูลพื้นฐาน -->
  <fieldset>
    <legend>ข้อมูลผู้ประเมิน</legend>

    <div class="form-row">
      <div class="form-group">
        <label for="name">ชื่อ-นามสกุล *</label>
        <input type="text" id="name" name="name" required />
      </div>

      <div class="form-group">
        <label for="email">อีเมล *</label>
        <input type="email" id="email" name="email" required />
      </div>
    </div>

    <div class="form-row">
      <div class="form-group">
        <label for="age-group">กลุ่มอายุ</label>
        <select id="age-group" name="ageGroup">
          <option value="">-- เลือกกลุ่มอายุ --</option>
          <option value="under-18">ต่ำกว่า 18 ปี</option>
          <option value="18-25">18-25 ปี</option>
          <option value="26-35">26-35 ปี</option>
          <option value="36-45">36-45 ปี</option>
          <option value="46-55">46-55 ปี</option>
          <option value="over-55">มากกว่า 55 ปี</option>
        </select>
      </div>

      <div class="form-group">
        <label for="occupation">อาชีพ</label>
        <select id="occupation" name="occupation">
          <option value="">-- เลือกอาชีพ --</option>

          <optgroup label="ภาครัฐ">
            <option value="government">ข้าราชการ</option>
            <option value="state-enterprise">รัฐวิสาหกิจ</option>
            <option value="military">ทหาร/ตำรวจ</option>
          </optgroup>

          <optgroup label="ภาคเอกชน">
            <option value="employee">พนักงาน</option>
            <option value="manager">ผู้จัดการ</option>
            <option value="executive">ผู้บริหาร</option>
          </optgroup>

          <optgroup label="อิสระ">
            <option value="business-owner">เจ้าของธุรกิจ</option>
            <option value="freelancer">ฟรีแลนซ์</option>
            <option value="professional">อาชีพอิสระ</option>
          </optgroup>

          <optgroup label="อื่นๆ">
            <option value="student">นักเรียน/นักศึกษา</option>
            <option value="retired">เกษียณ</option>
            <option value="unemployed">ไม่ได้ทำงาน</option>
          </optgroup>
        </select>
      </div>
    </div>
  </fieldset>

  <!-- การประเมินบริการ -->
  <fieldset>
    <legend>การประเมินบริการ</legend>

    <div class="form-group">
      <label for="service-type">ประเภทบริการที่ใช้ (เลือกได้หลายข้อ)</label>
      <select id="service-type" name="serviceType" multiple size="5">
        <optgroup label="บริการออนไลน์">
          <option value="website">เว็บไซต์</option>
          <option value="mobile-app">แอปพลิเคชัน</option>
          <option value="online-chat">แชทออนไลน์</option>
        </optgroup>

        <optgroup label="บริการสาขา">
          <option value="branch-service">บริการหน้าเคาน์เตอร์</option>
          <option value="consultation">การให้คำปรึกษา</option>
          <option value="document-service">บริการเอกสาร</option>
        </optgroup>

        <optgroup label="บริการโทรศัพท์">
          <option value="call-center">ศูนย์บริการลูกค้า</option>
          <option value="technical-support">สนับสนุนด้านเทคนิค</option>
        </optgroup>
      </select>
      <small>กด Ctrl (หรือ Cmd บน Mac) ค้างไว้เพื่อเลือกหลายรายการ</small>
    </div>

    <div class="form-group">
      <label for="satisfaction">ระดับความพึงพอใจ</label>
      <select id="satisfaction" name="satisfaction" required>
        <option value="">-- เลือกระดับความพึงพอใจ --</option>
        <option value="1">1 - ไม่พึงพอใจอย่างมาก</option>
        <option value="2">2 - ไม่พึงพอใจ</option>
        <option value="3">3 - ปานกลาง</option>
        <option value="4">4 - พึงพอใจ</option>
        <option value="5">5 - พึงพอใจมาก</option>
      </select>
    </div>
  </fieldset>

  <!-- ความคิดเห็นและข้อเสนอแนะ -->
  <fieldset>
    <legend>ความคิดเห็นและข้อเสนอแนะ</legend>

    <div class="form-group">
      <label for="positive-feedback">สิ่งที่ชอบ/ประทับใจ</label>
      <textarea
        id="positive-feedback"
        name="positiveFeedback"
        rows="4"
        cols="50"
        placeholder="บอกเราถึงสิ่งที่ท่านชอบหรือประทับใจในบริการของเรา..."
      ></textarea>
    </div>

    <div class="form-group">
      <label for="improvement-suggestions">ข้อเสนอแนะในการปรับปรุง</label>
      <textarea
        id="improvement-suggestions"
        name="improvementSuggestions"
        rows="4"
        cols="50"
        placeholder="มีข้อเสนอแนะอะไรที่จะช่วยให้บริการของเราดีขึ้นบ้าง?"
      ></textarea>
    </div>

    <div class="form-group">
      <label for="additional-comments">ความคิดเห็นเพิ่มเติม</label>
      <textarea
        id="additional-comments"
        name="additionalComments"
        rows="6"
        cols="50"
        maxlength="1000"
        placeholder="ความคิดเห็นอื่นๆ ที่อยากแชร์กับเรา..."
        oninput="updateCharCount()"
      ></textarea>
      <div class="char-counter">
        <span id="char-count">0</span>/1000 ตัวอักษร
      </div>
    </div>
  </fieldset>

  <!-- การติดต่อกลับ -->
  <fieldset>
    <legend>การติดต่อกลับ</legend>

    <div class="form-group">
      <label for="follow-up">ต้องการให้เราติดต่อกลับหรือไม่?</label>
      <select
        id="follow-up"
        name="followUp"
        onchange="toggleContactPreference()"
      >
        <option value="no">ไม่ต้องการ</option>
        <option value="yes">ต้องการ</option>
      </select>
    </div>

    <div class="form-group" id="contact-preference" style="display: none;">
      <label for="preferred-contact">ช่องทางที่ต้องการให้ติดต่อกลับ</label>
      <select id="preferred-contact" name="preferredContact">
        <option value="">-- เลือกช่องทาง --</option>
        <option value="email">อีเมล</option>
        <option value="phone">โทรศัพท์</option>
        <option value="sms">SMS</option>
        <option value="line">Line</option>
      </select>
    </div>

    <div class="form-group" id="contact-time" style="display: none;">
      <label for="best-time">เวลาที่สะดวกให้ติดต่อ</label>
      <select id="best-time" name="bestTime" multiple size="4">
        <optgroup label="เช้า">
          <option value="morning-early">06:00-09:00</option>
          <option value="morning-late">09:00-12:00</option>
        </optgroup>

        <optgroup label="บ่าย">
          <option value="afternoon-early">12:00-15:00</option>
          <option value="afternoon-late">15:00-18:00</option>
        </optgroup>

        <optgroup label="เย็น">
          <option value="evening">18:00-21:00</option>
          <option value="night">21:00-22:00</option>
        </optgroup>
      </select>
    </div>
  </fieldset>

  <!-- ข้อมูลซ่อน -->
  <input type="hidden" name="formVersion" value="2.1" />
  <input type="hidden" name="source" value="website" />
  <input type="hidden" name="timestamp" id="timestamp" />

  <!-- ปุ่มส่ง -->
  <div class="form-actions">
    <button type="reset" class="btn btn-secondary">ล้างข้อมูล</button>
    <button type="submit" class="btn btn-primary">ส่งการประเมิน</button>
  </div>
</form>

<script>
  // อัปเดตตัวนับตัวอักษร
  function updateCharCount() {
    const textarea = document.getElementById('additional-comments');
    const count = textarea.value.length;
    document.getElementById('char-count').textContent = count;

    // เปลี่ยนสีเมื่อใกล้ถึงลิมิต
    const counter = document.getElementById('char-count');
    if (count > 900) {
      counter.style.color = 'red';
    } else if (count > 800) {
      counter.style.color = 'orange';
    } else {
      counter.style.color = 'green';
    }
  }

  // แสดง/ซ่อนตัวเลือกการติดต่อกลับ
  function toggleContactPreference() {
    const followUp = document.getElementById('follow-up').value;
    const contactPreference = document.getElementById('contact-preference');
    const contactTime = document.getElementById('contact-time');

    if (followUp === 'yes') {
      contactPreference.style.display = 'block';
      contactTime.style.display = 'block';
    } else {
      contactPreference.style.display = 'none';
      contactTime.style.display = 'none';
    }
  }

  // ตั้งค่า timestamp
  document.getElementById('timestamp').value = new Date().toISOString();

  // เริ่มต้นการนับตัวอักษร
  updateCharCount();
</script>
```

## 4. Best Practices

### 4.1 การใช้ `<textarea>`

```html
<!-- ✅ ควรทำ -->
<label for="message">ข้อความ *</label>
<textarea
  id="message"
  name="message"
  rows="5"
  required
  aria-describedby="message-help"
></textarea>
<div id="message-help">กรุณาใส่ข้อความอย่างน้อย 10 ตัวอักษร</div>

<!-- ❌ หลีกเลี่ยง -->
<textarea placeholder="ข้อความ *"></textarea>
<!-- ไม่มี label -->
```

### 4.2 การใช้ `<select>` และ `<option>`

```html
<!-- ✅ ควรทำ -->
<label for="country">ประเทศ *</label>
<select id="country" name="country" required>
  <option value="">-- เลือกประเทศ --</option>
  <option value="TH">ไทย</option>
  <option value="US">สหรัฐอเมริกา</option>
</select>

<!-- ❌ หลีกเลี่ยง -->
<select name="country">
  <option>เลือกประเทศ</option>
  <!-- ไม่มี value -->
  <option>ไทย</option>
  <!-- value ไม่ชัดเจน -->
</select>
```

### 4.3 การใช้ `<optgroup>`

```html
<!-- ✅ ใช้เมื่อมีตัวเลือกมาก -->
<select name="location">
  <optgroup label="ภาคเหนือ">
    <option value="CM">เชียงใหม่</option>
    <option value="CR">เชียงราย</option>
  </optgroup>
  <optgroup label="ภาคกลาง">
    <option value="BKK">กรุงเทพฯ</option>
    <option value="NBI">นนทบุรี</option>
  </optgroup>
</select>

<!-- ❌ หลีกเลี่ยงการใช้เมื่อตัวเลือกน้อย -->
<select name="gender">
  <optgroup label="เพศ">
    <option value="M">ชาย</option>
    <option value="F">หญิง</option>
  </optgroup>
</select>
```

---

**สรุป**: การใช้ `<textarea>`, `<select>`, `<option>`, และ `<optgroup>` อย่างเหมาะสมจะช่วยให้ฟอร์มมีประสิทธิภาพและใช้งานง่าย โดยเฉพาะการจัดกลุ่มข้อมูลและการให้ตัวเลือกที่ชัดเจน
