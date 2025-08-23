# การจัดคอลัมน์และ Attributes สำคัญของตาราง

## 1. การจัดกลุ่มคอลัมน์ (Column Grouping)

### `<colgroup>` และ `<col>`

- `<colgroup>`: จัดกลุ่มคอลัมน์ที่เกี่ยวข้องกัน
- `<col>`: กำหนดคุณสมบัติของคอลัมน์แต่ละคอลัมน์

```html
<table>
  <colgroup>
    <col style="background-color: #f0f0f0;" />
    <col span="2" style="background-color: #e0e0e0;" />
    <col style="background-color: #d0d0d0;" />
  </colgroup>
  <thead>
    <tr>
      <th>ชื่อ</th>
      <th>คะแนนกลางภาค</th>
      <th>คะแนนปลายภาค</th>
      <th>เกรด</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>สมชาย</td>
      <td>85</td>
      <td>88</td>
      <td>A</td>
    </tr>
  </tbody>
</table>
```

## 2. Attributes สำคัญ

### 2.1 `scope` Attribute

ใช้กำหนดขอบเขตของ header cell

**ค่าที่ใช้ได้:**

- `col`: header สำหรับคอลัมน์
- `row`: header สำหรับแถว
- `colgroup`: header สำหรับกลุ่มคอลัมน์
- `rowgroup`: header สำหรับกลุ่มแถว

```html
<table>
  <thead>
    <tr>
      <th scope="col">ชื่อวิชา</th>
      <th scope="col">หน่วยกิต</th>
      <th scope="col">เกรด</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">คณิตศาสตร์</th>
      <td>3</td>
      <td>A</td>
    </tr>
    <tr>
      <th scope="row">ฟิสิกส์</th>
      <td>3</td>
      <td>B+</td>
    </tr>
  </tbody>
</table>
```

### 2.2 `colspan` Attribute

ผสานเซลล์ในแนวนอน (ข้ามคอลัมน์)

```html
<table border="1">
  <tr>
    <th colspan="3">ข้อมูลนักเรียน</th>
  </tr>
  <tr>
    <th>ชื่อ</th>
    <th>อายุ</th>
    <th>ชั้น</th>
  </tr>
  <tr>
    <td>สมชาย</td>
    <td>16</td>
    <td>ม.4</td>
  </tr>
  <tr>
    <td colspan="2">ไม่มีข้อมูล</td>
    <td>ม.5</td>
  </tr>
</table>
```

### 2.3 `rowspan` Attribute

ผสานเซลล์ในแนวตั้ง (ข้ามแถว)

```html
<table border="1">
  <tr>
    <th rowspan="3">วิชา</th>
    <th>คณิตศาสตร์</th>
    <td>A</td>
  </tr>
  <tr>
    <th>ฟิสิกส์</th>
    <td>B+</td>
  </tr>
  <tr>
    <th>เคมี</th>
    <td>A-</td>
  </tr>
</table>
```

## 3. ตัวอย่างแบบละเอียด

### ตาราง Time Schedule แบบซับซ้อน

```html
<table border="1" style="border-collapse: collapse; width: 100%;">
  <colgroup>
    <col style="width: 10%; background-color: #f5f5f5;" />
    <col span="5" style="width: 18%; background-color: #fff;" />
  </colgroup>

  <thead>
    <tr>
      <th scope="col">เวลา</th>
      <th scope="col">จันทร์</th>
      <th scope="col">อังคาร</th>
      <th scope="col">พุธ</th>
      <th scope="col">พฤหัส</th>
      <th scope="col">ศุกร์</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <th scope="row">08:00-09:30</th>
      <td>คณิตศาสตร์</td>
      <td rowspan="2">ฟิสิกส์ขั้นสูง</td>
      <td>เคมี</td>
      <td>ชีววิทยา</td>
      <td>ภาษาอังกฤษ</td>
    </tr>
    <tr>
      <th scope="row">09:30-11:00</th>
      <td>ประวัติศาสตร์</td>
      <!-- rowspan จากแถวก่อน -->
      <td>คณิตศาสตร์</td>
      <td colspan="2">กิจกรรมพิเศษ</td>
    </tr>
    <tr>
      <th scope="row">11:00-12:30</th>
      <td colspan="5" style="text-align: center; background-color: #ffffcc;">
        พักกลางวัน
      </td>
    </tr>
    <tr>
      <th scope="row">13:30-15:00</th>
      <td>ภาษาไทย</td>
      <td>ศิลปะ</td>
      <td>พลศึกษา</td>
      <td>ดนตรี</td>
      <td>คอมพิวเตอร์</td>
    </tr>
  </tbody>
</table>
```

### ตารางรายงานยอดขาย (ใช้ scope แบบ colgroup/rowgroup)

```html
<table border="1" style="border-collapse: collapse;">
  <colgroup>
    <col />
    <col span="4" style="background-color: #e8f4fd;" />
    <col style="background-color: #fff2cc;" />
  </colgroup>

  <thead>
    <tr>
      <th scope="col">สาขา</th>
      <th scope="colgroup" colspan="4">ไตรมาส</th>
      <th scope="col">รวม</th>
    </tr>
    <tr>
      <th scope="col">ชื่อสาขา</th>
      <th scope="col">Q1</th>
      <th scope="col">Q2</th>
      <th scope="col">Q3</th>
      <th scope="col">Q4</th>
      <th scope="col">ยอดรวม</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <th scope="rowgroup" rowspan="3">ภาคเหนือ</th>
      <th scope="row">เชียงใหม่</th>
      <td>150,000</td>
      <td>180,000</td>
      <td>200,000</td>
      <td>220,000</td>
      <td><strong>750,000</strong></td>
    </tr>
    <tr>
      <th scope="row">เชียงราย</th>
      <td>120,000</td>
      <td>140,000</td>
      <td>160,000</td>
      <td>180,000</td>
      <td><strong>600,000</strong></td>
    </tr>
    <tr>
      <th scope="row">ลำปาง</th>
      <td>100,000</td>
      <td>110,000</td>
      <td>130,000</td>
      <td>150,000</td>
      <td><strong>490,000</strong></td>
    </tr>

    <tr style="background-color: #f0f0f0;">
      <th scope="row" colspan="2">รวมภาคเหนือ</th>
      <td><strong>370,000</strong></td>
      <td><strong>430,000</strong></td>
      <td><strong>490,000</strong></td>
      <td><strong>550,000</strong></td>
      <td><strong>1,840,000</strong></td>
    </tr>
  </tbody>
</table>
```

## 4. Best Practices และ Accessibility

### 4.1 การใช้ scope อย่างถูกต้อง

```html
<!-- ✅ ถูกต้อง -->
<th scope="col">หัวข้อคอลัมน์</th>
<th scope="row">หัวข้อแถว</th>

<!-- ❌ ผิด - ไม่ระบุ scope -->
<th>หัวข้อ</th>
```

### 4.2 การผสาน colspan/rowspan

```html
<!-- ✅ ถูกต้อง - มีโครงสร้างชัดเจน -->
<tr>
  <td colspan="2">ข้อมูลผสาน</td>
  <td>ข้อมูลปกติ</td>
</tr>

<!-- ❌ หลีกเลี่ยง - การผสานที่ซับซ้อนเกินไป -->
<tr>
  <td colspan="3" rowspan="2">ผสานซับซ้อน</td>
</tr>
```

### 4.3 การจัดรูปแบบด้วย CSS

```css
/* จัดสีสลับแถว */
tbody tr:nth-child(even) {
  background-color: #f9f9f9;
}

/* จัดรูปแบบ header */
th {
  background-color: #4caf50;
  color: white;
  padding: 12px;
  text-align: center;
}

/* จัดรูปแบบตาม colgroup */
col.highlight {
  background-color: #ffffcc;
}
```

## 5. เทคนิคขั้นสูง

### การใช้ headers attribute (สำหรับตารางซับซ้อน)

```html
<table>
  <tr>
    <th id="name">ชื่อ</th>
    <th id="math">คณิต</th>
    <th id="science">วิทย์</th>
  </tr>
  <tr>
    <td headers="name">สมชาย</td>
    <td headers="math">95</td>
    <td headers="science">88</td>
  </tr>
</table>
```

### การใช้ caption และ summary

```html
<table>
  <caption>
    ตารางแสดงผลการเรียนของนักเรียนชั้น ม.6
  </caption>
  <colgroup>
    <col style="width: 30%;" />
    <col style="width: 35%;" />
    <col style="width: 35%;" />
  </colgroup>
  <!-- เนื้อหาตาราง -->
</table>
```

---

**หมายเหตุ**: การใช้ attributes เหล่านี้อย่างถูกต้องจะช่วยให้ตารางมีความหมายชัดเจน และเข้าถึงได้สำหรับผู้ใช้ทุกกลุ่ม รวมถึงผู้ที่ใช้ Screen Reader
