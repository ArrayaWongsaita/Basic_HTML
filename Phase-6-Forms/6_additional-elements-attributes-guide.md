# Elements เสริมและ Attributes สำคัญของฟอร์ม

## 1. Elements เสริมสำหรับฟอร์ม

### 1.1 `<datalist>` - รายการข้อเสนอแนะ

`<datalist>` ใช้สร้างรายการตัวเลือกที่แนะนำสำหรับ input โดยผู้ใช้สามารถพิมพ์เองหรือเลือกจากรายการได้

**Syntax พื้นฐาน:**

```html
<input list="datalist-id" name="fieldname" />
<datalist id="datalist-id">
  <option value="ตัวเลือกที่ 1"></option>
  <option value="ตัวเลือกที่ 2"></option>
</datalist>
```

#### ตัวอย่างการใช้งาน datalist

```html
<!-- ค้นหาเมือง -->
<div class="form-group">
  <label for="city">เมือง</label>
  <input
    type="text"
    id="city"
    name="city"
    list="cities"
    placeholder="พิมพ์หรือเลือกเมือง"
  />
  <datalist id="cities">
    <option value="กรุงเทพมหานคร"></option>
    <option value="เชียงใหม่"></option>
    <option value="เชียงราย"></option>
    <option value="ภูเก็ต"></option>
    <option value="ขอนแก่น"></option>
    <option value="นครราชสีมา"></option>
    <option value="สงขลา"></option>
    <option value="อุดรธานี"></option>
  </datalist>
</div>

<!-- อีเมลที่ใช้บ่อย -->
<div class="form-group">
  <label for="email">อีเมล</label>
  <input
    type="email"
    id="email"
    name="email"
    list="email-domains"
    placeholder="your-email@"
  />
  <datalist id="email-domains">
    <option value="user@gmail.com"></option>
    <option value="user@yahoo.com"></option>
    <option value="user@hotmail.com"></option>
    <option value="user@outlook.com"></option>
    <option value="user@company.com"></option>
  </datalist>
</div>

<!-- ภาษาโปรแกรม -->
<div class="form-group">
  <label for="programming-language">ภาษาโปรแกรมที่ใช้</label>
  <input
    type="text"
    id="programming-language"
    name="programmingLanguage"
    list="languages"
    placeholder="เลือกหรือพิมพ์ภาษาโปรแกรม"
  />
  <datalist id="languages">
    <option value="JavaScript" label="JS - ภาษาสำหรับเว็บ"></option>
    <option value="Python" label="Python - ใช้งานง่าย"></option>
    <option value="Java" label="Java - Object-Oriented"></option>
    <option value="C++" label="C++ - ประสิทธิภาพสูง"></option>
    <option value="PHP" label="PHP - เว็บไซต์"></option>
    <option value="C#" label="C# - Microsoft"></option>
    <option value="Ruby" label="Ruby - Elegant"></option>
    <option value="Go" label="Go - Google"></option>
  </datalist>
</div>
```

#### Datalist แบบไดนามิก

```html
<div class="search-form">
  <label for="product-search">ค้นหาสินค้า</label>
  <input
    type="text"
    id="product-search"
    name="productSearch"
    list="product-suggestions"
    placeholder="พิมพ์ชื่อสินค้า..."
    oninput="updateProductSuggestions(this.value)"
  />
  <datalist id="product-suggestions">
    <!-- จะถูกเติมด้วย JavaScript -->
  </datalist>
</div>

<script>
  const products = [
    { name: 'iPhone 15', category: 'มือถือ', price: 35000 },
    { name: 'Samsung Galaxy S24', category: 'มือถือ', price: 30000 },
    { name: 'MacBook Air', category: 'คอมพิวเตอร์', price: 45000 },
    { name: 'Dell XPS', category: 'คอมพิวเตอร์', price: 40000 },
    { name: 'iPad Pro', category: 'แท็บเล็ต', price: 35000 },
    { name: 'Surface Pro', category: 'แท็บเล็ต', price: 38000 },
    { name: 'AirPods Pro', category: 'หูฟัง', price: 8000 },
    { name: 'Sony WH-1000XM4', category: 'หูฟัง', price: 12000 },
  ];

  function updateProductSuggestions(searchTerm) {
    const datalist = document.getElementById('product-suggestions');
    datalist.innerHTML = '';

    if (searchTerm.length < 2) return;

    const filteredProducts = products.filter(
      (product) =>
        product.name.toLowerCase().includes(searchTerm.toLowerCase()) ||
        product.category.toLowerCase().includes(searchTerm.toLowerCase())
    );

    filteredProducts.forEach((product) => {
      const option = document.createElement('option');
      option.value = product.name;
      option.label = `${
        product.category
      } - ${product.price.toLocaleString()} บาท`;
      datalist.appendChild(option);
    });
  }
</script>
```

### 1.2 `<output>` - แสดงผลลัพธ์

`<output>` ใช้แสดงผลลัพธ์ของการคำนวณหรือการทำงานของผู้ใช้

```html
<!-- เครื่องคิดเลขง่ายๆ -->
<form oninput="result.value = parseInt(a.value) + parseInt(b.value)">
  <div class="calculator">
    <label for="num1">ตัวเลขที่ 1:</label>
    <input type="number" id="num1" name="a" value="0" />

    <span> + </span>

    <label for="num2">ตัวเลขที่ 2:</label>
    <input type="number" id="num2" name="b" value="0" />

    <span> = </span>

    <output name="result" for="a b">0</output>
  </div>
</form>

<!-- คำนวณ BMI -->
<form class="bmi-calculator">
  <div class="form-group">
    <label for="weight">น้ำหนัก (กิโลกรัม):</label>
    <input
      type="number"
      id="weight"
      name="weight"
      min="1"
      max="300"
      step="0.1"
      oninput="calculateBMI()"
    />
  </div>

  <div class="form-group">
    <label for="height">ส่วนสูง (เซนติเมตร):</label>
    <input
      type="number"
      id="height"
      name="height"
      min="50"
      max="250"
      oninput="calculateBMI()"
    />
  </div>

  <div class="result">
    <label>ค่า BMI:</label>
    <output id="bmi-result" name="bmi" for="weight height">-</output>
    <output id="bmi-status" name="status">กรุณาใส่ข้อมูล</output>
  </div>
</form>

<script>
  function calculateBMI() {
    const weight = parseFloat(document.getElementById('weight').value);
    const height = parseFloat(document.getElementById('height').value);

    if (weight && height) {
      const heightInMeters = height / 100;
      const bmi = weight / (heightInMeters * heightInMeters);

      document.getElementById('bmi-result').value = bmi.toFixed(1);

      let status = '';
      if (bmi < 18.5) {
        status = 'น้ำหนักน้อย';
      } else if (bmi < 25) {
        status = 'น้ำหนักปกติ';
      } else if (bmi < 30) {
        status = 'น้ำหนักเกิน';
      } else {
        status = 'อ้วน';
      }

      document.getElementById('bmi-status').value = status;
    }
  }
</script>

<!-- ระบบให้คะแนน -->
<div class="rating-system">
  <h3>ประเมินสินค้า</h3>

  <div class="rating-criteria">
    <div class="form-group">
      <label for="quality">คุณภาพ (1-10):</label>
      <input
        type="range"
        id="quality"
        name="quality"
        min="1"
        max="10"
        value="5"
        oninput="updateRating()"
      />
      <span id="quality-value">5</span>
    </div>

    <div class="form-group">
      <label for="price">ราคาเหมาะสม (1-10):</label>
      <input
        type="range"
        id="price"
        name="price"
        min="1"
        max="10"
        value="5"
        oninput="updateRating()"
      />
      <span id="price-value">5</span>
    </div>

    <div class="form-group">
      <label for="service">บริการ (1-10):</label>
      <input
        type="range"
        id="service"
        name="service"
        min="1"
        max="10"
        value="5"
        oninput="updateRating()"
      />
      <span id="service-value">5</span>
    </div>
  </div>

  <div class="overall-rating">
    <label>คะแนนรวม:</label>
    <output id="total-rating" name="totalRating">5.0</output>
    <span>/10</span>
    <div class="stars" id="star-display">⭐⭐⭐⭐⭐</div>
  </div>
</div>

<script>
  function updateRating() {
    const quality = parseInt(document.getElementById('quality').value);
    const price = parseInt(document.getElementById('price').value);
    const service = parseInt(document.getElementById('service').value);

    // อัปเดตค่าที่แสดง
    document.getElementById('quality-value').textContent = quality;
    document.getElementById('price-value').textContent = price;
    document.getElementById('service-value').textContent = service;

    // คำนวณคะแนนเฉลี่ย
    const average = ((quality + price + service) / 3).toFixed(1);
    document.getElementById('total-rating').value = average;

    // แสดงดาว
    const stars = Math.round(average / 2);
    document.getElementById('star-display').textContent =
      '⭐'.repeat(stars) + '☆'.repeat(5 - stars);
  }
</script>
```

### 1.3 `<progress>` - แถบความคืบหน้า

`<progress>` แสดงความคืบหน้าของงานที่กำลังดำเนินการ

```html
<!-- Progress แบบคงที่ -->
<div class="progress-examples">
  <div class="progress-item">
    <label for="download-progress">ดาวน์โหลดไฟล์:</label>
    <progress id="download-progress" value="32" max="100">32%</progress>
    <span>32%</span>
  </div>

  <div class="progress-item">
    <label for="upload-progress">อัปโหลดรูปภาพ:</label>
    <progress id="upload-progress" value="0.7" max="1">70%</progress>
    <span>70%</span>
  </div>

  <!-- Progress ไม่ระบุค่า (indeterminate) -->
  <div class="progress-item">
    <label>กำลังประมวลผล:</label>
    <progress>กำลังประมวลผล...</progress>
  </div>
</div>

<!-- Progress แบบไดนามิก -->
<div class="file-processor">
  <h3>ประมวลผลไฟล์</h3>

  <div class="file-input">
    <input
      type="file"
      id="file-input"
      multiple
      onchange="processFiles(event)"
    />
    <label for="file-input" class="btn">เลือกไฟล์</label>
  </div>

  <div
    class="progress-container"
    id="progress-container"
    style="display: none;"
  >
    <div class="current-file">
      กำลังประมวลผล: <span id="current-file-name">-</span>
    </div>

    <div class="progress-bar">
      <label>ไฟล์ปัจจุบัน:</label>
      <progress id="current-file-progress" value="0" max="100"></progress>
      <span id="current-percent">0%</span>
    </div>

    <div class="progress-bar">
      <label>ความคืบหน้าทั้งหมด:</label>
      <progress id="total-progress" value="0" max="100"></progress>
      <span id="total-percent">0%</span>
    </div>

    <div class="file-count">
      <span id="processed-count">0</span> / <span id="total-count">0</span> ไฟล์
    </div>

    <button
      type="button"
      onclick="cancelProcessing()"
      class="btn btn-secondary"
    >
      ยกเลิก
    </button>
  </div>

  <div class="results" id="results"></div>
</div>

<script>
  let processingCancelled = false;

  async function processFiles(event) {
    const files = Array.from(event.target.files);
    if (files.length === 0) return;

    const container = document.getElementById('progress-container');
    const results = document.getElementById('results');

    container.style.display = 'block';
    results.innerHTML = '';
    processingCancelled = false;

    document.getElementById('total-count').textContent = files.length;
    document.getElementById('total-progress').max = files.length;

    for (let i = 0; i < files.length; i++) {
      if (processingCancelled) break;

      const file = files[i];
      document.getElementById('current-file-name').textContent = file.name;
      document.getElementById('processed-count').textContent = i;

      // จำลองการประมวลผลไฟล์
      await simulateFileProcessing(file);

      // อัปเดต progress ทั้งหมด
      const totalProgress = i + 1;
      document.getElementById('total-progress').value = totalProgress;
      document.getElementById('total-percent').textContent =
        Math.round((totalProgress / files.length) * 100) + '%';

      // เพิ่มผลลัพธ์
      const result = document.createElement('div');
      result.className = 'file-result';
      result.innerHTML = `✅ ${file.name} (${formatFileSize(file.size)})`;
      results.appendChild(result);
    }

    if (!processingCancelled) {
      document.getElementById('current-file-name').textContent = 'เสร็จสิ้น!';
      document.getElementById('processed-count').textContent = files.length;
    }
  }

  async function simulateFileProcessing(file) {
    const steps = 10;
    const currentProgress = document.getElementById('current-file-progress');
    const currentPercent = document.getElementById('current-percent');

    currentProgress.value = 0;
    currentProgress.max = steps;

    for (let step = 0; step <= steps; step++) {
      if (processingCancelled) break;

      currentProgress.value = step;
      const percent = Math.round((step / steps) * 100);
      currentPercent.textContent = percent + '%';

      // รอ 200ms เพื่อจำลองการประมวลผล
      await new Promise((resolve) => setTimeout(resolve, 200));
    }
  }

  function cancelProcessing() {
    processingCancelled = true;
    document.getElementById('current-file-name').textContent = 'ถูกยกเลิก';
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

### 1.4 `<meter>` - แสดงค่าในช่วง

`<meter>` แสดงค่าสเกลาร์ในช่วงที่กำหนด หรือค่าเศษส่วน

```html
<!-- ตัวอย่างพื้นฐาน -->
<div class="meter-examples">
  <div class="meter-item">
    <label>พื้นที่ดิสก์ที่ใช้:</label>
    <meter value="6" min="0" max="10">6 จาก 10</meter>
    <span>6/10 GB</span>
  </div>

  <div class="meter-item">
    <label>คะแนนสอบ:</label>
    <meter value="0.6">60%</meter>
    <span>60%</span>
  </div>

  <div class="meter-item">
    <label>อุณหภูมิ:</label>
    <meter value="25" min="0" max="50" low="10" high="40" optimum="20">
      25°C
    </meter>
    <span>25°C</span>
  </div>
</div>

<!-- Dashboard แสดงสถานะระบบ -->
<div class="system-dashboard">
  <h3>สถานะระบบ</h3>

  <div class="metric-group">
    <div class="metric-item">
      <label>การใช้งาน CPU:</label>
      <meter
        id="cpu-usage"
        value="0.45"
        min="0"
        max="1"
        low="0.6"
        high="0.8"
        optimum="0.3"
      ></meter>
      <span id="cpu-percent">45%</span>
    </div>

    <div class="metric-item">
      <label>การใช้งาน RAM:</label>
      <meter
        id="ram-usage"
        value="0.62"
        min="0"
        max="1"
        low="0.7"
        high="0.9"
        optimum="0.5"
      ></meter>
      <span id="ram-percent">62%</span>
    </div>

    <div class="metric-item">
      <label>พื้นที่ฮาร์ดดิสก์:</label>
      <meter
        id="disk-usage"
        value="0.78"
        min="0"
        max="1"
        low="0.8"
        high="0.9"
        optimum="0.6"
      ></meter>
      <span id="disk-percent">78%</span>
    </div>

    <div class="metric-item">
      <label>อุณหภูมิ CPU:</label>
      <meter
        id="cpu-temp"
        value="65"
        min="0"
        max="100"
        low="70"
        high="85"
        optimum="50"
      ></meter>
      <span id="temp-value">65°C</span>
    </div>

    <div class="metric-item">
      <label>ความเร็วเครือข่าย:</label>
      <meter
        id="network-speed"
        value="85"
        min="0"
        max="100"
        low="30"
        high="80"
        optimum="90"
      ></meter>
      <span id="speed-value">85 Mbps</span>
    </div>
  </div>

  <button type="button" onclick="updateMetrics()" class="btn">
    รีเฟรชข้อมูล
  </button>
</div>

<!-- ประเมินสมรรถนะพนักงาน -->
<div class="performance-review">
  <h3>การประเมินสมรรถนะ</h3>

  <div class="performance-metrics">
    <div class="metric-category">
      <h4>ทักษะด้านเทคนิค</h4>
      <div class="skill-item">
        <label>การเขียนโปรแกรม:</label>
        <meter value="4.2" min="1" max="5" low="2" high="4" optimum="5">
          4.2/5
        </meter>
        <span>4.2/5</span>
      </div>
      <div class="skill-item">
        <label>การแก้ปัญหา:</label>
        <meter value="3.8" min="1" max="5" low="2" high="4" optimum="5">
          3.8/5
        </meter>
        <span>3.8/5</span>
      </div>
      <div class="skill-item">
        <label>การทำงานเป็นทีม:</label>
        <meter value="4.5" min="1" max="5" low="2" high="4" optimum="5">
          4.5/5
        </meter>
        <span>4.5/5</span>
      </div>
    </div>

    <div class="metric-category">
      <h4>ผลงาน</h4>
      <div class="skill-item">
        <label>การทำงานตามเป้าหมาย:</label>
        <meter value="92" min="0" max="100" low="60" high="80" optimum="100">
          92%
        </meter>
        <span>92%</span>
      </div>
      <div class="skill-item">
        <label>คุณภาพงาน:</label>
        <meter value="88" min="0" max="100" low="60" high="80" optimum="100">
          88%
        </meter>
        <span>88%</span>
      </div>
    </div>
  </div>
</div>

<script>
  function updateMetrics() {
    // จำลองการอัปเดตข้อมูล
    const metrics = [
      { id: 'cpu-usage', spanId: 'cpu-percent', suffix: '%' },
      { id: 'ram-usage', spanId: 'ram-percent', suffix: '%' },
      { id: 'disk-usage', spanId: 'disk-percent', suffix: '%' },
      { id: 'cpu-temp', spanId: 'temp-value', suffix: '°C', isTemp: true },
      {
        id: 'network-speed',
        spanId: 'speed-value',
        suffix: ' Mbps',
        isSpeed: true,
      },
    ];

    metrics.forEach((metric) => {
      const meter = document.getElementById(metric.id);
      const span = document.getElementById(metric.spanId);

      let newValue;
      if (metric.isTemp) {
        newValue = Math.random() * 40 + 40; // 40-80°C
      } else if (metric.isSpeed) {
        newValue = Math.random() * 50 + 50; // 50-100 Mbps
      } else {
        newValue = Math.random(); // 0-1
      }

      meter.value = newValue;

      if (metric.isTemp || metric.isSpeed) {
        span.textContent = Math.round(newValue) + metric.suffix;
      } else {
        span.textContent = Math.round(newValue * 100) + metric.suffix;
      }
    });
  }

  // อัปเดตข้อมูลอัตโนมัติทุก 5 วินาที
  setInterval(updateMetrics, 5000);
</script>
```

## 2. Attributes สำคัญของฟอร์ม

### 2.1 Attributes พื้นฐาน

#### `name` Attribute

```html
<!-- ใช้สำหรับส่งข้อมูล -->
<input type="text" name="username" value="john_doe" />
<input type="email" name="email" value="john@example.com" />

<!-- การจัดกลุ่ม radio buttons -->
<input type="radio" name="gender" value="male" id="male" />
<label for="male">ชาย</label>
<input type="radio" name="gender" value="female" id="female" />
<label for="female">หญิง</label>

<!-- การส่งข้อมูลแบบ array -->
<input type="checkbox" name="hobbies[]" value="reading" />
<input type="checkbox" name="hobbies[]" value="sports" />
<input type="checkbox" name="hobbies[]" value="music" />
```

#### `value` Attribute

```html
<!-- ค่าเริ่มต้น -->
<input type="text" name="country" value="ไทย" />
<input type="number" name="age" value="25" />

<!-- ค่าสำหรับ radio และ checkbox -->
<input type="radio" name="size" value="S" id="size-s" />
<input type="radio" name="size" value="M" id="size-m" checked />
<input type="radio" name="size" value="L" id="size-l" />

<!-- ข้อความบนปุ่ม -->
<input type="submit" value="ส่งข้อมูล" />
<input type="reset" value="ล้างข้อมูล" />
```

#### `placeholder` Attribute

```html
<!-- คำแนะนำในช่องกรอก -->
<input type="text" name="fullname" placeholder="ชื่อ-นามสกุล" />
<input type="email" name="email" placeholder="example@email.com" />
<input type="tel" name="phone" placeholder="08X-XXX-XXXX" />
<input type="password" name="password" placeholder="อย่างน้อย 8 ตัวอักษร" />

<textarea name="message" placeholder="ใส่ข้อความของคุณที่นี่..."></textarea>

<!-- ใช้กับ datalist -->
<input
  type="text"
  name="skill"
  list="skills"
  placeholder="เลือกหรือพิมพ์ทักษะ"
/>
<datalist id="skills">
  <option value="JavaScript"></option>
  <option value="Python"></option>
  <option value="Java"></option>
</datalist>
```

### 2.2 Validation Attributes

#### `required` Attribute

```html
<!-- ฟิลด์บังคับ -->
<form>
  <div class="form-group">
    <label for="name">ชื่อ *</label>
    <input type="text" id="name" name="name" required />
  </div>

  <div class="form-group">
    <label for="email">อีเมล *</label>
    <input type="email" id="email" name="email" required />
  </div>

  <!-- Radio ที่บังคับเลือก -->
  <fieldset>
    <legend>เพศ *</legend>
    <input type="radio" name="gender" value="male" id="gender-m" required />
    <label for="gender-m">ชาย</label>
    <input type="radio" name="gender" value="female" id="gender-f" required />
    <label for="gender-f">หญิง</label>
  </fieldset>

  <!-- Checkbox ที่บังคับติ๊ก -->
  <div class="form-group">
    <input type="checkbox" id="agree" name="agree" required />
    <label for="agree">ยอมรับเงื่อนไขการใช้งาน *</label>
  </div>

  <button type="submit">ส่งข้อมูล</button>
</form>
```

#### `pattern` Attribute

```html
<!-- รูปแบบเฉพาะ -->
<form class="pattern-form">
  <div class="form-group">
    <label for="phone">เบอร์โทรศัพท์ (10 หลัก)</label>
    <input
      type="tel"
      id="phone"
      name="phone"
      pattern="[0-9]{10}"
      title="กรุณาใส่เบอร์โทร 10 หลัก"
      placeholder="0812345678"
    />
  </div>

  <div class="form-group">
    <label for="id-card">เลขประจำตัวประชาชน (13 หลัก)</label>
    <input
      type="text"
      id="id-card"
      name="idCard"
      pattern="[0-9]{13}"
      title="กรุณาใส่เลขประจำตัว 13 หลัก"
      placeholder="1234567890123"
    />
  </div>

  <div class="form-group">
    <label for="postal-code">รหัสไปรษณีย์ (5 หลัก)</label>
    <input
      type="text"
      id="postal-code"
      name="postalCode"
      pattern="[0-9]{5}"
      title="กรุณาใส่รหัสไปรษณีย์ 5 หลัก"
      placeholder="10110"
    />
  </div>

  <div class="form-group">
    <label for="license-plate">ป้ายทะเบียนรถ</label>
    <input
      type="text"
      id="license-plate"
      name="licensePlate"
      pattern="[ก-ฮ]{1,2}[0-9]{1,4}"
      title="เช่น กข1234 หรือ 1กข2345"
      placeholder="กข1234"
    />
  </div>

  <div class="form-group">
    <label for="strong-password">รหัสผ่านแข็งแรง</label>
    <input
      type="password"
      id="strong-password"
      name="password"
      pattern="^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$"
      title="ต้องมีตัวพิมพ์เล็ก พิมพ์ใหญ่ ตัวเลข และอักขระพิเศษ อย่างน้อย 8 ตัว"
    />
  </div>

  <button type="submit">ตรวจสอบ</button>
</form>
```

#### `min`, `max`, `step` Attributes

```html
<!-- สำหรับตัวเลข -->
<form class="number-form">
  <div class="form-group">
    <label for="age">อายุ (18-99 ปี)</label>
    <input
      type="number"
      id="age"
      name="age"
      min="18"
      max="99"
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
    <label for="rating">คะแนน (1-5)</label>
    <input
      type="range"
      id="rating"
      name="rating"
      min="1"
      max="5"
      step="0.5"
      value="3"
      oninput="updateRatingValue(this.value)"
    />
    <output id="rating-output">3</output>
  </div>

  <!-- สำหรับวันที่ -->
  <div class="form-group">
    <label for="birth-date">วันเกิด</label>
    <input
      type="date"
      id="birth-date"
      name="birthDate"
      min="1920-01-01"
      max="2010-12-31"
    />
  </div>

  <div class="form-group">
    <label for="appointment">นัดหมาย</label>
    <input
      type="datetime-local"
      id="appointment"
      name="appointment"
      min="2024-01-01T09:00"
      max="2024-12-31T17:00"
      step="1800"
    />
    <!-- ขั้น 30 นาที -->
  </div>

  <button type="submit">บันทึก</button>
</form>

<script>
  function updateRatingValue(value) {
    document.getElementById('rating-output').value = value;
  }
</script>
```

### 2.3 State Attributes

#### `disabled` Attribute

```html
<!-- ปิดการใช้งานแบบต่างๆ -->
<form class="disabled-example">
  <div class="form-group">
    <label for="username">ชื่อผู้ใช้</label>
    <input
      type="text"
      id="username"
      name="username"
      value="john_doe"
      disabled
    />
    <small>ไม่สามารถแก้ไขได้</small>
  </div>

  <div class="form-group">
    <label for="role">บทบาท</label>
    <select id="role" name="role" disabled>
      <option value="admin" selected>ผู้ดูแลระบบ</option>
      <option value="user">ผู้ใช้งานทั่วไป</option>
    </select>
  </div>

  <fieldset disabled>
    <legend>ข้อมูลที่ไม่สามารถแก้ไขได้</legend>
    <input type="text" name="field1" value="ข้อมูล 1" />
    <input type="text" name="field2" value="ข้อมูล 2" />
    <textarea name="field3">ข้อมูล 3</textarea>
  </fieldset>

  <div class="form-group">
    <input
      type="checkbox"
      id="notifications"
      name="notifications"
      checked
      disabled
    />
    <label for="notifications">การแจ้งเตือน (ไม่สามารถเปลี่ยนได้)</label>
  </div>

  <button type="submit" disabled>ส่งข้อมูล</button>
</form>
```

#### `readonly` Attribute

```html
<!-- อ่านได้อย่างเดียว -->
<form class="readonly-example">
  <div class="form-group">
    <label for="invoice-number">เลขที่ใบแจ้งหนี้</label>
    <input
      type="text"
      id="invoice-number"
      name="invoiceNumber"
      value="INV-2024-001"
      readonly
    />
  </div>

  <div class="form-group">
    <label for="calculated-total">ยอดรวม (คำนวณอัตโนมัติ)</label>
    <input
      type="number"
      id="calculated-total"
      name="total"
      value="1500"
      readonly
    />
  </div>

  <div class="form-group">
    <label for="terms">เงื่อนไขการใช้งาน</label>
    <textarea id="terms" name="terms" rows="10" readonly>
นี่คือเงื่อนไขการใช้งานที่ผู้ใช้สามารถอ่านและเลือกข้อความได้
แต่ไม่สามารถแก้ไขเนื้อหาได้
ผู้ใช้สามารถ copy ข้อความได้
    </textarea>
  </div>

  <!-- readonly ไม่ทำงานกับ checkbox, radio, select -->
  <div class="form-group">
    <label for="editable-notes">หมายเหตุ (แก้ไขได้)</label>
    <textarea id="editable-notes" name="notes" rows="3"></textarea>
  </div>

  <button type="submit">ส่งข้อมูล</button>
</form>
```

#### `checked` และ `selected` Attributes

```html
<form class="default-values">
  <!-- Radio buttons พร้อมค่าเริ่มต้น -->
  <fieldset>
    <legend>ขนาดเสื้อ</legend>
    <label><input type="radio" name="size" value="S" /> S</label>
    <label><input type="radio" name="size" value="M" checked /> M</label>
    <label><input type="radio" name="size" value="L" /> L</label>
    <label><input type="radio" name="size" value="XL" /> XL</label>
  </fieldset>

  <!-- Checkboxes พร้อมค่าเริ่มต้น -->
  <fieldset>
    <legend>บริการเสริม</legend>
    <label
      ><input type="checkbox" name="services" value="delivery" checked />
      จัดส่งถึงบ้าน</label
    >
    <label
      ><input type="checkbox" name="services" value="gift-wrap" />
      ห่อของขวัญ</label
    >
    <label
      ><input type="checkbox" name="services" value="express" checked />
      ส่งด่วน</label
    >
    <label
      ><input type="checkbox" name="services" value="insurance" />
      ประกันภัย</label
    >
  </fieldset>

  <!-- Select พร้อมค่าเริ่มต้น -->
  <div class="form-group">
    <label for="country">ประเทศ</label>
    <select id="country" name="country">
      <option value="">-- เลือกประเทศ --</option>
      <option value="TH" selected>ไทย</option>
      <option value="US">สหรัฐอเมริกา</option>
      <option value="JP">ญี่ปุ่น</option>
      <option value="KR">เกาหลีใต้</option>
    </select>
  </div>

  <!-- Multiple select -->
  <div class="form-group">
    <label for="languages">ภาษาที่ใช้ได้</label>
    <select id="languages" name="languages" multiple size="4">
      <option value="th" selected>ไทย</option>
      <option value="en" selected>อังกฤษ</option>
      <option value="jp">ญี่ปุ่น</option>
      <option value="kr">เกาหลี</option>
      <option value="cn">จีน</option>
    </select>
  </div>

  <button type="submit">บันทึกการตั้งค่า</button>
</form>
```

## 3. ตัวอย่างการใช้งานครบครัน

### 3.1 ฟอร์มสมัครสมาชิกขั้นสูง

```html
<form
  action="/advanced-register"
  method="POST"
  class="advanced-registration"
  novalidate
>
  <h1>สมัครสมาชิก</h1>

  <!-- ข้อมูลเข้าสู่ระบบ -->
  <fieldset>
    <legend>ข้อมูลเข้าสู่ระบบ</legend>

    <div class="form-group">
      <label for="username">ชื่อผู้ใช้ *</label>
      <input
        type="text"
        id="username"
        name="username"
        pattern="^[a-zA-Z0-9_]{3,20}$"
        title="3-20 ตัวอักษร ใช้ได้เฉพาะ a-z, A-Z, 0-9, _"
        placeholder="username123"
        required
        oninput="checkUsernameAvailability(this.value)"
      />
      <div class="validation-message" id="username-status"></div>
    </div>

    <div class="form-group">
      <label for="email">อีเมล *</label>
      <input
        type="email"
        id="email"
        name="email"
        placeholder="your-email@example.com"
        required
        list="email-suggestions"
      />
      <datalist id="email-suggestions">
        <option value="@gmail.com"></option>
        <option value="@yahoo.com"></option>
        <option value="@hotmail.com"></option>
        <option value="@outlook.com"></option>
      </datalist>
    </div>

    <div class="form-group">
      <label for="password">รหัสผ่าน *</label>
      <input
        type="password"
        id="password"
        name="password"
        pattern="^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$"
        title="อย่างน้อย 8 ตัวอักษร มีตัวพิมพ์เล็ก พิมพ์ใหญ่ ตัวเลข และอักขระพิเศษ"
        required
        oninput="updatePasswordStrength(this.value)"
      />
      <div class="password-strength">
        <label>ความแข็งแรงรหัสผ่าน:</label>
        <meter id="password-strength-meter" min="0" max="4" value="0"></meter>
        <span id="password-strength-text">อ่อนแอ</span>
      </div>
    </div>

    <div class="form-group">
      <label for="confirm-password">ยืนยันรหัสผ่าน *</label>
      <input
        type="password"
        id="confirm-password"
        name="confirmPassword"
        required
        oninput="checkPasswordMatch()"
      />
      <div class="validation-message" id="password-match-status"></div>
    </div>
  </fieldset>

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
          pattern="[ก-๙a-zA-Z\s]{2,50}"
          required
        />
      </div>

      <div class="form-group">
        <label for="last-name">นามสกุล *</label>
        <input
          type="text"
          id="last-name"
          name="lastName"
          pattern="[ก-๙a-zA-Z\s]{2,50}"
          required
        />
      </div>
    </div>

    <div class="form-row">
      <div class="form-group">
        <label for="birth-date">วันเกิด</label>
        <input
          type="date"
          id="birth-date"
          name="birthDate"
          min="1920-01-01"
          max="2010-12-31"
          onchange="calculateAge()"
        />
      </div>

      <div class="form-group">
        <label for="age">อายุ</label>
        <input type="number" id="age" name="age" readonly />
      </div>
    </div>

    <div class="form-group">
      <label for="phone">เบอร์โทรศัพท์</label>
      <input
        type="tel"
        id="phone"
        name="phone"
        pattern="[0-9]{10}"
        placeholder="0812345678"
      />
    </div>
  </fieldset>

  <!-- ความสนใจและทักษะ -->
  <fieldset>
    <legend>ความสนใจและทักษะ</legend>

    <div class="form-group">
      <label for="interests">ความสนใจหลัก</label>
      <select id="interests" name="interests" multiple size="5">
        <optgroup label="เทคโนโลยี">
          <option value="programming">การเขียนโปรแกรม</option>
          <option value="web-design">การออกแบบเว็บ</option>
          <option value="data-science">วิทยาศาสตร์ข้อมูล</option>
          <option value="ai">ปัญญาประดิษฐ์</option>
        </optgroup>

        <optgroup label="ศิลปะและการออกแบบ">
          <option value="graphic-design">กราฟิกดีไซน์</option>
          <option value="photography">การถ่ายภาพ</option>
          <option value="music">ดนตรี</option>
          <option value="drawing">การวาดภาพ</option>
        </optgroup>

        <optgroup label="กีฬาและออกกำลังกาย">
          <option value="football">ฟุตบอล</option>
          <option value="basketball">บาสเกตบอล</option>
          <option value="swimming">ว่ายน้ำ</option>
          <option value="fitness">ฟิตเนส</option>
        </optgroup>
      </select>
      <small>กด Ctrl+Click เพื่อเลือกหลายรายการ</small>
    </div>

    <div class="form-group">
      <label for="skill-level">ระดับทักษะการใช้คอมพิวเตอร์:</label>
      <input
        type="range"
        id="skill-level"
        name="skillLevel"
        min="1"
        max="10"
        value="5"
        step="1"
        oninput="updateSkillLevel(this.value)"
      />
      <output id="skill-level-output">5</output>/10
      <div class="skill-labels">
        <span>เริ่มต้น</span>
        <span>ปานกลาง</span>
        <span>ขั้นสูง</span>
      </div>
    </div>
  </fieldset>

  <!-- การตั้งค่าบัญชี -->
  <fieldset>
    <legend>การตั้งค่าบัญชี</legend>

    <div class="form-group">
      <label>ประเภทบัญชี:</label>
      <div class="radio-group">
        <label
          ><input type="radio" name="accountType" value="personal" checked />
          บุคคลทั่วไป</label
        >
        <label
          ><input type="radio" name="accountType" value="business" />
          ธุรกิจ</label
        >
        <label
          ><input type="radio" name="accountType" value="organization" />
          องค์กร</label
        >
      </div>
    </div>

    <div class="form-group">
      <label>การแจ้งเตือน:</label>
      <div class="checkbox-group">
        <label
          ><input
            type="checkbox"
            name="notifications[]"
            value="email"
            checked
          />
          อีเมล</label
        >
        <label
          ><input type="checkbox" name="notifications[]" value="sms" />
          SMS</label
        >
        <label
          ><input type="checkbox" name="notifications[]" value="push" checked />
          Push Notification</label
        >
      </div>
    </div>

    <div class="form-group">
      <label for="privacy-level">ระดับความเป็นส่วนตัว:</label>
      <select id="privacy-level" name="privacyLevel">
        <option value="public">สาธารณะ</option>
        <option value="friends" selected>เฉพาะเพื่อน</option>
        <option value="private">ส่วนตัว</option>
      </select>
    </div>
  </fieldset>

  <!-- ข้อตกลงและยืนยัน -->
  <fieldset>
    <legend>ข้อตกลงและยืนยัน</legend>

    <div class="form-group">
      <input type="checkbox" id="agree-terms" name="agreeTerms" required />
      <label for="agree-terms">
        ยอมรับ <a href="/terms" target="_blank">เงื่อนไขการใช้งาน</a> และ
        <a href="/privacy" target="_blank">นโยบายความเป็นส่วนตัว</a> *
      </label>
    </div>

    <div class="form-group">
      <input type="checkbox" id="marketing-consent" name="marketingConsent" />
      <label for="marketing-consent">
        ยินยอมให้ส่งข้อมูลการตลาดและโปรโมชั่น
      </label>
    </div>

    <div class="form-group">
      <label for="referral-code">รหัสแนะนำ (ถ้ามี)</label>
      <input
        type="text"
        id="referral-code"
        name="referralCode"
        pattern="[A-Z0-9]{6,10}"
        placeholder="ABC123DEF"
      />
    </div>
  </fieldset>

  <!-- สถานะการสมัคร -->
  <div class="registration-progress">
    <label>ความคืบหน้าการกรอกข้อมูล:</label>
    <progress id="form-progress" value="0" max="100"></progress>
    <span id="progress-percentage">0%</span>
  </div>

  <div class="form-actions">
    <button type="reset" class="btn btn-secondary">ล้างข้อมูล</button>
    <button type="submit" id="submit-btn" class="btn btn-primary" disabled>
      สมัครสมาชิก
    </button>
  </div>
</form>

<script>
  // ตรวจสอบความพร้อมของชื่อผู้ใช้
  async function checkUsernameAvailability(username) {
    const status = document.getElementById('username-status');

    if (username.length < 3) {
      status.textContent = '';
      return;
    }

    status.textContent = 'กำลังตรวจสอบ...';
    status.className = 'checking';

    // จำลองการเรียก API
    setTimeout(() => {
      const isAvailable = !['admin', 'user', 'test'].includes(
        username.toLowerCase()
      );

      if (isAvailable) {
        status.textContent = '✓ ชื่อผู้ใช้นี้ใช้ได้';
        status.className = 'available';
      } else {
        status.textContent = '✗ ชื่อผู้ใช้นี้ถูกใช้แล้ว';
        status.className = 'unavailable';
      }

      updateFormProgress();
    }, 1000);
  }

  // ตรวจสอบความแข็งแรงของรหัสผ่าน
  function updatePasswordStrength(password) {
    const meter = document.getElementById('password-strength-meter');
    const text = document.getElementById('password-strength-text');

    let strength = 0;
    let feedback = 'อ่อนแอ';

    if (password.length >= 8) strength++;
    if (/[a-z]/.test(password)) strength++;
    if (/[A-Z]/.test(password)) strength++;
    if (/[0-9]/.test(password)) strength++;
    if (/[@$!%*?&]/.test(password)) strength++;

    meter.value = strength;

    switch (strength) {
      case 0:
      case 1:
        feedback = 'อ่อนแอ';
        break;
      case 2:
        feedback = 'ปานกลาง';
        break;
      case 3:
        feedback = 'ดี';
        break;
      case 4:
      case 5:
        feedback = 'แข็งแรง';
        break;
    }

    text.textContent = feedback;
    updateFormProgress();
  }

  // ตรวจสอบรหัสผ่านตรงกัน
  function checkPasswordMatch() {
    const password = document.getElementById('password').value;
    const confirmPassword = document.getElementById('confirm-password').value;
    const status = document.getElementById('password-match-status');

    if (confirmPassword === '') {
      status.textContent = '';
      return;
    }

    if (password === confirmPassword) {
      status.textContent = '✓ รหัสผ่านตรงกัน';
      status.className = 'match';
    } else {
      status.textContent = '✗ รหัสผ่านไม่ตรงกัน';
      status.className = 'no-match';
    }

    updateFormProgress();
  }

  // คำนวณอายุ
  function calculateAge() {
    const birthDate = new Date(document.getElementById('birth-date').value);
    const today = new Date();
    const age = Math.floor(
      (today - birthDate) / (365.25 * 24 * 60 * 60 * 1000)
    );

    document.getElementById('age').value = age;
    updateFormProgress();
  }

  // อัปเดตระดับทักษะ
  function updateSkillLevel(value) {
    document.getElementById('skill-level-output').value = value;
    updateFormProgress();
  }

  // อัปเดตความคืบหน้าการกรอกฟอร์ม
  function updateFormProgress() {
    const form = document.querySelector('.advanced-registration');
    const requiredFields = form.querySelectorAll('[required]');
    let completedFields = 0;

    requiredFields.forEach((field) => {
      if (field.type === 'checkbox' || field.type === 'radio') {
        if (field.checked) completedFields++;
      } else if (field.value.trim() !== '') {
        completedFields++;
      }
    });

    const progress = Math.round(
      (completedFields / requiredFields.length) * 100
    );
    document.getElementById('form-progress').value = progress;
    document.getElementById('progress-percentage').textContent = progress + '%';

    // เปิด/ปิดปุ่มส่ง
    const submitBtn = document.getElementById('submit-btn');
    submitBtn.disabled = progress < 100;
  }

  // ตรวจสอบฟอร์มเมื่อมีการเปลี่ยนแปลง
  document.addEventListener('DOMContentLoaded', function () {
    const form = document.querySelector('.advanced-registration');
    const inputs = form.querySelectorAll('input, select, textarea');

    inputs.forEach((input) => {
      input.addEventListener('input', updateFormProgress);
      input.addEventListener('change', updateFormProgress);
    });

    updateFormProgress();
  });
</script>
```

## 4. Best Practices

### 4.1 การใช้ Attributes อย่างเหมาะสม

```html
<!-- ✅ ควรทำ -->
<input
  type="email"
  name="email"
  required
  placeholder="your-email@example.com"
  autocomplete="email"
  aria-describedby="email-help"
/>
<div id="email-help">เราจะไม่แชร์อีเมลของคุณกับใคร</div>

<!-- ❌ หลีกเลี่ยง -->
<input type="text" name="email" placeholder="อีเมล *" />
<!-- ไม่มี validation -->
```

### 4.2 การใช้ Progressive Enhancement

```html
<!-- ✅ ใช้ fallback สำหรับ browser เก่า -->
<input
  type="email"
  name="email"
  pattern="[^@\s]+@[^@\s]+\.[^@\s]+"
  title="กรุณาใส่อีเมลที่ถูกต้อง"
/>

<input
  type="date"
  name="date"
  pattern="\d{4}-\d{2}-\d{2}"
  placeholder="YYYY-MM-DD"
/>
```

### 4.3 การจัดการ Validation

```html
<!-- ✅ ใช้ทั้ง client-side และ server-side validation -->
<form novalidate>
  <!-- ปิด browser validation เพื่อใช้ custom validation -->
  <input type="email" name="email" required data-validate="email" />
  <div class="error-message" id="email-error"></div>
</form>
```

---

**สรุป**: การใช้ elements เสริมและ attributes ต่างๆ อย่างถูกต้องจะช่วยให้ฟอร์มมีฟังก์ชันการทำงานที่ดี มี UX ที่ยอดเยี่ยม และรองรับ accessibility ได้อย่างครบถ้วน
