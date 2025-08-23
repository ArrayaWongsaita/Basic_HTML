# กลุ่มรูป: `<figure>` และ `<figcaption>`

## ภาพรวม

องค์ประกอบ `<figure>` และ `<figcaption>` เป็นส่วนสำคัญของ HTML5 ที่ใช้สำหรับจัดกลุ่มเนื้อหาที่เป็นภาพ แผนภูมิ โค้ด หรือสื่ออื่นๆ พร้อมกับคำอธิบาย

---

## 1. `<figure>` Element

### คำอธิบาย

- `<figure>` เป็น semantic element ที่ใช้จัดกลุ่มเนื้อหาที่อ้างอิงได้ (self-contained content)
- สามารถย้ายตำแหน่งได้โดยไม่กระทบต่อความหมายของเอกสารหลัก
- มักใช้กับภาพ แผนภูมิ โค้ด วิดีโอ หรือเนื้อหาอื่นที่ต้องการคำอธิบาย

### ไวยากรณ์พื้นฐาน

```html
<figure>
  <!-- เนื้อหาหลัก (รูปภาพ, โค้ด, แผนภูมิ ฯลฯ) -->
</figure>
```

### ตัวอย่างการใช้งานพื้นฐาน

```html
<figure>
  <img src="sunset.jpg" alt="พระอาทิตย์ตกดิน" />
</figure>
```

---

## 2. `<figcaption>` Element

### คำอธิบาย

- `<figcaption>` ใช้สำหรับเพิ่มคำอธิบายหรือคำบรรยายให้กับเนื้อหาใน `<figure>`
- ต้องเป็น child element แรกหรือสุดท้ายของ `<figure>` เท่านั้น
- ช่วยให้ screen readers และ search engines เข้าใจเนื้อหาได้ดีขึ้น

### ไวยากรณ์

```html
<figure>
  <figcaption>คำอธิบายรูปภาพ</figcaption>
  <!-- หรือ -->
  <!-- เนื้อหาหลัก -->
  <figcaption>คำอธิบายรูปภาพ</figcaption>
</figure>
```

---

## 3. ตัวอย่างการใช้งานแบบต่างๆ

### 3.1 รูปภาพพร้อมคำอธิบาย

```html
<figure>
  <img src="mountain.jpg" alt="ภูเขาในช่วงฤดูหนาว" />
  <figcaption>ภูเขาดอยอินทนนท์ในช่วงฤดูหนาว ถ่ายโดย: นายสมชาย ใจดี</figcaption>
</figure>
```

### 3.2 หลายภาพในกลุ่มเดียว

```html
<figure>
  <img src="before.jpg" alt="ก่อนปรับปรุง" />
  <img src="after.jpg" alt="หลังปรับปรุง" />
  <figcaption>
    การเปรียบเทียบพื้นที่สวนสาธารณะ ก่อนและหลังการปรับปรุง
  </figcaption>
</figure>
```

### 3.3 แผนภูมิและกราฟ

```html
<figure>
  <svg width="300" height="200">
    <rect x="10" y="10" width="50" height="100" fill="blue" />
    <rect x="70" y="30" width="50" height="80" fill="red" />
    <rect x="130" y="50" width="50" height="60" fill="green" />
  </svg>
  <figcaption>แผนภูมิแสดงยอดขายในแต่ละไตรมาส ปี 2024</figcaption>
</figure>
```

### 3.4 โค้ดโปรแกรม

```html
<figure>
  <pre><code>
function greet(name) {
  return `สวัสดี ${name}!`;
}

console.log(greet("สมชาย"));
  </code></pre>
  <figcaption>ตัวอย่างฟังก์ชัน JavaScript สำหรับการทักทาย</figcaption>
</figure>
```

### 3.5 วิดีโอพร้อมคำอธิบาย

```html
<figure>
  <video controls width="400">
    <source src="tutorial.mp4" type="video/mp4" />
    เบราว์เซอร์ไม่รองรับ video tag
  </video>
  <figcaption>วิดีโอสอนการใช้งาน HTML5 สำหรับผู้เริ่มต้น</figcaption>
</figure>
```

### 3.6 ข้อความยกมา (Blockquote)

```html
<figure>
  <blockquote>
    "การเรียนรู้ไม่เคยสิ้นสุด ทุกวันคือโอกาสใหม่ในการพัฒนาตนเอง"
  </blockquote>
  <figcaption>
    คำกล่าวของ <cite>อาจารย์สมศักดิ์ วิทยากร</cite>
    ในงานสัมมนาการศึกษา 2024
  </figcaption>
</figure>
```

---

## 4. การจัดรูปแบบด้วย CSS

### 4.1 สไตล์พื้นฐาน

```css
figure {
  margin: 20px 0;
  padding: 15px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background-color: #f9f9f9;
  text-align: center;
}

figcaption {
  margin-top: 10px;
  font-style: italic;
  color: #666;
  font-size: 0.9em;
  line-height: 1.4;
}
```

### 4.2 การจัดตำแหน่ง

```css
/* จัดให้อยู่กลาง */
figure {
  margin: 0 auto;
  max-width: 600px;
}

/* จัดให้ลอยทางซ้าย */
figure.float-left {
  float: left;
  margin: 0 20px 20px 0;
  max-width: 300px;
}

/* จัดให้ลอยทางขวา */
figure.float-right {
  float: right;
  margin: 0 0 20px 20px;
  max-width: 300px;
}
```

### 4.3 การตอบสนองต่ออุปกรณ์ (Responsive)

```css
figure {
  width: 100%;
  max-width: 100%;
}

figure img {
  width: 100%;
  height: auto;
  display: block;
}

@media (max-width: 768px) {
  figure {
    margin: 10px 0;
    padding: 10px;
  }

  figcaption {
    font-size: 0.8em;
  }
}
```

### 4.4 เอฟเฟกต์พิเศษ

```css
figure {
  position: relative;
  overflow: hidden;
  transition: transform 0.3s ease;
}

figure:hover {
  transform: scale(1.02);
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

figure img {
  transition: opacity 0.3s ease;
}

figure:hover img {
  opacity: 0.9;
}
```

---

## 5. การทำให้เป็น Accessible

### 5.1 การใช้ alt text และ figcaption

```html
<figure>
  <img src="chart.png" alt="แผนภูมิแสดงการเติบโตของยอดขายรายเดือน" />
  <figcaption>
    ยอดขายเพิ่มขึ้น 25% เมื่อเทียบกับปีที่แล้ว โดยเดือนธันวาคมมีการเติบโตสูงสุด
  </figcaption>
</figure>
```

### 5.2 การใช้ ARIA attributes

```html
<figure role="img" aria-labelledby="chart-caption">
  <canvas id="sales-chart" width="400" height="300"></canvas>
  <figcaption id="chart-caption">
    แผนภูมิวงกลมแสดงสัดส่วนการขายสินค้าตามหมวดหมู่
  </figcaption>
</figure>
```

### 5.3 การอธิบายข้อมูลในตาราง

```html
<figure>
  <table>
    <caption>
      ข้อมูลยอดขายรายไตรมาส
    </caption>
    <thead>
      <tr>
        <th>ไตรมาส</th>
        <th>ยอดขาย (ล้านบาท)</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Q1</td>
        <td>15.2</td>
      </tr>
      <tr>
        <td>Q2</td>
        <td>18.7</td>
      </tr>
    </tbody>
  </table>
  <figcaption>
    ตารางแสดงผลการดำเนินงานของบริษัทในครึ่งปีแรกของปี 2024
  </figcaption>
</figure>
```

---

## 6. ตัวอย่างการใช้งานขั้นสูง

### 6.1 แกลลอรี่รูปภาพ

```html
<section class="gallery">
  <h2>แกลลอรี่ภาพธรรมชาติ</h2>

  <figure>
    <img src="forest.jpg" alt="ป่าไผ่ในยามเช้า" />
    <figcaption>ป่าไผ่อันเงียบสงบในยามเช้า จังหวัดเชียงใหม่</figcaption>
  </figure>

  <figure>
    <img src="waterfall.jpg" alt="น้ำตกในฤดูฝน" />
    <figcaption>น้ำตกแห่งหนึ่งในอุทยานแห่งชาติ ช่วงฤดูฝน</figcaption>
  </figure>
</section>
```

### 6.2 รายงานข้อมูล

```html
<article>
  <h1>รายงานการวิเคราะห์ยอดขาย</h1>

  <figure>
    <img src="sales-trend.png" alt="กราฟเส้นแสดงแนวโน้มยอดขาย 12 เดือน" />
    <figcaption>
      <strong>รูปที่ 1:</strong> แนวโน้มยอดขายรายเดือน ตั้งแต่มกราคม - ธันวาคม
      2024
    </figcaption>
  </figure>

  <p>จากกราฟข้างต้นจะเห็นได้ว่า...</p>

  <figure>
    <table>
      <!-- ข้อมูลในตาราง -->
    </table>
    <figcaption>
      <strong>ตารางที่ 1:</strong> สรุปยอดขายแยกตามภูมิภาค
    </figcaption>
  </figure>
</article>
```

### 6.3 ตัวอย่างโค้ดพร้อมคำอธิบาย

```html
<figure class="code-example">
  <pre><code class="language-css">
.figure-responsive {
  width: 100%;
  max-width: 600px;
  margin: 0 auto;
}

.figure-responsive img {
  width: 100%;
  height: auto;
  border-radius: 8px;
}
  </code></pre>
  <figcaption>
    <strong>ตัวอย่างที่ 1:</strong> CSS สำหรับทำให้ figure เป็น responsive
  </figcaption>
</figure>
```

---

## 7. ข้อผิดพลาดที่พบบ่อย

### 7.1 การใช้ figcaption นอก figure

```html
<!-- ผิด -->
<img src="photo.jpg" alt="รูปภาพ" />
<figcaption>คำอธิบายรูปภาพ</figcaption>

<!-- ถูกต้อง -->
<figure>
  <img src="photo.jpg" alt="รูปภาพ" />
  <figcaption>คำอธิบายรูปภาพ</figcaption>
</figure>
```

### 7.2 การใส่ figcaption หลายตัวใน figure เดียว

```html
<!-- ผิด -->
<figure>
  <figcaption>คำอธิบายที่ 1</figcaption>
  <img src="photo.jpg" alt="รูปภาพ" />
  <figcaption>คำอธิบายที่ 2</figcaption>
</figure>

<!-- ถูกต้อง -->
<figure>
  <img src="photo.jpg" alt="รูปภาพ" />
  <figcaption>
    คำอธิบายรูปภาพ<br />
    ข้อมูลเพิ่มเติม
  </figcaption>
</figure>
```

### 7.3 การใช้ figure กับเนื้อหาที่ไม่เหมาะสม

```html
<!-- ไม่เหมาะสม - ใช้สำหรับเนื้อหาทั่วไป -->
<figure>
  <p>ข้อความทั่วไปในเอกสาร</p>
  <figcaption>ข้อความนี้</figcaption>
</figure>

<!-- เหมาะสม - ใช้กับเนื้อหาที่อ้างอิงได้ -->
<figure>
  <blockquote>"คำคมสำคัญที่อ้างอิงได้"</blockquote>
  <figcaption>ที่มา: หนังสือ XYZ</figcaption>
</figure>
```

---

## 8. เคล็ดลับและแนวทางปฏิบัติที่ดี

### 8.1 การเขียน figcaption ที่ดี

- ใช้ภาษาที่ชัดเจนและกระชับ
- ระบุที่มาของข้อมูลหากจำเป็น
- เพิ่มบริบทที่สำคัญ
- หลีกเลี่ยงการใช้คำซ้ำกับ alt text

### 8.2 การจัดการเนื้อหาแบบ responsive

```css
.figure-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
  margin: 20px 0;
}

@media (max-width: 768px) {
  .figure-container {
    grid-template-columns: 1fr;
  }
}
```

### 8.3 การใช้ semantic markup

```html
<article>
  <h1>บทความเกี่ยวกับ HTML5</h1>

  <figure>
    <img src="html5-logo.png" alt="โลโก้ HTML5" />
    <figcaption>โลโก้อย่างเป็นทางการของ HTML5 จาก <cite>W3C</cite></figcaption>
  </figure>

  <p>HTML5 เป็นมาตรฐานล่าสุด...</p>
</article>
```

---

## สรุป

องค์ประกอบ `<figure>` และ `<figcaption>` เป็นเครื่องมือที่ทรงพลังสำหรับ:

### ประโยชน์หลัก

- **จัดระเบียบเนื้อหา**: จัดกลุ่มสื่อพร้อมคำอธิบาย
- **ปรับปรุง SEO**: ช่วยให้ search engines เข้าใจเนื้อหาได้ดีขึ้น
- **เพิ่ม Accessibility**: ช่วยผู้ใช้ screen readers เข้าใจเนื้อหา
- **Semantic HTML**: ให้ความหมายที่ชัดเจนแก่โครงสร้างเอกสาร

### แนวทางการใช้งาน

- ใช้กับเนื้อหาที่สามารถอ้างอิงได้อย่างอิสระ
- เขียน figcaption ที่มีประโยชน์และชัดเจน
- จัดรูปแบบให้เหมาะสมกับการใช้งาน
- คำนึงถึง accessibility และ responsive design

การใช้งาน `<figure>` และ `<figcaption>` อย่างถูกต้องจะทำให้เว็บไซต์มีโครงสร้างที่ดี เข้าใจง่าย และเป็นมิตรกับผู้ใช้งานทุกกลุ่ม
