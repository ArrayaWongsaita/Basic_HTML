# Lab Phase 5: HTML Tables - เฉลย
## 🎯 เฉลยการเติม HTML Table Tags

---

## 📊 **Lab 1: ตารางรายชื่อนักเรียนและคะแนน - เฉลย**

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>ผลการเรียนนักเรียน</title>
</head>
<body>
    <h1>ผลการเรียนภาคเรียนที่ 1/2567</h1>
    
    <table>
        <caption>
            ผลการเรียนนักเรียนชั้นมัธยมศึกษาปีที่ 6/1 ภาคเรียนที่ 1 ปีการศึกษา 2567
        </caption>
        
        <thead>
            <tr>
                <th scope="col">ชื่อ-นามสกุล</th>
                <th scope="col">คณิตศาสตร์</th>
                <th scope="col">ฟิสิกส์</th>
                <th scope="col">เคมี</th>
                <th scope="col">ชีววิทยา</th>
                <th scope="col">เกรดเฉลี่ย</th>
            </tr>
        </thead>
        
        <tbody>
            <tr>
                <th scope="row">นางสาวสมใจ ใจดี</th>
                <td>85</td>
                <td>78</td>
                <td>92</td>
                <td>88</td>
                <td>A</td>
            </tr>
            
            <tr>
                <th scope="row">นายสมชาย รักเรียน</th>
                <td>90</td>
                <td>88</td>
                <td>85</td>
                <td>92</td>
                <td>A</td>
            </tr>
            
            <tr>
                <th scope="row">นางสาวมานี ขยัน</th>
                <td>78</td>
                <td>82</td>
                <td>80</td>
                <td>85</td>
                <td>B+</td>
            </tr>
            
            <tr>
                <th scope="row">นายประสิทธิ์ มุ่งมั่น</th>
                <td>95</td>
                <td>90</td>
                <td>88</td>
                <td>93</td>
                <td>A</td>
            </tr>
        </tbody>
        
        <tfoot>
            <tr>
                <th scope="row">คะแนนเฉลี่ยของชั้น</th>
                <td>87.0</td>
                <td>84.5</td>
                <td>86.3</td>
                <td>89.5</td>
                <td>A</td>
            </tr>
        </tfoot>
    </table>
    
    <p><small>หมายเหตุ: A = 80-100, B+ = 75-79, B = 70-74</small></p>
</body>
</html>
```

### **คำอธิบาย:**
- `<table>`: Container หลักของตาราง
- `<caption>`: คำอธิบายตาราง ช่วย SEO และ accessibility
- `<thead>`: ส่วนหัวตาราง ประกอบด้วยชื่อคอลัมน์
- `<th scope="col">`: หัวคอลัมน์ ระบุ scope เป็น "col"
- `<tbody>`: เนื้อหาหลักของตาราง
- `<th scope="row">`: หัวแถว (ชื่อนักเรียน) ระบุ scope เป็น "row"
- `<td>`: เซลล์ข้อมูลทั่วไป
- `<tfoot>`: ส่วนท้ายตาราง สำหรับสรุปข้อมูล

**จุดสำคัญ:**
- ใช้ `scope="col"` สำหรับหัวคอลัมน์
- ใช้ `scope="row"` สำหรับหัวแถว
- ชื่อนักเรียนควรเป็น `<th>` ไม่ใช่ `<td>`

---

## 💰 **Lab 2: ตารางราคาสินค้า E-Commerce - เฉลย**

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>TechStore - รายการสินค้า</title>
</head>
<body>
    <h1>TechStore - รายการสินค้าและราคา</h1>
    
    <table>
        <caption>
            <strong>รายการสินค้าและราคาโปรโมชั่น</strong><br>
            <small>อัปเดต: 15 ตุลาคม 2567 | ราคารวม VAT 7% แล้ว</small>
        </caption>
        
        <thead>
            <tr>
                <th scope="col">รหัสสินค้า</th>
                <th scope="col">ชื่อสินค้า</th>
                <th scope="col">ราคาปกติ (บาท)</th>
                <th scope="col">ส่วนลด (%)</th>
                <th scope="col">ราคาพิเศษ (บาท)</th>
                <th scope="col">จำนวนคงเหลือ</th>
            </tr>
        </thead>
        
        <tbody>
            <tr>
                <th scope="row">MB-001</th>
                <td>MacBook Pro M3 14"</td>
                <td>62,900</td>
                <td>15</td>
                <td><mark>53,465</mark></td>
                <td>12</td>
            </tr>
            
            <tr>
                <th scope="row">IP-001</th>
                <td>iPhone 15 Pro Max 256GB</td>
                <td>47,900</td>
                <td>10</td>
                <td><mark>43,110</mark></td>
                <td>8</td>
            </tr>
            
            <tr>
                <th scope="row">IP-002</th>
                <td>iPad Pro 11" M2</td>
                <td>32,900</td>
                <td>12</td>
                <td><mark>28,952</mark></td>
                <td>15</td>
            </tr>
            
            <tr>
                <th scope="row">AW-001</th>
                <td>Apple Watch Series 9</td>
                <td>14,900</td>
                <td>8</td>
                <td><mark>13,708</mark></td>
                <td>20</td>
            </tr>
            
            <tr>
                <th scope="row">AP-001</th>
                <td>AirPods Pro (2nd Gen)</td>
                <td>8,990</td>
                <td>5</td>
                <td><mark>8,541</mark></td>
                <td>25</td>
            </tr>
        </tbody>
        
        <tfoot>
            <tr>
                <th scope="row" colspan="2">รวมมูลค่าสินค้าทั้งหมด</th>
                <td><strong>167,590</strong></td>
                <td>-</td>
                <td><strong>147,776</strong></td>
                <td><strong>80</strong></td>
            </tr>
        </tfoot>
    </table>
    
    <p><small>* โปรโมชั่นถึง 31 ตุลาคม 2567 | จัดส่งฟรีทั่วประเทศ</small></p>
</body>
</html>
```

### **คำอธิบาย:**
- `<caption>` พร้อม `<strong>` และ `<small>` สำหรับจัดรูปแบบ
- `<th scope="row">`: รหัสสินค้าเป็นหัวแถว
- `colspan="2"`: รวม 2 คอลัมน์สำหรับข้อความ "รวมมูลค่าสินค้าทั้งหมด"
- `<mark>`: ไฮไลต์ราคาพิเศษ
- `<tfoot>`: แสดงยอดรวมทั้งหมด

**จุดสำคัญ:**
- ใช้ `colspan` เพื่อรวมเซลล์ในส่วน tfoot
- รหัสสินค้าควรเป็น `<th scope="row">`
- ใช้ semantic elements (`<strong>`, `<mark>`) ในเซลล์ได้

---

## 📅 **Lab 3: ตารางเวลาเรียน - เฉลย**

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>ตารางเรียน ม.6/1</title>
</head>
<body>
    <h1>ตารางเรียนชั้นมัธยมศึกษาปีที่ 6/1</h1>
    
    <table>
        <caption>
            ตารางเรียนภาคเรียนที่ 1/2567 ชั้นมัธยมศึกษาปีที่ 6/1<br>
            <small>มีผลตั้งแต่ 1 พฤษภาคม 2567</small>
        </caption>
        
        <thead>
            <tr>
                <th scope="col">เวลา</th>
                <th scope="col">จันทร์</th>
                <th scope="col">อังคาร</th>
                <th scope="col">พุธ</th>
                <th scope="col">พฤหัสบดี</th>
                <th scope="col">ศุกร์</th>
            </tr>
        </thead>
        
        <tbody>
            <tr>
                <th scope="row">08:00-09:00</th>
                <td>คณิตศาสตร์<br><small>(ห้อง 601)</small></td>
                <td>ฟิสิกส์<br><small>(ห้องปฏิบัติการ)</small></td>
                <td>เคมี<br><small>(ห้องปฏิบัติการ)</small></td>
                <td>ชีววิทยา<br><small>(ห้อง 602)</small></td>
                <td>ภาษาไทย<br><small>(ห้อง 601)</small></td>
            </tr>
            
            <tr>
                <th scope="row">09:00-10:00</th>
                <td>ภาษาอังกฤษ<br><small>(ห้อง 601)</small></td>
                <td rowspan="2">ฟิสิกส์ (ปฏิบัติ)<br><small>(ห้องปฏิบัติการ)</small></td>
                <td rowspan="2">เคมี (ปฏิบัติ)<br><small>(ห้องปฏิบัติการ)</small></td>
                <td>คณิตศาสตร์<br><small>(ห้อง 602)</small></td>
                <td>สังคมศึกษา<br><small>(ห้อง 601)</small></td>
            </tr>
            
            <tr>
                <th scope="row">10:00-11:00</th>
                <td>สังคมศึกษา<br><small>(ห้อง 601)</small></td>
                <td>ภาษาอังกฤษ<br><small>(ห้อง 602)</small></td>
                <td>คณิตศาสตร์<br><small>(ห้อง 601)</small></td>
            </tr>
            
            <tr>
                <th scope="row">11:00-12:00</th>
                <td colspan="5"><strong>พักเที่ยง</strong></td>
            </tr>
            
            <tr>
                <th scope="row">12:00-13:00</th>
                <td>ชีววิทยา<br><small>(ห้อง 601)</small></td>
                <td>คณิตศาสตร์<br><small>(ห้อง 601)</small></td>
                <td>ภาษาอังกฤษ<br><small>(ห้องคอมพิวเตอร์)</small></td>
                <td>พลศึกษา<br><small>(สนามกีฬา)</small></td>
                <td rowspan="2">กิจกรรมชุมนุม<br><small>(ตามกลุ่ม)</small></td>
            </tr>
            
            <tr>
                <th scope="row">13:00-14:00</th>
                <td>ภาษาจีน<br><small>(ห้อง 603)</small></td>
                <td>ศิลปะ<br><small>(ห้องศิลปะ)</small></td>
                <td>ดนตรี<br><small>(ห้องดนตรี)</small></td>
                <td>คอมพิวเตอร์<br><small>(ห้องคอมพิวเตอร์)</small></td>
            </tr>
        </tbody>
    </table>
    
    <p><small>หมายเหตุ: ตารางอาจมีการเปลี่ยนแปลงตามความเหมาะสม</small></p>
</body>
</html>
```

### **คำอธิบาย:**
- `rowspan="2"`: รวม 2 แถวสำหรับวิชาปฏิบัติการที่เรียน 2 ชั่วโมงติดต่อกัน
- `colspan="5"`: รวม 5 คอลัมน์สำหรับ "พักเที่ยง"
- `<br>`: ขึ้นบรรทัดใหม่ภายในเซลล์
- `<small>`: แสดงข้อมูลเสริม (ห้องเรียน) ในขนาดเล็ก

**จุดสำคัญ:**
- `rowspan` ใช้เมื่อเซลล์ครอบคลุมหลายแถว
- `colspan` ใช้เมื่อเซลล์ครอบคลุมหลายคอลัมน์
- ต้องนับจำนวนเซลล์ในแต่ละแถวให้ถูกต้อง

---

## 💼 **Lab 4: ตารางรายงานยอดขาย - เฉลย**

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>รายงานยอดขายไตรมาส 1</title>
</head>
<body>
    <h1>รายงานยอดขายประจำไตรมาสที่ 1 ปี 2567</h1>
    
    <table>
        <caption>
            <strong>รายงานยอดขายตามประเภทสินค้า ไตรมาสที่ 1/2567</strong><br>
            <small>หน่วย: ล้านบาท | อัปเดต: 31 มีนาคม 2567</small>
        </caption>
        
        <colgroup>
            <col>
            <col span="3" class="months">
            <col span="2" class="summary">
        </colgroup>
        
        <thead>
            <tr>
                <th scope="col" rowspan="2">ประเภทสินค้า</th>
                <th scope="colgroup" colspan="3">รายเดือน</th>
                <th scope="colgroup" colspan="2">สรุป</th>
            </tr>
            <tr>
                <th scope="col">มกราคม</th>
                <th scope="col">กุมภาพันธ์</th>
                <th scope="col">มีนาคม</th>
                <th scope="col">รวม</th>
                <th scope="col">เติบโต (%)</th>
            </tr>
        </thead>
        
        <tbody>
            <tr>
                <th scope="row">โทรศัพท์มือถือ</th>
                <td>15.2</td>
                <td>18.5</td>
                <td>22.1</td>
                <td><strong>55.8</strong></td>
                <td><mark>+12.5</mark></td>
            </tr>
            
            <tr>
                <th scope="row">แท็บเล็ต</th>
                <td>8.3</td>
                <td>9.7</td>
                <td>11.2</td>
                <td><strong>29.2</strong></td>
                <td><mark>+8.3</mark></td>
            </tr>
            
            <tr>
                <th scope="row">โน้ตบุ๊ก</th>
                <td>12.5</td>
                <td>14.8</td>
                <td>16.3</td>
                <td><strong>43.6</strong></td>
                <td><mark>+15.2</mark></td>
            </tr>
            
            <tr>
                <th scope="row">สมารท์วอทช์</th>
                <td>5.8</td>
                <td>6.2</td>
                <td>7.5</td>
                <td><strong>19.5</strong></td>
                <td><mark>+18.7</mark></td>
            </tr>
            
            <tr>
                <th scope="row">หูฟัง</th>
                <td>3.2</td>
                <td>3.8</td>
                <td>4.5</td>
                <td><strong>11.5</strong></td>
                <td><mark>+22.1</mark></td>
            </tr>
            
            <tr>
                <th scope="row">อุปกรณ์เสริม</th>
                <td>4.5</td>
                <td>5.2</td>
                <td>6.1</td>
                <td><strong>15.8</strong></td>
                <td><mark>+10.5</mark></td>
            </tr>
        </tbody>
        
        <tfoot>
            <tr>
                <th scope="row">รวมทั้งหมด</th>
                <td><strong>49.5</strong></td>
                <td><strong>58.2</strong></td>
                <td><strong>67.7</strong></td>
                <td><mark>175.4</mark></td>
                <td><mark>+14.2</mark></td>
            </tr>
        </tfoot>
    </table>
    
    <section>
        <h2>สรุปผล</h2>
        <ul>
            <li>ยอดขายรวม <strong>175.4 ล้านบาท</strong> เติบโต <mark>14.2%</mark> จากไตรมาสก่อน</li>
            <li>สินค้าที่ขายดีที่สุด: <strong>โทรศัพท์มือถือ</strong> (55.8 ล้านบาท)</li>
            <li>สินค้าที่เติบโตสูงสุด: <mark>หูฟัง +22.1%</mark></li>
        </ul>
    </section>
</body>
</html>
```

### **คำอธิบาย:**
- `<colgroup>` และ `<col>`: จัดกลุ่มคอลัมน์สำหรับ styling
- `<col span="3">`: กำหนด attributes สำหรับ 3 คอลัมน์
- `rowspan="2"` ใน `<th>`: หัว "ประเภทสินค้า" ครอบคลุม 2 แถว
- `colspan="3"` ใน `<th>`: หัว "รายเดือน" ครอบคลุม 3 คอลัมน์
- `scope="colgroup"`: ระบุว่าเป็นหัวของกลุ่มคอลัมน์

**จุดสำคัญ:**
- ตารางซับซ้อนต้องวางแผนโครงสร้างก่อน
- ใช้ `rowspan` และ `colspan` ร่วมกันสำหรับ multi-level headers
- `scope="colgroup"` ใช้สำหรับหัวที่ครอบคลุมหลายคอลัมน์
- `<colgroup>` ช่วยในการจัด styling แบบกลุ่ม

---

## 📊 **สรุปการใช้ Table Elements**

### **โครงสร้างมาตรฐาน:**

```html
<table>
    <caption>คำอธิบายตาราง</caption>
    
    <colgroup>
        <col>
        <col span="2" class="highlight">
    </colgroup>
    
    <thead>
        <tr>
            <th scope="col">หัวคอลัมน์ 1</th>
            <th scope="col">หัวคอลัมน์ 2</th>
        </tr>
    </thead>
    
    <tbody>
        <tr>
            <th scope="row">หัวแถว</th>
            <td>ข้อมูล</td>
        </tr>
    </tbody>
    
    <tfoot>
        <tr>
            <th scope="row">สรุป</th>
            <td>ยอดรวม</td>
        </tr>
    </tfoot>
</table>
```

### **Scope Attribute Values:**

| Value       | ใช้กับ | ความหมาย                    |
| ----------- | ------ | --------------------------- |
| `col`       | `<th>` | หัวคอลัมน์                  |
| `row`       | `<th>` | หัวแถว                      |
| `colgroup`  | `<th>` | หัวกลุ่มคอลัมน์             |
| `rowgroup`  | `<th>` | หัวกลุ่มแถว                 |

### **Colspan และ Rowspan:**

```html
<!-- รวมคอลัมน์ -->
<td colspan="3">รวม 3 คอลัมน์</td>

<!-- รวมแถว -->
<td rowspan="2">รวม 2 แถว</td>

<!-- รวมทั้งคอลัมน์และแถว -->
<td colspan="2" rowspan="3">รวม 2 คอลัมน์ x 3 แถว</td>
```

---

## ✅ **Checklist สำหรับตาราง HTML ที่ดี**

### **โครงสร้าง:**
- ✅ มี `<table>` เป็น container
- ✅ มี `<caption>` อธิบายตาราง
- ✅ แบ่งส่วนด้วย `<thead>`, `<tbody>`, `<tfoot>`
- ✅ ใช้ `<tr>` สำหรับแถว
- ✅ ใช้ `<th>` สำหรับหัวคอลัมน์/แถว
- ✅ ใช้ `<td>` สำหรับข้อมูลทั่วไป

### **Accessibility:**
- ✅ ใส่ `scope` attribute ใน `<th>`
- ✅ ใช้ `<caption>` ทุกครั้ง
- ✅ ไม่ใช้ตารางสำหรับ layout
- ✅ ตรวจสอบด้วย screen reader
- ✅ HTML validation ผ่าน

### **Attributes:**
- ✅ ใช้ `colspan` ถูกต้อง
- ✅ ใช้ `rowspan` ถูกต้อง
- ✅ ระบุ `scope` ใน `<th>`
- ✅ ใช้ `<colgroup>` เมื่อจำเป็น

---

## 🎨 **Styling Tips (CSS)**

### **Basic Table Styling:**

```css
/* Border และ spacing */
table {
    border-collapse: collapse;
    width: 100%;
    margin: 20px 0;
}

/* เซลล์ */
th, td {
    border: 1px solid #ddd;
    padding: 12px;
    text-align: left;
}

/* หัวตาราง */
thead {
    background-color: #4CAF50;
    color: white;
}

/* แถวสลับสี */
tbody tr:nth-child(even) {
    background-color: #f2f2f2;
}

/* Hover effect */
tbody tr:hover {
    background-color: #e0e0e0;
}

/* ส่วนท้าย */
tfoot {
    background-color: #333;
    color: white;
    font-weight: bold;
}
```

### **Responsive Table:**

```css
/* Wrapper สำหรับ scroll */
.table-wrapper {
    overflow-x: auto;
}

/* Mobile responsive */
@media screen and (max-width: 600px) {
    table {
        font-size: 14px;
    }
    
    th, td {
        padding: 8px;
    }
}
```

---

## 🚫 **ข้อผิดพลาดที่พบบ่อย**

### **1. ใช้ `<td>` แทน `<th>` สำหรับ headers:**

```html
<!-- ❌ ผิด -->
<tr>
    <td><strong>ชื่อ</strong></td>
    <td><strong>อายุ</strong></td>
</tr>

<!-- ✅ ถูก -->
<tr>
    <th scope="col">ชื่อ</th>
    <th scope="col">อายุ</th>
</tr>
```

### **2. ลืมใส่ `scope` attribute:**

```html
<!-- ❌ ผิด -->
<th>ชื่อคอลัมน์</th>

<!-- ✅ ถูก -->
<th scope="col">ชื่อคอลัมน์</th>
```

### **3. ใช้ `colspan`/`rowspan` ผิด:**

```html
<!-- ❌ ผิด - จำนวนเซลล์ไม่ตรง -->
<tr>
    <td>A</td>
    <td colspan="2">B</td>
    <td>C</td>
    <td>D</td> <!-- เกินจำนวน! -->
</tr>

<!-- ✅ ถูก -->
<tr>
    <td>A</td>
    <td colspan="2">B</td>
    <td>C</td> <!-- รวมได้ 4 เซลล์ -->
</tr>
```

### **4. ไม่มี `<caption>`:**

```html
<!-- ❌ ผิด -->
<table>
    <thead>...</thead>
</table>

<!-- ✅ ถูก -->
<table>
    <caption>คำอธิบายตาราง</caption>
    <thead>...</thead>
</table>
```

### **5. ใช้ตารางสำหรับ layout:**

```html
<!-- ❌ ผิด - ใช้ตารางจัด layout -->
<table>
    <tr>
        <td><header>...</header></td>
    </tr>
    <tr>
        <td><main>...</main></td>
    </tr>
</table>

<!-- ✅ ถูก - ใช้ semantic HTML -->
<header>...</header>
<main>...</main>
```

---

## 🏆 **Best Practices Summary**

1. **ใช้ตารางเฉพาะข้อมูลตาราง** - ไม่ใช้สำหรับ layout
2. **ใส่ `<caption>` เสมอ** - ช่วย accessibility และ SEO
3. **แบ่งโครงสร้าง** - ใช้ `<thead>`, `<tbody>`, `<tfoot>`
4. **ใช้ `<th>` สำหรับ headers** - พร้อม `scope` attribute
5. **ระวัง `colspan`/`rowspan`** - นับเซลล์ให้ถูกต้อง
6. **Validate HTML** - ตรวจสอบโครงสร้างให้ถูกต้อง
7. **ทดสอบ accessibility** - ใช้ screen reader ทดสอบ
8. **Responsive design** - ใช้ wrapper สำหรับ overflow

---

**สำเร็จแล้ว!** 🎉 ตอนนี้คุณเชี่ยวชาญการสร้างตาราง HTML แล้ว จำไว้ว่าตารางใช้เฉพาะข้อมูลตารางจริงๆ เท่านั้นนะครับ!