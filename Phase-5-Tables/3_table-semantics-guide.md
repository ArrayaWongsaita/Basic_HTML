# ความหมายเชิงข้อมูลของตาราง และข้อผิดพลาดที่ต้องหลีกเลี่ยง

## 1. ความหมายเชิงข้อมูล vs การจัด Layout

### ✅ ใช้ตารางอย่างถูกต้อง (เพื่อแสดงข้อมูล)

```html
<!-- ตารางสำหรับแสดงข้อมูลที่มีความสัมพันธ์ -->
<table>
  <caption>
    ผลการเรียนนักเรียนชั้น ม.6/1
  </caption>
  <thead>
    <tr>
      <th scope="col">ชื่อ-นามสกุล</th>
      <th scope="col">คณิตศาสตร์</th>
      <th scope="col">ฟิสิกส์</th>
      <th scope="col">เคมี</th>
      <th scope="col">เกรดเฉลี่ย</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">นางสาวสมใจ ใจดี</th>
      <td>85</td>
      <td>78</td>
      <td>92</td>
      <td>A</td>
    </tr>
    <tr>
      <th scope="row">นายสมชาย รักเรียน</th>
      <td>90</td>
      <td>88</td>
      <td>85</td>
      <td>A</td>
    </tr>
  </tbody>
</table>
```

### ❌ ใช้ตารางผิดวัตถุประสงค์ (สำหรับจัด Layout)

```html
<!-- ไม่ควรทำ - ใช้ตารางจัด layout -->
<table>
  <tr>
    <td>
      <img src="logo.png" alt="โลโก้" />
    </td>
    <td>
      <h1>ชื่อเว็บไซต์</h1>
    </td>
  </tr>
  <tr>
    <td colspan="2">
      <nav>เมนูนำทาง</nav>
    </td>
  </tr>
</table>

<!-- ✅ ใช้ CSS Grid/Flexbox แทน -->
<header class="site-header">
  <img src="logo.png" alt="โลโก้" />
  <h1>ชื่อเว็บไซต์</h1>
</header>
<nav>เมนูนำทาง</nav>
```

## 2. ข้อผิดพลาดสำคัญที่ลด Accessibility

### 2.1 ข้าม `<th>` สำหรับ Header

#### ❌ ผิด - ไม่ใช้ `<th>`

```html
<table>
  <tr>
    <td><strong>ชื่อสินค้า</strong></td>
    <td><strong>ราคา</strong></td>
    <td><strong>จำนวน</strong></td>
  </tr>
  <tr>
    <td>แล็ปท็อป</td>
    <td>25,000</td>
    <td>5</td>
  </tr>
</table>
```

**ปัญหา:**

- Screen Reader ไม่สามารถแยกแยะ header จาก data cell
- ผู้ใช้ที่มีความบกพร่องทางการมองเห็นไม่เข้าใจโครงสร้างตาราง
- การนำทางด้วย keyboard ทำได้ยาก

#### ✅ ถูก - ใช้ `<th>` อย่างถูกต้อง

```html
<table>
  <thead>
    <tr>
      <th scope="col">ชื่อสินค้า</th>
      <th scope="col">ราคา</th>
      <th scope="col">จำนวน</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>แล็ปท็อป</td>
      <td>25,000</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
```

### 2.2 ไม่ใช้ `scope` Attribute

#### ❌ ผิด - ไม่ระบุ scope

```html
<table>
  <tr>
    <th>แผนก</th>
    <th>Q1</th>
    <th>Q2</th>
    <th>Q3</th>
    <th>Q4</th>
  </tr>
  <tr>
    <th>การตลาด</th>
    <td>500,000</td>
    <td>600,000</td>
    <td>550,000</td>
    <td>650,000</td>
  </tr>
  <tr>
    <th>ขาย</th>
    <td>800,000</td>
    <td>850,000</td>
    <td>900,000</td>
    <td>950,000</td>
  </tr>
</table>
```

**ปัญหา:**

- Screen Reader ไม่ทราบว่า header แต่ละตัวครอบคลุมข้อมูลส่วนไหน
- ความสัมพันธ์ระหว่าง header และ data ไม่ชัดเจน

#### ✅ ถูก - ใช้ scope อย่างถูกต้อง

```html
<table>
  <caption>
    รายงานยอดขายรายไตรมาส
  </caption>
  <thead>
    <tr>
      <th scope="col">แผนก</th>
      <th scope="col">Q1</th>
      <th scope="col">Q2</th>
      <th scope="col">Q3</th>
      <th scope="col">Q4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">การตลาด</th>
      <td>500,000</td>
      <td>600,000</td>
      <td>550,000</td>
      <td>650,000</td>
    </tr>
    <tr>
      <th scope="row">ขาย</th>
      <td>800,000</td>
      <td>850,000</td>
      <td>900,000</td>
      <td>950,000</td>
    </tr>
  </tbody>
</table>
```

### 2.3 ข้าม `<caption>` Element

#### ❌ ผิด - ไม่มี caption

```html
<table>
  <!-- ไม่มีการอธิบายว่าตารางนี้แสดงข้อมูลอะไร -->
  <thead>
    <tr>
      <th scope="col">วันที่</th>
      <th scope="col">อุณหภูมิ</th>
      <th scope="col">ความชื้น</th>
    </tr>
  </thead>
  <!-- ... -->
</table>
```

#### ✅ ถูก - มี caption ที่ชัดเจน

```html
<table>
  <caption>
    ข้อมูลสภาพอากาศประจำวันในเดือนมกราคม 2567
  </caption>
  <thead>
    <tr>
      <th scope="col">วันที่</th>
      <th scope="col">อุณหภูมิ (°C)</th>
      <th scope="col">ความชื้น (%)</th>
    </tr>
  </thead>
  <!-- ... -->
</table>
```

## 3. ตัวอย่างตารางซับซ้อนที่ถูกต้อง

### ตารางแบบหลายระดับ Header

```html
<table>
  <caption>
    ผลการสำรวจความพึงพอใจของลูกค้า แยกตามเพศและช่วงอายุ
  </caption>

  <colgroup>
    <col />
    <col span="2" style="background-color: #e8f4fd;" />
    <col span="2" style="background-color: #fff2cc;" />
  </colgroup>

  <thead>
    <tr>
      <th scope="col" rowspan="2">ช่วงอายุ</th>
      <th scope="colgroup" colspan="2">ชาย</th>
      <th scope="colgroup" colspan="2">หญิง</th>
    </tr>
    <tr>
      <th scope="col">พึงพอใจ</th>
      <th scope="col">ไม่พึงพอใจ</th>
      <th scope="col">พึงพอใจ</th>
      <th scope="col">ไม่พึงพอใจ</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <th scope="row">18-25 ปี</th>
      <td>85%</td>
      <td>15%</td>
      <td>90%</td>
      <td>10%</td>
    </tr>
    <tr>
      <th scope="row">26-35 ปี</th>
      <td>78%</td>
      <td>22%</td>
      <td>82%</td>
      <td>18%</td>
    </tr>
    <tr>
      <th scope="row">36-45 ปี</th>
      <td>75%</td>
      <td>25%</td>
      <td>88%</td>
      <td>12%</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <th scope="row">เฉลี่ยรวม</th>
      <td><strong>79%</strong></td>
      <td><strong>21%</strong></td>
      <td><strong>87%</strong></td>
      <td><strong>13%</strong></td>
    </tr>
  </tfoot>
</table>
```

### ใช้ `headers` attribute สำหรับตารางซับซ้อนมาก

```html
<table>
  <caption>
    ผลการศึกษาเปรียบเทียบยาต่าง ๆ
  </caption>

  <thead>
    <tr>
      <th id="medicine">ยา</th>
      <th id="dosage">ขนาดยา</th>
      <th id="week1">สัปดาห์ที่ 1</th>
      <th id="week2">สัปดาห์ที่ 2</th>
      <th id="week3">สัปดาห์ที่ 3</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <th id="aspirin" headers="medicine">Aspirin</th>
      <td headers="aspirin dosage">100mg</td>
      <td headers="aspirin week1">มีผล 70%</td>
      <td headers="aspirin week2">มีผล 80%</td>
      <td headers="aspirin week3">มีผล 85%</td>
    </tr>
    <tr>
      <th id="ibuprofen" headers="medicine">Ibuprofen</th>
      <td headers="ibuprofen dosage">200mg</td>
      <td headers="ibuprofen week1">มีผล 65%</td>
      <td headers="ibuprofen week2">มีผล 75%</td>
      <td headers="ibuprofen week3">มีผล 82%</td>
    </tr>
  </tbody>
</table>
```

## 4. การทดสอบ Accessibility

### 4.1 ใช้ Screen Reader

```html
<!-- เมื่อ Screen Reader อ่านตารางที่ถูกต้อง จะได้ยินแบบนี้: -->
<!-- "ตาราง ผลการเรียนนักเรียน มี 4 คอลัมน์ 3 แถว" -->
<!-- "แถวที่ 1 หัวข้อคอลัมน์: ชื่อ, คณิต, วิทยา, เกรด" -->
<!-- "แถวที่ 2 หัวข้อแถว: นายสมชาย คอลัมน์ คณิต: 85 คอลัมน์ วิทยา: 78" -->

<table>
  <caption>
    ผลการเรียนนักเรียน
  </caption>
  <thead>
    <tr>
      <th scope="col">ชื่อ</th>
      <th scope="col">คณิต</th>
      <th scope="col">วิทยา</th>
      <th scope="col">เกรด</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">นายสมชาย</th>
      <td>85</td>
      <td>78</td>
      <td>A</td>
    </tr>
  </tbody>
</table>
```

### 4.2 การนำทางด้วย Keyboard

```css
/* เพิ่ม focus styles เพื่อการนำทางที่ดี */
th:focus,
td:focus {
  outline: 2px solid #4a90e2;
  outline-offset: 2px;
  background-color: #f0f8ff;
}

/* ทำให้เซลล์สามารถโฟกัสได้ */
th,
td {
  position: relative;
}

th[tabindex],
td[tabindex] {
  cursor: pointer;
}
```

## 5. เครื่องมือตรวจสอบ

### 5.1 HTML Validator

```html
<!-- ใช้ W3C Markup Validator ตรวจสอบ -->
<!-- https://validator.w3.org/ -->

<!-- ข้อผิดพลาดที่พบบ่อย: -->
<!-- - Missing table headers -->
<!-- - Invalid nesting of table elements -->
<!-- - Missing required attributes -->
```

### 5.2 Accessibility Testing Tools

```javascript
// ใช้ axe-core สำหรับตรวจสอบ accessibility
// npm install @axe-core/webdriverjs

const { Builder } = require('selenium-webdriver');
const AxeBuilder = require('@axe-core/webdriverjs');

const driver = new Builder().forBrowser('chrome').build();

AxeBuilder(driver)
  .analyze()
  .then((results) => {
    console.log('Accessibility issues:', results.violations);
  });
```

## 6. Best Practices สรุป

### ✅ สิ่งที่ควรทำ

- ใช้ `<table>` เฉพาะข้อมูลที่มีความสัมพันธ์
- ใส่ `<caption>` อธิบายจุดประสงค์ของตาราง
- ใช้ `<th>` สำหรับ header เสมอ
- ระบุ `scope` attribute ใน `<th>`
- จัดกลุ่มด้วย `<thead>`, `<tbody>`, `<tfoot>`
- ใช้ `<colgroup>` และ `<col>` สำหรับจัดรูปแบบ

### ❌ สิ่งที่ไม่ควรทำ

- ใช้ตารางสำหรับจัด layout
- ข้าม `<th>` ใช้ `<td>` พร้อม CSS แทน
- ไม่ใส่ `scope` ใน header
- ผสาน `colspan`/`rowspan` โดยไม่จำเป็น
- ใส่ข้อมูลที่ไม่เกี่ยวข้องกันในตารางเดียว

### 📝 การตรวจสอบขั้นสุดท้าย

1. **ความหมาย**: ตารางแสดงข้อมูลที่มีความสัมพันธ์หรือไม่?
2. **โครงสร้าง**: มี `<caption>`, `<th>` พร้อม `scope` หรือไม่?
3. **การเข้าถึง**: Screen Reader อ่านเข้าใจได้หรือไม่?
4. **การนำทาง**: ใช้ keyboard นำทางได้หรือไม่?
5. **ความหมาย**: HTML มีความหมายเชิงข้อมูลชัดเจนหรือไม่?

---

**หมายเหตุ**: ตารางที่ดีคือตารางที่ทุกคนเข้าใจได้ ไม่ว่าจะมองเห็นหรือไม่ก็ตาม
