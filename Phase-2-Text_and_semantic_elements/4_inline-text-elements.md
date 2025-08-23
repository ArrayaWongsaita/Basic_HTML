# Text Elements และ Semantic Markup: `<span>`, `<mark>`, `<small>`, `<sup>`, `<sub>`, `<abbr>`, `<cite>`, `<code>`, `<pre>`, `<blockquote>`, `<q>`

## แนวคิดพื้นฐาน: Inline vs Block vs Semantic

### 🎯 **ประเภท Elements**

- **Inline Elements**: แสดงในบรรทัดเดียวกัน ไม่ขึ้นบรรทัดใหม่
- **Block Elements**: ขึ้นบรรทัดใหม่ครอบครองความกว้างเต็ม
- **Semantic Elements**: มีความหมายเฉพาะด้วยการใช้งาน

---

## 1. `<span>` Tag - Container ทั่วไป

### 📝 **ความหมายและการใช้งาน**

- **ประเภท**: Inline element ที่ไม่มีความหมายพิเศษ
- **วัตถุประสงค์**: จัดกลุ่มข้อความเพื่อการตกแต่งหรือ scripting
- **การแสดงผล**: ไม่เปลี่ยนรูปแบบใดๆ (จนกว่าจะมี CSS)

#### **ตัวอย่างการใช้งาน**

```html
<!-- การเน้นสีข้อความ -->
<p>ราคาสินค้า: <span style="color: red; font-weight: bold;">1,990 บาท</span></p>

<!-- การจัดกลุ่มเพื่อ CSS -->
<p>สถานะ: <span class="status-active">ใช้งานได้</span></p>

<!-- การใช้งานกับ JavaScript -->
<p>คะแนนปัจจุบัน: <span id="score">0</span> คะแนน</p>

<!-- การจัดกลุ่มข้อความหลายคำ -->
<p>
  <span class="highlight">ข้อความสำคัญ</span>
  ที่ต้องการเน้นเป็นพิเศษ
</p>
```

#### **การใช้งานขั้นสูง**

```html
<!-- Tooltip information -->
<p>
  <span title="HyperText Markup Language">HTML</span>
  เป็นภาษาสำหรับสร้างเว็บเพจ
</p>

<!-- Language specification -->
<p>
  คำว่า <span lang="en">responsive design</span>
  หมายถึงการออกแบบที่ปรับตัวได้
</p>

<!-- Data attributes สำหรับ JavaScript -->
<p>
  สินค้า: <span data-product-id="12345" data-price="1990"> iPhone 15 Pro </span>
</p>
```

#### **CSS styling ตัวอย่าง**

```html
<style>
  .highlight {
    background-color: yellow;
    padding: 2px 4px;
    border-radius: 3px;
  }

  .price {
    color: #e74c3c;
    font-weight: bold;
    font-size: 1.2em;
  }

  .status-active {
    color: #27ae60;
    background-color: #d5f4e6;
    padding: 2px 8px;
    border-radius: 12px;
    font-size: 0.9em;
  }
</style>

<p>ราคา: <span class="price">1,990 บาท</span></p>
<p>สถานะ: <span class="status-active">พร้อมใช้งาน</span></p>
```

---

## 2. `<mark>` Tag - การเน้นด้วยสีเหลือง

### 📝 **ความหมายและการใช้งาน**

- **ความหมาย**: เน้นข้อความที่เกี่ยวข้องในบริบทปัจจุบัน
- **การแสดงผล**: พื้นหลังสีเหลือง (เหมือนปากกาเน้นข้อความ)
- **ใช้สำหรับ**: ผลการค้นหา, ข้อความสำคัญในบริบท

#### **ตัวอย่างการใช้งาน**

```html
<!-- ผลการค้นหา -->
<p>เรียนรู้ <mark>HTML</mark> และ <mark>CSS</mark> สำหรับการพัฒนาเว็บ</p>

<!-- เน้นข้อความสำคัญ -->
<p>
  โปรดจำไว้ว่า <mark>รหัสผ่านต้องมีอย่างน้อย 8 ตัวอักษร</mark>
  และประกอบด้วยตัวเลขและตัวอักษร
</p>

<!-- การใช้ในบทความ -->
<p>
  ผลการวิจัยพบว่า <mark>90% ของผู้ใช้ออกจากเว็บไซต์</mark>
  หากโหลดช้าเกิน 3 วินาที
</p>

<!-- การเน้นคำศัพท์ใหม่ -->
<p>
  <mark>Progressive Web App (PWA)</mark>
  คือเทคโนโลยีที่ทำให้เว็บไซต์ทำงานเหมือนแอปมือถือ
</p>
```

#### **การปรับแต่งด้วย CSS**

```html
<style>
  /* เปลี่ยนสีพื้นหลัง */
  mark {
    background-color: #ffeb3b;
    color: #000;
    padding: 2px 4px;
    border-radius: 3px;
  }

  /* สไตล์พิเศษ */
  mark.important {
    background-color: #ff5722;
    color: white;
    font-weight: bold;
  }

  mark.search-result {
    background-color: #4caf50;
    color: white;
  }
</style>

<p>ข้อมูล <mark class="important">สำคัญมาก</mark> ที่ต้องจำ</p>
<p>ผลค้นหา: <mark class="search-result">JavaScript</mark></p>
```

---

## 3. `<small>` Tag - ข้อความขนาดเล็ก

### 📝 **ความหมายและการใช้งาน**

- **ความหมาย**: ข้อความที่มีความสำคัญรอง เช่น หมายเหตุ, ข้อกำหนด
- **การแสดงผล**: ตัวอักษรขนาดเล็กกว่าปกติ
- **ใช้สำหรับ**: Copyright, disclaimer, หมายเหตุ

#### **ตัวอย่างการใช้งาน**

```html
<!-- Copyright -->
<footer>
  <small>&copy; 2024 ABC Company. สงวนลิขสิทธิ์.</small>
</footer>

<!-- ข้อกำหนดและเงื่อนไข -->
<p>
  ราคาพิเศษ 1,990 บาท
  <small>*ราคาไม่รวม VAT และค่าจัดส่ง</small>
</p>

<!-- หมายเหตุ -->
<p>
  โปรแกรมนี้ใช้งานได้กับ Windows 10 ขึ้นไป
  <small>(แนะนำ Windows 11 สำหรับประสิทธิภาพที่ดีที่สุด)</small>
</p>

<!-- ข้อมูลเพิ่มเติม -->
<article>
  <h2>บทความเกี่ยวกับ AI</h2>
  <p>เนื้อหาบทความ...</p>
  <small>อัปเดตล่าสุด: 15 มกราคม 2024 | ผู้เขียน: นาย ก</small>
</article>

<!-- เวลาและวันที่ -->
<p>
  โพสต์ใหม่: "เรียนรู้ React.js"
  <small>เผยแพร่เมื่อ 2 ชั่วโมงที่แล้ว</small>
</p>
```

#### **การใช้งานที่ถูกต้อง vs ผิด**

```html
<!-- ✅ ถูก - ข้อมูลรอง -->
<p>
  ราคา: 1,990 บาท
  <small>ลดจาก 2,500 บาท</small>
</p>

<!-- ❌ ผิด - ไม่ควรใช้เพื่อให้ข้อความเล็ก -->
<small>หัวข้อหลักของบทความ</small>

<!-- ✅ ถูก - ใช้ CSS แทน -->
<h1 style="font-size: 14px;">หัวข้อหลักของบทความ</h1>
```

---

## 4. `<sup>` Tag - ตัวยก และ `<sub>` Tag - ตัวห้อย

### 📝 **ความหมายและการใช้งาน**

#### **`<sup>` (Superscript)**

- **ใช้สำหรับ**: เลขยก, หมายเหตุ, หน่วยกำลัง, ลิขสิทธิ์

#### **`<sub>` (Subscript)**

- **ใช้สำหรับ**: สูตรเคมี, คณิตศาสตร์, ดัชนี

#### **ตัวอย่างการใช้งาน**

```html
<!-- คณิตศาสตร์ -->
<p>สูตรคำนวณพื้นที่วงกลม: A = πr<sup>2</sup></p>
<p>ทฤษฎีบทพีทาโกรัส: a<sup>2</sup> + b<sup>2</sup> = c<sup>2</sup></p>

<!-- เคมี -->
<p>น้ำมีสูตร H<sub>2</sub>O</p>
<p>ก๊าซคาร์บอนไดออกไซด์: CO<sub>2</sub></p>
<p>กรดกำมะถัน: H<sub>2</sub>SO<sub>4</sub></p>

<!-- หมายเหตุอ้างอิง -->
<p>
  ตามการศึกษาของมหาวิทยาลัย ABC<sup>1</sup>
  พบว่าการเรียนออนไลน์มีประสิทธิภาพสูง<sup>2</sup>
</p>

<!-- ลิขสิทธิ์และเครื่องหมายการค้า -->
<p>Microsoft<sup>®</sup> Windows<sup>™</sup></p>
<p>iPhone<sup>®</sup> เป็นเครื่องหมายการค้าของ Apple Inc.</p>

<!-- วันที่ -->
<p>วันที่ 1<sup>st</sup> มกราคม 2024</p>
<p>ศตวรรษที่ 21<sup>st</sup></p>

<!-- สูตรฟิสิกส์ -->
<p>E = mc<sup>2</sup> (สมการของไอน์สไตน์)</p>
<p>ความเร่งโน้มถ่วง: 9.8 m/s<sup>2</sup></p>

<!-- การเขียนดัชนี -->
<p>ข้อมูลในตาราง A<sub>1</sub>, B<sub>2</sub>, C<sub>3</sub></p>
<p>ตัวแปร x<sub>n</sub> และ y<sub>n+1</sub></p>
```

#### **การจัดรูปแบบด้วย CSS**

```html
<style>
  sup,
  sub {
    font-size: 0.75em;
    line-height: 0;
    position: relative;
    vertical-align: baseline;
  }

  sup {
    top: -0.5em;
  }

  sub {
    bottom: -0.25em;
  }

  /* สำหรับสูตรเคมี */
  .chemical-formula sub {
    color: #666;
    font-weight: normal;
  }

  /* สำหรับคณิตศาสตร์ */
  .math-formula sup {
    color: #0066cc;
    font-weight: bold;
  }
</style>

<p class="chemical-formula">H<sub>2</sub>SO<sub>4</sub></p>
<p class="math-formula">x<sup>2</sup> + y<sup>2</sup> = z<sup>2</sup></p>
```

---

## 5. `<abbr>` Tag - คำย่อ

### 📝 **ความหมายและการใช้งาน**

- **ความหมาย**: คำย่อหรือตัวย่อ
- **คุณสมบัติ**: ใช้ `title` attribute เพื่อแสดงความหมายเต็ม
- **การแสดงผล**: เส้นประใต้รูปปุ่มเมื่อ hover (ขึ้นกับ browser)

#### **ตัวอย่างการใช้งาน**

```html
<!-- คำย่อทั่วไป -->
<p>
  <abbr title="HyperText Markup Language">HTML</abbr>
  เป็นภาษาสำหรับสร้างเว็บเพจ
</p>

<p>
  <abbr title="Cascading Style Sheets">CSS</abbr>
  ใช้สำหรับตกแต่งหน้าเว็บ
</p>

<!-- คำย่อทางเทคนิค -->
<p>
  <abbr title="Application Programming Interface">API</abbr>
  คือชุดคำสั่งสำหรับการติดต่อระหว่างโปรแกรม
</p>

<p>
  เว็บไซต์นี้ใช้ <abbr title="Secure Sockets Layer">SSL</abbr>
  เพื่อความปลอดภัย
</p>

<!-- คำย่อองค์กร -->
<p>
  <abbr title="World Wide Web Consortium">W3C</abbr>
  เป็นองค์กรที่กำหนดมาตรฐานเว็บ
</p>

<p>
  <abbr title="บริษัท ไมโครซอฟท์ (ประเทศไทย) จำกัด">Microsoft Thailand</abbr>
  จัดอบรมหลักสูรโปรแกรมมิ่ง
</p>

<!-- คำย่อหน่วยวัด -->
<p>ไฟล์มีขนาด 2.5 <abbr title="Megabytes">MB</abbr></p>
<p>ความเร็วอินเทอร์เน็ต 100 <abbr title="Megabits per second">Mbps</abbr></p>

<!-- คำย่อทางการแพทย์ -->
<p>ผู้ป่วยได้รับการตรวจ <abbr title="Magnetic Resonance Imaging">MRI</abbr></p>
```

#### **การปรับแต่งด้วย CSS**

```html
<style>
  abbr {
    text-decoration: underline dotted;
    cursor: help;
    border-bottom: 1px dotted #666;
  }

  abbr:hover {
    color: #0066cc;
    background-color: #f0f8ff;
    padding: 1px 2px;
    border-radius: 3px;
  }

  /* สำหรับ abbreviation ที่สำคัญ */
  abbr.important {
    font-weight: bold;
    color: #e74c3c;
  }
</style>

<p>
  เรียนรู้ <abbr class="important" title="HyperText Markup Language">HTML</abbr>
  เบื้องต้น
</p>
```

---

## 6. `<cite>` Tag - การอ้างอิง

### 📝 **ความหมายและการใช้งาน**

- **ความหมาย**: ชื่อผลงาน เช่น หนังสือ, ภาพยนตร์, เพลง, บทความ
- **การแสดงผล**: ตัวเอียง (italic) โดยค่าเริ่มต้น
- **ใช้สำหรับ**: การอ้างอิงแหล่งที่มา

#### **ตัวอย่างการใช้งาน**

```html
<!-- หนังสือ -->
<p>
  หนังสือ <cite>Harry Potter and the Philosopher's Stone</cite>
  เขียนโดย J.K. Rowling
</p>

<!-- ภาพยนตร์ -->
<p>
  ภาพยนตร์ <cite>The Matrix</cite>
  เป็นหนังแนว Sci-Fi ที่มีชื่อเสียง
</p>

<!-- เพลง -->
<p>
  เพลง <cite>Bohemian Rhapsody</cite>
  ของวง Queen เป็นเพลงคลาสสิกที่ยิ่งใหญ่
</p>

<!-- บทความ -->
<p>
  ตามบทความ <cite>The Future of Web Development</cite>
  ใน TechCrunch ระบุว่า...
</p>

<!-- เว็บไซต์ -->
<p>
  ข้อมูลจาก <cite>MDN Web Docs</cite>
  เป็นแหล่งเรียนรู้ที่น่าเชื่อถือ
</p>

<!-- รายงานการวิจัย -->
<blockquote>
  "การเรียนออนไลน์มีประสิทธิภาพเท่ากับการเรียนในห้องเรียน"
  <cite>— Journal of Educational Technology, 2024</cite>
</blockquote>

<!-- ผลงานศิลปะ -->
<p>
  ภาพวาด <cite>The Starry Night</cite>
  ของ Vincent van Gogh เป็นผลงานที่มีชื่อเสียง
</p>
```

#### **การใช้งานกับ CSS**

```html
<style>
  cite {
    font-style: italic;
    color: #666;
    font-weight: normal;
  }

  /* สำหรับชื่อหนังสือ */
  cite.book {
    color: #8b4513;
    font-weight: bold;
  }

  /* สำหรับภาพยนตร์ */
  cite.movie {
    color: #4b0082;
  }

  /* สำหรับเพลง */
  cite.song {
    color: #ff6347;
  }
</style>

<p>หนังสือ <cite class="book">1984</cite> โดย George Orwell</p>
<p>ภาพยนตร์ <cite class="movie">Inception</cite> กำกับโดย Christopher Nolan</p>
<p>เพลง <cite class="song">Yesterday</cite> ของ The Beatles</p>
```

---

## 7. `<code>` Tag - โค้ดโปรแกรม

### 📝 **ความหมายและการใช้งาน**

- **ความหมาย**: โค้ดคำสั่งคอมพิวเตร์
- **การแสดงผล**: ฟอนต์ monospace (เช่น Courier)
- **ใช้สำหรับ**: คำสั่ง, ฟังก์ชัน, ตัวแปร

#### **ตัวอย่างการใช้งาน**

```html
<!-- คำสั่งเดี่ยว -->
<p>ใช้คำสั่ง <code>console.log()</code> เพื่อแสดงผลใน browser console</p>

<!-- ตัวแปร -->
<p>กำหนดค่าให้ตัวแปร <code>userName</code> ด้วยข้อมูลผู้ใช้</p>

<!-- ฟังก์ชัน -->
<p>เรียกใช้ฟังก์ชัน <code>getElementById()</code> เพื่อค้นหา element</p>

<!-- HTML tags -->
<p>ใช้ <code>&lt;div&gt;</code> สำหรับจัดกลุ่ม elements</p>

<!-- CSS properties -->
<p>ตั้งค่า <code>display: flex</code> เพื่อใช้ Flexbox layout</p>

<!-- คำสั่ง command line -->
<p>รันคำสั่ง <code>npm install</code> เพื่อติดตั้ง dependencies</p>

<!-- File paths -->
<p>ไฟล์อยู่ที่ <code>/Users/username/Documents/project/</code></p>

<!-- HTTP methods -->
<p>ใช้ <code>GET</code> method เพื่อดึงข้อมูลจาก API</p>
```

#### **การจัดรูปแบบด้วย CSS**

```html
<style>
  code {
    font-family: 'Courier New', Courier, monospace;
    background-color: #f4f4f4;
    border: 1px solid #ddd;
    border-radius: 3px;
    padding: 2px 4px;
    font-size: 0.9em;
    color: #d73a49;
  }

  /* สำหรับโค้ด JavaScript */
  code.javascript {
    background-color: #fff3cd;
    border-color: #ffeaa7;
    color: #856404;
  }

  /* สำหรับโค้ด CSS */
  code.css {
    background-color: #cce5ff;
    border-color: #99ccff;
    color: #004085;
  }

  /* สำหรับโค้ด HTML */
  code.html {
    background-color: #ffe6e6;
    border-color: #ffcccc;
    color: #721c24;
  }
</style>

<p>JavaScript: <code class="javascript">document.querySelector()</code></p>
<p>CSS: <code class="css">margin: 10px auto;</code></p>
<p>HTML: <code class="html">&lt;div class="container"&gt;</code></p>
```

---

## 8. `<pre>` Tag - ข้อความที่จัดรูปแบบแล้ว

### 📝 **ความหมายและการใช้งาน**

- **ความหมาย**: ข้อความที่คงรูปแบบเดิม (preformatted)
- **การแสดงผล**: รักษาช่องว่าง, บรรทัดใหม่, ใช้ฟอนต์ monospace
- **ใช้สำหรับ**: โค้ดหลายบรรทัด, ASCII art, ข้อความที่มีการจัดวาง

#### **ตัวอย่างการใช้งาน**

```html
<!-- โค้ดหลายบรรทัด -->
<pre>
<code>
function greeting(name) {
    if (name) {
        console.log("Hello, " + name + "!");
    } else {
        console.log("Hello, World!");
    }
}

greeting("JavaScript");
</code>
</pre>

<!-- โครงสร้างไฟล์ -->
<pre>
project/
├── src/
│   ├── components/
│   │   ├── Header.js
│   │   └── Footer.js
│   ├── pages/
│   │   └── Home.js
│   └── App.js
├── public/
│   └── index.html
└── package.json
</pre>

<!-- ตารางข้อมูล -->
<pre>
Name        Age    City
John        25     Bangkok
Jane        30     Chiang Mai
Bob         35     Phuket
</pre>

<!-- ASCII Art -->
<pre>
    ░░░░░░░░░░░░░░░░░
    ░░░██░░░░██░░░░░
    ░░██▒▒██▒▒██░░░
    ░░██▒▒▒▒▒▒██░░░
    ░░░██▒▒▒▒██░░░░
    ░░░░████████░░░░
    ░░░░░░░░░░░░░░░░
</pre>

<!-- Output ตัวอย่าง -->
<pre>
$ npm start
> react-app@1.0.0 start
> react-scripts start

Compiled successfully!

Local:            http://localhost:3000
On Your Network:  http://192.168.1.100:3000
</pre>
```

#### **การใช้งานร่วมกับ `<code>`**

```html
<!-- แนะนำให้ใช้ร่วมกัน -->
<pre><code class="language-javascript">
const users = [
    { id: 1, name: 'John', email: 'john@example.com' },
    { id: 2, name: 'Jane', email: 'jane@example.com' }
];

const userNames = users.map(user => user.name);
console.log(userNames); // ['John', 'Jane']
</code></pre>

<!-- CSS styling -->
<style>
  pre {
    background-color: #f8f9fa;
    border: 1px solid #e9ecef;
    border-radius: 5px;
    padding: 15px;
    overflow-x: auto;
    font-family: 'Courier New', monospace;
    font-size: 14px;
    line-height: 1.5;
  }

  pre code {
    background: none;
    border: none;
    padding: 0;
    color: inherit;
  }
</style>
```

---

## 9. `<blockquote>` Tag - การอ้างอิงข้อความยาว

### 📝 **ความหมายและการใช้งาน**

- **ความหมาย**: ข้อความที่อ้างมาจากแหล่งอื่น (บล็อกข้อความ)
- **การแสดงผล**: เยื้องจากขอบซ้าย มีระยะห่างบนล่าง
- **ใช้สำหรับ**: คำพูด, ข้อความอ้างอิง, เนื้อหาจากแหล่งอื่น

#### **ตัวอย่างการใช้งาน**

```html
<!-- คำพูดที่มีชื่อเสียง -->
<blockquote>
  <p>
    "The only way to do great work is to love what you do. If you haven't found
    it yet, keep looking. Don't settle."
  </p>
  <cite>— Steve Jobs</cite>
</blockquote>

<!-- การอ้างอิงจากบทความ -->
<blockquote cite="https://example.com/article">
  <p>
    การพัฒนาเว็บไซต์ในยุคปัจจุบันต้องให้ความสำคัญกับ User Experience
    มากกว่าที่เคย เพราะผู้ใช้มีความคาดหวังสูงขึ้นเรื่อยๆ
  </p>
  <footer>— จาก <cite>Web Development Trends 2024</cite></footer>
</blockquote>

<!-- ข้อความจากลูกค้า (Testimonial) -->
<blockquote>
  <p>
    "บริการของ ABC Company ยอดเยี่ยมมาก ทีมงานใส่ใจในรายละเอียด
    และส่งมอบงานตรงเวลาเสมอ แนะนำให้เพื่อนๆ ใช้บริการแน่นอน"
  </p>
  <cite>— คุณสมชาย, CEO ของ XYZ Corp</cite>
</blockquote>

<!-- การอ้างอิงหลายย่อหน้า -->
<blockquote>
  <p>
    HTML5 นำเสนอคุณสมบัติใหม่มากมายที่ช่วยให้นักพัฒนา
    สามารถสร้างเว็บแอปพลิเคชันที่ทันสมัยได้ง่ายขึ้น
  </p>
  <p>
    Semantic elements เช่น header, nav, main, footer
    ช่วยให้โครงสร้างหน้าเว็บมีความหมายชัดเจนขึ้น
  </p>
  <cite>— MDN Web Docs</cite>
</blockquote>
```

#### **การจัดรูปแบบด้วย CSS**

```html
<style>
  blockquote {
    margin: 20px 0;
    padding: 20px;
    border-left: 4px solid #0066cc;
    background-color: #f8f9fa;
    font-style: italic;
    position: relative;
  }

  blockquote p {
    margin: 0 0 10px 0;
    font-size: 1.1em;
    line-height: 1.6;
  }

  blockquote cite {
    display: block;
    text-align: right;
    font-style: normal;
    font-weight: bold;
    color: #666;
    margin-top: 10px;
  }

  /* Quote marks */
  blockquote::before {
    content: '"';
    font-size: 4em;
    color: #0066cc;
    position: absolute;
    left: 10px;
    top: -10px;
    line-height: 1;
  }

  /* สำหรับ testimonial */
  blockquote.testimonial {
    border-left-color: #28a745;
    background-color: #f8fff9;
  }

  blockquote.testimonial::before {
    color: #28a745;
  }
</style>

<blockquote class="testimonial">
  <p>ผลิตภัณฑ์นี้เปลี่ยนวิธีการทำงานของเราไปโดยสิ้นเชิง</p>
  <cite>— ลูกค้าพิเศษ</cite>
</blockquote>
```

---

## 10. `<q>` Tag - การอ้างอิงข้อความสั้น

### 📝 **ความหมายและการใช้งาน**

- **ความหมาย**: ข้อความอ้างอิงสั้นๆ ภายในย่อหน้า
- **การแสดงผล**: ล้อมด้วยเครื่องหมายคำพูด (" ")
- **ความแตกต่างจาก blockquote**: ใช้ inline, สำหรับข้อความสั้น

#### **ตัวอย่างการใช้งาน**

```html
<!-- การอ้างคำพูดสั้นๆ -->
<p>
  Steve Jobs เคยกล่าวว่า
  <q>Innovation distinguishes between a leader and a follower</q>
  ซึ่งเป็นแนวคิดที่มีอิทธิพลต่อวงการเทคโนโลยี
</p>

<!-- การใช้ในบทสนทนา -->
<p>
  เมื่อฉันถามเขาว่าชอบการเขียนโปรแกรมไหม เขาตอบว่า
  <q>ชอบมาก เพราะได้สร้างสิ่งใหม่ๆ ตลอดเวลา</q>
</p>

<!-- การอ้างจากบทความ -->
<p>
  ตามรายงานระบุว่า <q>ปัญญาประดิษฐ์จะเป็นเทคโนโลยีหลักใน 10 ปีข้างหน้า</q>
  ซึ่งสะท้อนถึงความสำคัญของการเตรียมตัว
</p>

<!-- การอ้างคำย่อ -->
<p>
  เขาเตือนว่า <q>อย่าลืมสำรองข้อมูล</q>
  ก่อนจะอัปเดตระบบ
</p>

<!-- การใช้ cite attribute -->
<p>
  นักวิจัยกล่าวว่า
  <q cite="https://research-journal.com/ai-study">
    AI จะช่วยเพิ่มประสิทธิภาพการทำงานได้ถึง 40%
  </q>
</p>
```

#### **การซ้อน quotes**

```html
<!-- Quote ภายใน quote -->
<p>
  ผู้จัดการบอกกับทีมว่า
  <q>ลูกค้าเพิ่งโทรมาบอกว่า <q>โปรเจกต์นี้ยอดเยี่ยมมาก</q> แสดงว่าเราทำได้ดี</q>
</p>

<!-- การใช้กับภาษาต่างประเทศ -->
<p>
  คำว่า <q lang="en">Hello World</q>
  เป็นประโยคแรกที่โปรแกรมเมอร์ส่วนใหญ่เขียน
</p>
```

#### **การปรับแต่งด้วย CSS**

```html
<style>
  q {
    font-style: italic;
    color: #444;
  }

  /* เปลี่ยนเครื่องหมายคำพูด */
  q::before {
    content: '"';
  }

  q::after {
    content: '"';
  }

  /* สำหรับภาษาไทย */
  q[lang='th']::before {
    content: '"';
  }

  q[lang='th']::after {
    content: '"';
  }

  /* สำหรับ nested quotes */
  q q::before {
    content: '' ';
}

q q::after {
  content: ' '';
  }

  /* สไตล์พิเศษ */
  q.highlight {
    background-color: #fff3cd;
    padding: 2px 4px;
    border-radius: 3px;
  }
</style>

<p>เขากล่าวว่า <q class="highlight">นี่คือโอกาสทองของเรา</q></p>
```

---

## การเปรียบเทียบและการเลือกใช้

### 📊 **ตารางเปรียบเทียบ**

| Element        | ประเภท | ความหมาย         | ใช้สำหรับ             | การแสดงผล       |
| -------------- | ------ | ---------------- | --------------------- | --------------- |
| `<span>`       | Inline | ไม่มี            | จัดกลุ่มเพื่อ styling | ไม่เปลี่ยน      |
| `<mark>`       | Inline | เน้นในบริบท      | ผลค้นหา, เน้นข้อความ  | พื้นเหลือง      |
| `<small>`      | Inline | ข้อมูลรอง        | หมายเหตุ, disclaimer  | ตัวเล็ก         |
| `<sup>`        | Inline | ตัวยก            | เลขยก, หมายเหตุ       | ตัวเล็กยกขึ้น   |
| `<sub>`        | Inline | ตัวห้อย          | สูตรเคมี, ดัชนี       | ตัวเล็กห้อยลง   |
| `<abbr>`       | Inline | คำย่อ            | ตัวย่อมีความหมาย      | เส้นประ         |
| `<cite>`       | Inline | ชื่อผลงาน        | หนังสือ, ภาพยนตร์     | ตัวเอียง        |
| `<code>`       | Inline | โค้ดสั้น         | คำสั่ง, ฟังก์ชัน      | ฟอนต์ mono      |
| `<pre>`        | Block  | ข้อความจัดรูปแบบ | โค้ดยาว, ASCII        | คงรูปแบบ        |
| `<blockquote>` | Block  | อ้างอิงยาว       | คำพูด, บทความ         | เยื้อง          |
| `<q>`          | Inline | อ้างอิงสั้น      | คำพูดในย่อหน้า        | เครื่องหมาย " " |

### 🎯 **แนวทางการเลือกใช้**

#### **สำหรับการเน้นข้อความ**

```html
<!-- ข้อมูลสำคัญ -->
<strong>สำคัญมาก</strong>

<!-- เน้นเสียง -->
<em>เน้นเสียง</em>

<!-- เน้นในบริบท -->
<mark>ผลการค้นหา</mark>

<!-- จัดกลุ่มเพื่อ styling -->
<span class="highlight">ข้อความพิเศษ</span>
```

#### **สำหรับข้อมูลทางเทคนิค**

```html
<!-- คำย่อ -->
<abbr title="HyperText Markup Language">HTML</abbr>

<!-- โค้ดสั้น -->
<code>console.log()</code>

<!-- โค้ดยาว -->
<pre><code>
function example() {
    return "Hello World";
}
</code></pre>
```

#### **สำหรับการอ้างอิง**

```html
<!-- ชื่อผลงาน -->
<cite>The Art of Programming</cite>

<!-- คำพูดสั้น -->
<q>Life is short</q>

<!-- คำพูดยาว -->
<blockquote>
  <p>การเรียนรู้ไม่มีวันสิ้นสุด...</p>
  <cite>— นักปรัชญา</cite>
</blockquote>
```

---

## Best Practices และ Accessibility

### ✅ **สิ่งที่ควรทำ**

1. **ใช้ semantic elements ตามความหมาย**

   ```html
   <!-- ✅ ถูก -->
   <abbr title="World Health Organization">WHO</abbr>

   <!-- ❌ ผิด -->
   <span title="World Health Organization">WHO</span>
   ```

2. **เพิ่ม title attribute สำหรับ abbr**

   ```html
   <abbr title="Application Programming Interface">API</abbr>
   ```

3. **ใช้ cite attribute สำหรับ blockquote และ q**
   ```html
   <blockquote cite="https://source-url.com">
     <p>ข้อความอ้างอิง</p>
   </blockquote>
   ```

### ❌ **สิ่งที่ไม่ควรทำ**

1. **อย่าใช้ elements เพื่อการจัดรูปแบบเท่านั้น**

   ```html
   <!-- ❌ ผิด -->
   <small>หัวข้อใหญ่</small>

   <!-- ✅ ถูก -->
   <h1 style="font-size: 12px;">หัวข้อใหญ่</h1>
   ```

2. **อย่าใช้ pre สำหรับการจัดวางทั่วไป**

   ```html
   <!-- ❌ ผิด -->
   <pre>ข้อความปกติที่ต้องการเยื้อง</pre>

   <!-- ✅ ถูก -->
   <p style="margin-left: 20px;">ข้อความปกติที่ต้องการเยื้อง</p>
   ```

### 🔍 **การตรวจสอบและ Validation**

```html
<!-- ใช้ HTML validator -->
<!-- https://validator.w3.org/ -->

<!-- ตรวจสอบ accessibility -->
<!-- ใช้ screen reader ทดสอบ -->

<!-- ตรวจสอบ semantic correctness -->
<!-- ใช้ browser developer tools -->
```

การเลือกใช้ elements เหล่านี้อย่างถูกต้องจะช่วยให้เว็บไซต์มีความหมาย สามารถเข้าถึงได้ และเป็นมิตรต่อเครื่องมือค้นหา
