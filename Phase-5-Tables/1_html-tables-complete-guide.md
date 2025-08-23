# HTML Tables - คู่มือการใช้ตารางอย่างสมบูรณ์

## ภาพรวม

HTML Tables เป็นเครื่องมือสำหรับแสดงข้อมูลที่มีโครงสร้างเป็นแถวและคอลัมน์ **ใช้เฉพาะกับข้อมูลตารางจริงเท่านั้น** ไม่ควรใช้สำหรับ layout หน้าเว็บ

### เมื่อไหร่ควรใช้ Tables

✅ **ควรใช้**:

- ข้อมูลทางสถิติ
- รายการราคา
- ตารางเปรียบเทียบ
- ข้อมูลการเงิน
- ตารางเวลา
- ผลการแข่งขัน

❌ **ไม่ควรใช้**:

- Layout หน้าเว็บ
- การจัดวาง element
- เพื่อให้เนื้อหาเรียงกัน
- การจัดรูปแบบที่ไม่ใช่ข้อมูลตาราง

---

## 1. โครงสร้างพื้นฐานของ Table

### 1.1 Elements หลัก

```html
<!-- โครงสร้างพื้นฐาน -->
<table>
  <caption>
    คำอธิบายตาราง
  </caption>

  <thead>
    <tr>
      <th>หัวคอลัมน์ 1</th>
      <th>หัวคอลัมน์ 2</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>ข้อมูล 1</td>
      <td>ข้อมูล 2</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <td>สรุป 1</td>
      <td>สรุป 2</td>
    </tr>
  </tfoot>
</table>
```

### 1.2 รายละเอียด Elements

| Element     | หน้าที่                  | จำเป็น   |
| ----------- | ------------------------ | -------- |
| `<table>`   | Container หลักของตาราง   | ✅       |
| `<caption>` | คำอธิบายตาราง            | แนะนำ    |
| `<thead>`   | ส่วนหัวตาราง             | แนะนำ    |
| `<tbody>`   | เนื้อหาหลักตาราง         | แนะนำ    |
| `<tfoot>`   | ส่วนท้ายตาราง            | ทางเลือก |
| `<tr>`      | แถว (Table Row)          | ✅       |
| `<th>`      | หัวเซลล์ (Table Header)  | แนะนำ    |
| `<td>`      | เซลล์ข้อมูล (Table Data) | ✅       |

---

## 2. `<table>` Element

### 2.1 การใช้งานพื้นฐาน

```html
<!-- Table พื้นฐาน -->
<table>
  <tr>
    <td>ชื่อ</td>
    <td>อายุ</td>
  </tr>
  <tr>
    <td>สมชาย</td>
    <td>25</td>
  </tr>
</table>
```

### 2.2 Attributes สำคัญ

```html
<!-- Table พร้อม attributes -->
<table id="employee-table" class="data-table" role="table">
  <tr>
    <td>ข้อมูลพนักงาน</td>
  </tr>
</table>
```

**Attributes ที่ไม่แนะนำ** (ใช้ CSS แทน):

- `border`
- `cellpadding`
- `cellspacing`
- `width`
- `bgcolor`

---

## 3. `<caption>` Element - คำอธิบายตาราง

### 3.1 การใช้งาน `<caption>`

**จุดประสงค์**:

- อธิบายเนื้อหาของตาราง
- ช่วย Screen Readers เข้าใจบริบท
- ปรับปรุง SEO
- ให้ผู้ใช้เข้าใจตารางได้รวดเร็ว

```html
<!-- Caption พื้นฐาน -->
<table>
  <caption>
    รายชื่อพนักงานและเงินเดือน ประจำเดือนมกราคม 2024
  </caption>

  <thead>
    <tr>
      <th>ชื่อ-นามสกุล</th>
      <th>ตำแหน่ง</th>
      <th>เงินเดือน (บาท)</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>นาย ก ใจดี</td>
      <td>โปรแกรมเมอร์</td>
      <td>35,000</td>
    </tr>
    <tr>
      <td>นางสาว ข สวยงาม</td>
      <td>นักออกแบบ</td>
      <td>30,000</td>
    </tr>
  </tbody>
</table>
```

### 3.2 การใช้ `<caption>` แบบซับซ้อน

```html
<!-- Caption พร้อมรายละเอียด -->
<table>
  <caption>
    <strong>ยอดขายสินค้าไตรมาส 1 ปี 2024</strong>
    <br />
    <small>หน่วย: ล้านบาท | อัปเดตล่าสุด: 31 มีนาคม 2024</small>
  </caption>

  <thead>
    <tr>
      <th>สินค้า</th>
      <th>มกราคม</th>
      <th>กุมภาพันธ์</th>
      <th>มีนาคม</th>
      <th>รวม</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>โทรศัพท์</td>
      <td>15.2</td>
      <td>18.5</td>
      <td>22.1</td>
      <td>55.8</td>
    </tr>
    <tr>
      <td>แท็บเล็ต</td>
      <td>8.3</td>
      <td>9.7</td>
      <td>11.2</td>
      <td>29.2</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <th>รวมทั้งหมด</th>
      <td>23.5</td>
      <td>28.2</td>
      <td>33.3</td>
      <td>85.0</td>
    </tr>
  </tfoot>
</table>
```

### 3.3 การจัดรูปแบบ `<caption>`

```html
<!-- Caption ที่สามารถ style ได้ -->
<table>
  <caption class="table-title">
    <h3>ผลการเรียนนักเรียนชั้น ม.6/1</h3>
    <p class="table-description">ภาคเรียนที่ 1 ปีการศึกษา 2567</p>
  </caption>

  <!-- table content -->
</table>
```

```css
/* CSS สำหรับ caption */
.table-title {
  caption-side: top; /* หรือ bottom */
  text-align: left;
  margin-bottom: 1rem;
  font-weight: bold;
}

.table-title h3 {
  margin: 0 0 0.5rem 0;
  color: #333;
}

.table-description {
  margin: 0;
  font-size: 0.9em;
  color: #666;
}
```

---

## 4. โครงสร้างตารางแบบสมบูรณ์

### 4.1 `<thead>` - ส่วนหัวตาราง

```html
<table>
  <caption>
    ข้อมูลการขายรายเดือน
  </caption>

  <thead>
    <tr>
      <th scope="col">เดือน</th>
      <th scope="col">ยอดขาย</th>
      <th scope="col">เป้าหมาย</th>
      <th scope="col">ร้อยละความสำเร็จ</th>
    </tr>
  </thead>

  <!-- tbody และ tfoot -->
</table>
```

### 4.2 `<tbody>` - เนื้อหาหลัก

```html
<tbody>
  <tr>
    <th scope="row">มกราคม</th>
    <td>1,250,000</td>
    <td>1,200,000</td>
    <td>104.17%</td>
  </tr>
  <tr>
    <th scope="row">กุมภาพันธ์</th>
    <td>1,180,000</td>
    <td>1,200,000</td>
    <td>98.33%</td>
  </tr>
  <tr>
    <th scope="row">มีนาคม</th>
    <td>1,420,000</td>
    <td>1,300,000</td>
    <td>109.23%</td>
  </tr>
</tbody>
```

### 4.3 `<tfoot>` - ส่วนสรุป

```html
<tfoot>
  <tr>
    <th scope="row">รวมทั้งหมด</th>
    <td>3,850,000</td>
    <td>3,700,000</td>
    <td>104.05%</td>
  </tr>
</tfoot>
```

---

## 5. `<th>` และ `<td>` Elements

### 5.1 `<th>` - Table Headers

```html
<!-- th พร้อม scope attributes -->
<table>
  <caption>
    ตารางคะแนนการแข่งขัน
  </caption>

  <thead>
    <tr>
      <th scope="col">อันดับ</th>
      <th scope="col">ทีม</th>
      <th scope="col">แข่ง</th>
      <th scope="col">ชนะ</th>
      <th scope="col">เสมอ</th>
      <th scope="col">แพ้</th>
      <th scope="col">คะแนน</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <th scope="row">1</th>
      <td>ทีม A</td>
      <td>10</td>
      <td>8</td>
      <td>1</td>
      <td>1</td>
      <td>25</td>
    </tr>
    <tr>
      <th scope="row">2</th>
      <td>ทีม B</td>
      <td>10</td>
      <td>7</td>
      <td>2</td>
      <td>1</td>
      <td>23</td>
    </tr>
  </tbody>
</table>
```

### 5.2 Scope Attributes

| Scope      | ใช้เมื่อ     | ตัวอย่าง                    |
| ---------- | ------------ | --------------------------- |
| `col`      | หัวคอลัมน์   | `<th scope="col">ชื่อ</th>` |
| `row`      | หัวแถว       | `<th scope="row">2024</th>` |
| `colgroup` | กลุ่มคอลัมน์ | หลายคอลัมน์ที่เกี่ยวข้อง    |
| `rowgroup` | กลุ่มแถว     | หลายแถวที่เกี่ยวข้อง        |

### 5.3 `<td>` - Table Data

```html
<!-- td พร้อม attributes -->
<table>
  <tr>
    <td headers="name">สมชาย ใจดี</td>
    <td headers="age">25</td>
    <td headers="salary">35,000</td>
  </tr>
</table>
```

---

## 6. Colspan และ Rowspan

### 6.1 Colspan - รวมคอลัมน์

```html
<!-- ตัวอย่าง colspan -->
<table>
  <caption>
    รายงานยอดขายรายไตรมาส
  </caption>

  <thead>
    <tr>
      <th rowspan="2">สินค้า</th>
      <th colspan="3">ไตรมาส 1</th>
      <th colspan="3">ไตรมาส 2</th>
    </tr>
    <tr>
      <th>ม.ค.</th>
      <th>ก.พ.</th>
      <th>มี.ค.</th>
      <th>เม.ย.</th>
      <th>พ.ค.</th>
      <th>มิ.ย.</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <th scope="row">โทรศัพท์</th>
      <td>100</td>
      <td>120</td>
      <td>110</td>
      <td>130</td>
      <td>140</td>
      <td>125</td>
    </tr>
    <tr>
      <th scope="row">แท็บเล็ต</th>
      <td>50</td>
      <td>55</td>
      <td>60</td>
      <td>65</td>
      <td>70</td>
      <td>68</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <th scope="row">รวม</th>
      <td>150</td>
      <td>175</td>
      <td>170</td>
      <td>195</td>
      <td>210</td>
      <td>193</td>
    </tr>
  </tfoot>
</table>
```

### 6.2 Rowspan - รวมแถว

```html
<!-- ตัวอย่าง rowspan -->
<table>
  <caption>
    ตารางเรียนรายวิชา
  </caption>

  <thead>
    <tr>
      <th>เวลา</th>
      <th>จันทร์</th>
      <th>อังคาร</th>
      <th>พุธ</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <th scope="row">08:00-09:00</th>
      <td>คณิตศาสตร์</td>
      <td rowspan="2">ฟิสิกส์<br />(ห้อง Lab)</td>
      <td>ภาษาไทย</td>
    </tr>
    <tr>
      <th scope="row">09:00-10:00</th>
      <td>ภาษาอังกฤษ</td>
      <!-- rowspan จากแถวบน -->
      <td>เคมี</td>
    </tr>
    <tr>
      <th scope="row">10:00-11:00</th>
      <td colspan="3" class="break">พักเบรก</td>
    </tr>
  </tbody>
</table>
```

---

## 7. การทำให้ Table เข้าถึงได้ (Accessibility)

### 7.1 ARIA Labels และ Descriptions

```html
<!-- Table พร้อม ARIA -->
<table
  role="table"
  aria-label="ข้อมูลยอดขายรายเดือน"
  aria-describedby="sales-desc"
>
  <caption id="sales-desc">
    ตารางแสดงยอดขายสินค้าแต่ละประเภทรายเดือน ในไตรมาสแรกของปี 2024
  </caption>

  <thead>
    <tr role="row">
      <th role="columnheader" scope="col">เดือน</th>
      <th role="columnheader" scope="col">โทรศัพท์</th>
      <th role="columnheader" scope="col">แท็บเล็ต</th>
    </tr>
  </thead>

  <tbody>
    <tr role="row">
      <th role="rowheader" scope="row">มกราคม</th>
      <td role="cell">1,200,000</td>
      <td role="cell">800,000</td>
    </tr>
  </tbody>
</table>
```

### 7.2 Headers Attribute

```html
<!-- เชื่อมโยง headers สำหรับตารางซับซ้อน -->
<table>
  <thead>
    <tr>
      <th id="product" scope="col">สินค้า</th>
      <th id="q1" scope="col">ไตรมาส 1</th>
      <th id="q2" scope="col">ไตรมาส 2</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <th id="phone" scope="row" headers="product">โทรศัพท์</th>
      <td headers="phone q1">150,000</td>
      <td headers="phone q2">180,000</td>
    </tr>
    <tr>
      <th id="tablet" scope="row" headers="product">แท็บเล็ต</th>
      <td headers="tablet q1">90,000</td>
      <td headers="tablet q2">110,000</td>
    </tr>
  </tbody>
</table>
```

### 7.3 Responsive Tables

```html
<!-- Table ที่ responsive -->
<div
  class="table-container"
  role="region"
  aria-label="ตารางข้อมูลยอดขาย"
  tabindex="0"
>
  <table class="responsive-table">
    <caption>
      ยอดขายรายเดือน (เลื่อนซ้าย-ขวาเพื่อดูข้อมูลเพิ่มเติม)
    </caption>

    <thead>
      <tr>
        <th scope="col">เดือน</th>
        <th scope="col">สินค้า A</th>
        <th scope="col">สินค้า B</th>
        <th scope="col">สินค้า C</th>
        <th scope="col">รวม</th>
      </tr>
    </thead>

    <tbody>
      <tr>
        <th scope="row">มกราคม</th>
        <td data-label="สินค้า A">100,000</td>
        <td data-label="สินค้า B">150,000</td>
        <td data-label="สินค้า C">120,000</td>
        <td data-label="รวม">370,000</td>
      </tr>
    </tbody>
  </table>
</div>
```

```css
/* CSS สำหรับ responsive table */
.table-container {
  overflow-x: auto;
  max-width: 100%;
}

.responsive-table {
  min-width: 600px;
  border-collapse: collapse;
  width: 100%;
}

/* Mobile responsive */
@media (max-width: 768px) {
  .responsive-table thead {
    display: none;
  }

  .responsive-table tbody tr {
    display: block;
    border: 1px solid #ddd;
    margin-bottom: 1rem;
  }

  .responsive-table tbody td {
    display: block;
    padding: 0.5rem;
    border: none;
    border-bottom: 1px solid #eee;
  }

  .responsive-table tbody td:before {
    content: attr(data-label) ': ';
    font-weight: bold;
  }
}
```

---

## 8. ตัวอย่างตารางประเภทต่างๆ

### 8.1 ตารางข้อมูลพนักงาน

```html
<table class="employee-table">
  <caption>
    <h3>รายชื่อพนักงานแผนก IT</h3>
    <p>อัปเดตล่าสุด: 15 มกราคม 2024</p>
  </caption>

  <thead>
    <tr>
      <th scope="col">รหัส</th>
      <th scope="col">ชื่อ-นามสกุล</th>
      <th scope="col">ตำแหน่ง</th>
      <th scope="col">วันที่เริ่มงาน</th>
      <th scope="col">เงินเดือน</th>
      <th scope="col">สถานะ</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <th scope="row">IT001</th>
      <td>นายสมชาย ใจดี</td>
      <td>Senior Developer</td>
      <td>
        <time datetime="2020-03-15">15 มีนาคม 2020</time>
      </td>
      <td>45,000 บาท</td>
      <td><span class="status active">ปฏิบัติงาน</span></td>
    </tr>
    <tr>
      <th scope="row">IT002</th>
      <td>นางสาวสมหญิง สวยงาม</td>
      <td>UI/UX Designer</td>
      <td>
        <time datetime="2021-06-01">1 มิถุนายน 2021</time>
      </td>
      <td>38,000 บาท</td>
      <td><span class="status active">ปฏิบัติงาน</span></td>
    </tr>
    <tr>
      <th scope="row">IT003</th>
      <td>นายสมศักดิ์ ขยันเรียน</td>
      <td>System Admin</td>
      <td>
        <time datetime="2019-11-10">10 พฤศจิกายน 2019</time>
      </td>
      <td>42,000 บาท</td>
      <td><span class="status leave">ลาป่วย</span></td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <th scope="row" colspan="4">รวมค่าใช้จ่ายเงินเดือน</th>
      <td><strong>125,000 บาท</strong></td>
      <td>3 คน</td>
    </tr>
  </tfoot>
</table>
```

### 8.2 ตารางเปรียบเทียบแพ็กเกจ

```html
<table class="pricing-table">
  <caption>
    เปรียบเทียบแพ็กเกจบริการเว็บโฮสติ้ง
  </caption>

  <thead>
    <tr>
      <th scope="col">คุณสมบัติ</th>
      <th scope="col">Basic</th>
      <th scope="col">Pro</th>
      <th scope="col">Enterprise</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <th scope="row">พื้นที่จัดเก็บ</th>
      <td>10 GB</td>
      <td>50 GB</td>
      <td>500 GB</td>
    </tr>
    <tr>
      <th scope="row">Bandwidth</th>
      <td>100 GB/เดือน</td>
      <td>500 GB/เดือน</td>
      <td>ไม่จำกัด</td>
    </tr>
    <tr>
      <th scope="row">จำนวนโดเมน</th>
      <td>1</td>
      <td>5</td>
      <td>ไม่จำกัด</td>
    </tr>
    <tr>
      <th scope="row">SSL Certificate</th>
      <td>❌</td>
      <td>✅</td>
      <td>✅</td>
    </tr>
    <tr>
      <th scope="row">การสำรองข้อมูล</th>
      <td>รายสัปดาห์</td>
      <td>รายวัน</td>
      <td>แบบ Real-time</td>
    </tr>
    <tr>
      <th scope="row">การสนับสนุน</th>
      <td>อีเมล</td>
      <td>อีเมล + Chat</td>
      <td>24/7 Phone + Email + Chat</td>
    </tr>
    <tr class="price-row">
      <th scope="row">ราคา/เดือน</th>
      <td><strong>199 บาท</strong></td>
      <td><strong>499 บาท</strong></td>
      <td><strong>1,299 บาท</strong></td>
    </tr>
  </tbody>
</table>
```

### 8.3 ตารางรายงานการเงิน

```html
<table class="financial-table">
  <caption>
    <h3>รายงานกำไรขาดทุน</h3>
    <p>ประจำไตรมาสที่ 1 ปี 2024 (หน่วย: ล้านบาท)</p>
  </caption>

  <thead>
    <tr>
      <th scope="col">รายการ</th>
      <th scope="col">มกราคม</th>
      <th scope="col">กุมภาพันธ์</th>
      <th scope="col">มีนาคม</th>
      <th scope="col">รวม Q1</th>
      <th scope="col">% เปลี่ยนแปลง</th>
    </tr>
  </thead>

  <tbody>
    <tr class="revenue-section">
      <th scope="row">รายได้จากการขาย</th>
      <td>125.5</td>
      <td>132.8</td>
      <td>145.2</td>
      <td class="highlight">403.5</td>
      <td class="positive">+12.5%</td>
    </tr>
    <tr>
      <th scope="row">ต้นทุนขาย</th>
      <td>(75.3)</td>
      <td>(79.7)</td>
      <td>(87.1)</td>
      <td class="highlight">(242.1)</td>
      <td class="positive">+8.2%</td>
    </tr>
    <tr class="subtotal">
      <th scope="row">กำไรขั้นต้น</th>
      <td>50.2</td>
      <td>53.1</td>
      <td>58.1</td>
      <td class="highlight"><strong>161.4</strong></td>
      <td class="positive">+18.7%</td>
    </tr>
    <tr>
      <th scope="row">ค่าใช้จ่ายในการขาย</th>
      <td>(15.8)</td>
      <td>(16.2)</td>
      <td>(17.5)</td>
      <td class="highlight">(49.5)</td>
      <td class="negative">+11.2%</td>
    </tr>
    <tr>
      <th scope="row">ค่าใช้จ่ายการบริหาร</th>
      <td>(12.4)</td>
      <td>(12.8)</td>
      <td>(13.1)</td>
      <td class="highlight">(38.3)</td>
      <td class="negative">+5.5%</td>
    </tr>
    <tr class="total">
      <th scope="row">กำไรสุทธิ</th>
      <td><strong>22.0</strong></td>
      <td><strong>24.1</strong></td>
      <td><strong>27.5</strong></td>
      <td class="highlight"><strong>73.6</strong></td>
      <td class="positive"><strong>+25.8%</strong></td>
    </tr>
  </tbody>
</table>
```

---

## 9. การจัดรูปแบบด้วย CSS

### 9.1 CSS พื้นฐานสำหรับ Table

```css
/* Reset และ base styles */
table {
  border-collapse: collapse;
  width: 100%;
  margin: 1rem 0;
  font-family: Arial, sans-serif;
}

caption {
  caption-side: top;
  text-align: left;
  margin-bottom: 1rem;
  font-size: 1.2em;
  font-weight: bold;
  color: #333;
}

th,
td {
  padding: 0.75rem;
  text-align: left;
  border-bottom: 1px solid #ddd;
}

th {
  background-color: #f8f9fa;
  font-weight: 600;
  color: #495057;
}

/* Hover effects */
tbody tr:hover {
  background-color: #f5f5f5;
}

/* Zebra striping */
tbody tr:nth-child(even) {
  background-color: #f9f9f9;
}
```

### 9.2 Responsive Table Styles

```css
/* Responsive container */
.table-responsive {
  overflow-x: auto;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
  border-radius: 8px;
}

.table-responsive table {
  margin: 0;
  min-width: 600px;
}

/* Mobile styles */
@media (max-width: 768px) {
  .table-mobile-stack thead {
    display: none;
  }

  .table-mobile-stack tr {
    display: block;
    border: 1px solid #ccc;
    margin-bottom: 1rem;
    border-radius: 8px;
    padding: 1rem;
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .table-mobile-stack td {
    display: block;
    border: none;
    padding: 0.25rem 0;
    border-bottom: 1px solid #eee;
  }

  .table-mobile-stack td:last-child {
    border-bottom: none;
  }

  .table-mobile-stack td:before {
    content: attr(data-label) ': ';
    font-weight: bold;
    color: #666;
  }
}
```

### 9.3 Table Theme Styles

```css
/* Dark theme */
.table-dark {
  background-color: #2d3748;
  color: #e2e8f0;
}

.table-dark th {
  background-color: #4a5568;
  color: #f7fafc;
}

.table-dark tbody tr:hover {
  background-color: #4a5568;
}

/* Pricing table */
.pricing-table th[scope='col'] {
  text-align: center;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 1rem;
}

.pricing-table .price-row {
  background-color: #f8f9fa;
  font-size: 1.1em;
}

.pricing-table .price-row td {
  text-align: center;
  font-weight: bold;
  color: #28a745;
}

/* Financial table */
.financial-table .positive {
  color: #28a745;
}

.financial-table .negative {
  color: #dc3545;
}

.financial-table .highlight {
  background-color: #fff3cd;
  font-weight: bold;
}

.financial-table .subtotal,
.financial-table .total {
  border-top: 2px solid #333;
  font-weight: bold;
}
```

---

## 10. ข้อผิดพลาดที่พบบ่อย

### 10.1 ❌ ข้อผิดพลาดทั่วไป

```html
<!-- ❌ ผิด: ใช้ table สำหรับ layout -->
<table>
  <tr>
    <td>
      <nav>เมนู</nav>
    </td>
    <td>
      <main>เนื้อหา</main>
    </td>
    <td>
      <aside>Sidebar</aside>
    </td>
  </tr>
</table>

<!-- ❌ ผิด: ไม่มี caption หรือ th -->
<table>
  <tr>
    <td>ชื่อ</td>
    <td>อายุ</td>
  </tr>
  <tr>
    <td>สมชาย</td>
    <td>25</td>
  </tr>
</table>

<!-- ❌ ผิด: ไม่ใช้ scope -->
<table>
  <tr>
    <th>เดือน</th>
    <th>ยอดขาย</th>
  </tr>
  <tr>
    <th>มกราคม</th>
    <td>100,000</td>
  </tr>
</table>
```

### 10.2 ✅ การแก้ไข

```html
<!-- ✅ ถูก: ใช้ CSS Grid สำหรับ layout -->
<div class="layout-grid">
  <nav class="sidebar">เมนู</nav>
  <main class="content">เนื้อหา</main>
  <aside class="sidebar">Sidebar</aside>
</div>

<!-- ✅ ถูก: มี caption และ th -->
<table>
  <caption>
    รายชื่อพนักงาน
  </caption>
  <thead>
    <tr>
      <th scope="col">ชื่อ</th>
      <th scope="col">อายุ</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>สมชาย</td>
      <td>25</td>
    </tr>
  </tbody>
</table>

<!-- ✅ ถูก: ใช้ scope attributes -->
<table>
  <caption>
    ยอดขายรายเดือน
  </caption>
  <thead>
    <tr>
      <th scope="col">เดือน</th>
      <th scope="col">ยอดขาย</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">มกราคม</th>
      <td>100,000</td>
    </tr>
  </tbody>
</table>
```

---

## 11. Checklist การสร้าง Table

### ✅ รายการตรวจสอบ

- [ ] ใช้ `<table>` เฉพาะข้อมูลตารางจริง
- [ ] มี `<caption>` อธิบายเนื้อหาตาราง
- [ ] ใช้ `<thead>`, `<tbody>`, `<tfoot>` จัดโครงสร้าง
- [ ] ทุก `<th>` มี `scope` attribute
- [ ] ใช้ `<th>` สำหรับ headers ทั้งแถวและคอลัมน์
- [ ] `colspan` และ `rowspan` ถูกต้อง
- [ ] ผ่านการทดสอบ accessibility
- [ ] Responsive บนหน้าจอเล็ก
- [ ] มี ARIA labels เมื่อจำเป็น
- [ ] ไม่ใช้ deprecated attributes

### ❌ สิ่งที่ควรหลีกเลี่ยง

- [ ] ไม่ใช้ table สำหรับ layout
- [ ] ไม่ใช้ `border`, `cellpadding`, `cellspacing`
- [ ] ไม่ข้าม `<thead>`, `<tbody>` structures
- [ ] ไม่ละเลย `scope` attributes
- [ ] ไม่ใช้ `<td>` สำหรับ headers

---

## สรุป

### หลักการสำคัญ

1. **ใช้เฉพาะข้อมูลตาราง**: Tables สำหรับข้อมูลที่มีความสัมพันธ์แบบตาราง

2. **โครงสร้างที่ชัดเจน**: ใช้ `<caption>`, `<thead>`, `<tbody>`, `<tfoot>`

3. **Accessibility**: ใช้ `scope`, `headers`, ARIA attributes

4. **Responsive Design**: ทำให้ table ใช้งานได้บนหน้าจอเล็ก

### Elements สำคัญ

- **`<table>`**: Container หลัก
- **`<caption>`**: คำอธิบายตาราง (แนะนำให้ใช้เสมอ)
- **`<th>`**: Headers พร้อม scope attributes
- **`<td>`**: ข้อมูลในตาราง

การใช้ HTML Tables อย่างถูกต้องจะทำให้ข้อมูลเข้าใจง่าย เข้าถึงได้สำหรับทุกคน และปฏิบัติตามมาตรฐาน Web Standards
