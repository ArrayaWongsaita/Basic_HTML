# เฉลย Lab Phase 3: Links, Images & Lists Challenge

## 🌟 **เฉลย Lab 1: เว็บไซต์ร้านอาหาร**

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>ร้านอาหารไทยแสนอร่อย</title>
</head>
<body>
    <h1>ร้านอาหารไทยแสนอร่อย</h1>
    
    <img src="restaurant.jpg" alt="ร้านอาหารไทยบรรยากาศอบอุ่น">
    
    <h2>เมนูแนะนำ</h2>
    <ul>
        <li>ต้มยำกุ้ง - รสเผ็ดเปรื้ยว</li>
        <li>ผัดไทย - หอมหวานกลมกล่อม</li>
        <li>ส้มตำ - สดชื่นถูกปาก</li>
        <li>แกงเขียวหวาน - เข้มข้นหอมกะทิ</li>
    </ul>
    
    <a href="menu.html">เมนูอาหาร</a>
    <a href="about.html">เกี่ยวกับเรา</a>
    
    <hr>
    
    <h2>วิธีสั่งอาหาร</h2>
    <ol>
        <li>เลือกเมนูที่ต้องการ</li>
        <li>ระบุจำนวน</li>
        <li>เพิ่มในตะกร้า</li>
        <li>ยืนยันการสั่ง</li>
        <li>รอรับอาหาร 15-20 นาที</li>
    </ol>
    
    <hr>
    
    <figure>
        <img src="chef.jpg" alt="เชฟมืออาชีพกำลังปรุงอาหาร">
        <figcaption>เชฟผู้เชี่ยวชาญของเราใช้วัตถุดิบคุณภาพดี</figcaption>
    </figure>
    
    <hr>
    
    <h2>ติดต่อเรา</h2>
    
    <p>ที่อยู่:<br>
    123 ถนนสุขุมวิท<br>
    แขวงคลองเตย<br>
    เขตคลองเตย<br>
    กรุงเทพมหานคร 10110</p>
    
    <p><a href="tel:02-123-4567">โทร 02-123-4567</a></p>
    <p><a href="mailto:order@restaurant.com">ส่งอีเมลสั่งอาหาร</a></p>
    
    <h3>ติดตามเรา</h3>
    <p><a href="https://facebook.com/restaurant" target="_blank">Facebook</a></p>
    <p><a href="https://instagram.com/restaurant" target="_blank">Instagram</a></p>
</body>
</html>
```

---

## 📚 **เฉลย Lab 2: เว็บไซต์หลักสูตรเรียน**

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>หลักสูตร Web Development</title>
</head>
<body>
    <h1>หลักสูตร Full Stack Web Development</h1>
    
    <img src="course-banner.jpg" alt="นักเรียนกำลังเรียนเขียนโปรแกรม">
    
    <h2>เนื้อหาการเรียน</h2>
    <ol>
        <li>HTML & CSS พื้นฐาน</li>
        <li>JavaScript ES6+</li>
        <li>React.js Framework</li>
        <li>Node.js Backend</li>
        <li>Database & MongoDB</li>
        <li>การทำโปรเจกต์จริง</li>
    </ol>
    
    <p><a href="course-outline.pdf" download>ดาวน์โหลดหลักสูตร</a></p>
    <p><a href="#details">ไปยังรายละเอียด</a></p>
    
    <hr>
    
    <h2>คุณสมบัติผู้เรียน</h2>
    <ul>
        <li>มีพื้นฐานคอมพิวเตอร์</li>
        <li>อยากเรียนรู้เทคโนโลยีใหม่</li>
        <li>มีเวลาเรียน 3-4 ชั่วโมงต่อวัน</li>
        <li>ตั้งใจเรียนจริงจัง</li>
    </ul>
    
    <hr>
    
    <h2>ศัพท์เทคนิคที่ควรรู้</h2>
    
    <dl>
        <dt>HTML</dt>
        <dd>ภาษาสำหรับสร้างโครงสร้างหน้าเว็บ</dd>
        
        <dt>CSS</dt>
        <dd>ภาษาสำหรับตกแต่งรูปแบบหน้าเว็บ</dd>
        
        <dt>JavaScript</dt>
        <dd>ภาษาโปรแกรมสำหรับทำให้เว็บมีการโต้ตอบ</dd>
        
        <dt>React</dt>
        <dd>JavaScript library สำหรับสร้าง User Interface</dd>
    </dl>
    
    <hr>
    
    <h2>ภาพบรรยากาศการเรียน</h2>
    <figure>
        <img src="classroom.jpg" alt="นักเรียนกำลังเรียนในห้องเรียน">
        <figcaption>ห้องเรียนที่ทันสมัยพร้อมอุปกรณ์ครบครัน</figcaption>
    </figure>
    
    <h2 id="details">รายละเอียดเพิ่มเติม</h2>
    
    <p>หลักสูตรนี้เหมาะสำหรับผู้ที่ต้องการเป็นนักพัฒนาเว็บไซต์มืออาชีพ
    โดยจะได้เรียนรู้ทั้งฝั่ง Frontend และ Backend</p>
    
    <p><a href="registration.html">ลงทะเบียนเรียน</a></p>
    <p><a href="contact.html">ติดต่อสอบถาม</a></p>
</body>
</html>
```

---

## 🛒 **เฉลย Lab 3: เว็บไซต์ร้านค้าออนไลน์**

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>iPhone 15 Pro Max - TechStore</title>
</head>
<body>
    <h1>iPhone 15 Pro Max 256GB - Natural Titanium</h1>
    
    <img src="iphone-front.jpg" alt="iPhone 15 Pro Max ด้านหน้า">
    <img src="iphone-back.jpg" alt="iPhone 15 Pro Max ด้านหลัง">
    <img src="iphone-side.jpg" alt="iPhone 15 Pro Max ด้านข้าง">
    
    <h2>คุณสมบัติเด่น</h2>
    <ul>
        <li>หน้าจอ Super Retina XDR 6.7 นิ้ว</li>
        <li>ชิป A17 Pro ประสิทธิภาพสูง</li>
        <li>กล้องหลัง 48MP พร้อม zoom 5x</li>
        <li>แบตเตอรี่ใช้งานได้ทั้งวัน</li>
        <li>ทำจากไทเทเนียม เบาแต่แข็งแกร่ง</li>
    </ul>
    
    <h2>ขั้นตอนการสั่งซื้อ</h2>
    <ol>
        <li>เลือกสีและความจำที่ต้องการ</li>
        <li>คลิกเพิ่มลงตะกร้า</li>
        <li>ไปที่หน้าชำระเงิน</li>
        <li>กรอกข้อมูลการจัดส่ง</li>
        <li>เลือกวิธีชำระเงิน</li>
        <li>ยืนยันการสั่งซื้อ</li>
    </ol>
    
    <p><a href="javascript:addToCart('iphone15pm')">เพิ่มลงตะกร้า</a></p>
    
    <hr>
    
    <h2>สเปคโดยละเอียด</h2>
    
    <dl>
        <dt>หน้าจอ</dt>
        <dd>Super Retina XDR OLED 6.7 นิ้ว 2796 x 1290 พิกเซล</dd>
        
        <dt>ชิปประมวลผล</dt>
        <dd>A17 Pro 6-core CPU, 6-core GPU</dd>
        
        <dt>กล้อง</dt>
        <dd>กล้องหลัง 48MP + 12MP + 12MP, กล้องหน้า 12MP</dd>
        
        <dt>พื้นที่จัดเก็บ</dt>
        <dd>256GB, 512GB, 1TB</dd>
        
        <dt>น้ำหนัก</dt>
        <dd>221 กรัม</dd>
    </dl>
    
    <hr>
    
    <h2>รีวิวจากลูกค้า</h2>
    <figure>
        <img src="customer-review.jpg" alt="ลูกค้าใช้งาน iPhone 15 Pro Max">
        <figcaption>ลูกค้าให้คะแนน 5 ดาว พอใจประสิทธิภาพกล้อง</figcaption>
    </figure>
    
    <hr>
    
    <h2>สินค้าที่เกี่ยวข้อง</h2>
    <p><a href="iphone15pro.html">iPhone 15 Pro</a></p>
    <p><a href="airpods.html">AirPods Pro</a></p>
    <p><a href="case.html">เคสกันกระแทก</a></p>
    
    <h3>แชร์สินค้า</h3>
    <p><a href="https://facebook.com/sharer/..." target="_blank">แชร์ Facebook</a></p>
    <p><a href="https://social-plugins.line.me/..." target="_blank">แชร์ Line</a></p>
    <p><a href="https://twitter.com/intent/tweet..." target="_blank">แชร์ Twitter</a></p>
</body>
</html>
```

---

## 🏥 **เฉลย Lab 4: เว็บไซต์โรงพยาบาล**

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>โรงพยาบาลสุขภาพดี</title>
</head>
<body>
    <h1>โรงพยาบาลสุขภาพดี</h1>
    <p>ให้บริการด้วยใจ เพื่อสุขภาพที่ดีของคุณ</p>
    
    <img src="hospital-building.jpg" alt="อาคารโรงพยาบาลสุขภาพดี 10 ชั้น">
    
    <h2>แผนกบริการ</h2>
    <ul>
        <li>แผนกอายุรกรรม</li>
        <li>แผนกศัลยกรรม</li>
        <li>แผนกกุมารเวชกรรม</li>
        <li>แผนกสูตินรีเวชกรรม</li>
        <li>แผนกฉุกเฉิน 24 ชั่วโมง</li>
        <li>แผนกรังสีวินิจฉัย</li>
    </ul>
    
    <p><a href="departments.html">แผนกทั้งหมด</a></p>
    <p><a href="special-services.html">บริการพิเศษ</a></p>
    
    <hr>
    
    <h2>วิธีนัดหมายแพทย์</h2>
    <ol>
        <li>โทรศัพท์ติดต่อแผนกที่ต้องการ</li>
        <li>แจ้งอาการและข้อมูลผู้ป่วย</li>
        <li>เลือกวันเวลาที่เหมาะสม</li>
        <li>รับหมายเลขนัดหมาย</li>
        <li>มาตามนัดพร้อมเอกสาร</li>
    </ol>
    
    <p><a href="appointment.html">นัดหมายออนไลน์</a></p>
    <p><a href="tel:1669">โทรฉุกเฉิน 1669</a></p>
    <p><a href="tel:02-555-0100">โทรสอบถาม 02-555-0100</a></p>
    
    <hr>
    
    <h2>ทีมแพทย์เชี่ยวชาญ</h2>
    
    <dl>
        <dt>นพ.สมชาย ใจดี</dt>
        <dd>แพทย์เชี่ยวชาญด้านโรคหัวใจ 15 ปี</dd>
        
        <dt>นพ.สมหญิง รักษ์โรค</dt>
        <dd>แพทย์เชี่ยวชาญด้านมะเร็งวิทยา 12 ปี</dd>
        
        <dt>นพ.วิชัย หายป่วย</dt>
        <dd>แพทย์เชี่ยวชาญด้านศัลยกรรมกระดูก 18 ปี</dd>
        
        <dt>นพ.สมปอง รักษาดี</dt>
        <dd>แพทย์เชี่ยวชาญด้านกุมารเวชกรรม 10 ปี</dd>
    </dl>
    
    <hr>
    
    <h2>บริการพิเศษ</h2>
    <figure>
        <img src="mri-scan.jpg" alt="เครื่อง MRI ที่ทันสมัย">
        <figcaption>เครื่อง MRI ความละเอียดสูง สำหรับตรวจวินิจฉัยที่แม่นยำ</figcaption>
    </figure>
    
    <hr>
    
    <h2>ข้อมูลการติดต่อ</h2>
    
    <p>ที่อยู่:<br>
    456 ถนนพหลโยธิน<br>
    แขวงสามเสนใน<br>
    เขตพญาไท<br>
    กรุงเทพมหานคร 10400</p>
    
    <p><a href="https://goo.gl/maps/..." target="_blank">ดูแผนที่ Google Maps</a></p>
    
    <h3>ข้อมูลเพิ่มเติม</h3>
    <p><a href="about.html">เกี่ยวกับเรา</a></p>
    <p><a href="news.html">ข่าวสาร</a></p>
    <p><a href="contact.html">ติดต่อเรา</a></p>
</body>
</html>
```

---

## 📊 **สรุปการใช้ Tags ในแต่ละ Lab**

### **Lab 1 - ร้านอาหาร:**
- `<h1>`, `<h2>`, `<h3>` - หัวข้อต่างระดับ
- `<img>` - รูปภาพร้านและเชฟ
- `<ul>`, `<li>` - รายการเมนูอาหาร
- `<ol>`, `<li>` - ขั้นตอนการสั่งอาหาร
- `<figure>`, `<figcaption>` - รูปภาพพร้อมคำบรรยาย
- `<a href="file.html">` - ลิงก์หน้าอื่น
- `<a href="tel:">` - ลิงก์โทรศัพท์
- `<a href="mailto:">` - ลิงก์อีเมล
- `<a target="_blank">` - เปิดหน้าใหม่
- `<br>` - ขึ้นบรรทัดในที่อยู่

### **Lab 2 - หลักสูตรเรียน:**
- `<h1>`, `<h2>` - หัวข้อหลักและรอง
- `<ol>`, `<li>` - เนื้อหาการเรียนตามลำดับ
- `<ul>`, `<li>` - คุณสมบัติผู้เรียน
- `<dl>`, `<dt>`, `<dd>` - ศัพท์เทคนิค
- `<a href="#id">` - ลิงก์ภายในหน้า
- `<a download>` - ลิงก์ดาวน์โหลด
- `<figure>`, `<figcaption>` - ภาพบรรยากาศ
- `id="details"` - จุดปลายทางของลิงก์

### **Lab 3 - ร้านค้าออนไลน์:**
- รูปภาพหลายใบสำหรับสินค้า
- `<ul>` - คุณสมบัติสินค้า
- `<ol>` - ขั้นตอนการสั่งซื้อ
- `<dl>`, `<dt>`, `<dd>` - สเปคโดยละเอียด
- `<a href="javascript:">` - เรียกใช้ JavaScript
- `<figure>`, `<figcaption>` - รีวิวลูกค้า
- ลิงก์แชร์ social media
- ลิงก์สินค้าที่เกี่ยวข้อง

### **Lab 4 - โรงพยาบาล:**
- `<ul>` - แผนกบริการ
- `<ol>` - ขั้นตอนการนัดหมาย
- `<dl>`, `<dt>`, `<dd>` - ข้อมูลแพทย์
- `<a href="tel:1669">` - หมายเลขฉุกเฉิน
- `<a href="tel:02-xxx-xxxx">` - เบอร์สอบถาม
- `<figure>`, `<figcaption>` - เครื่องมือทางการแพทย์
- `<a target="_blank">` - แผนที่ Google Maps
- ลิงก์ข้อมูลเพิ่มเติม

---

## ✅ **หลักการตรวจให้คะแนน**

### **คะแนนเต็ม 100 แบ่งเป็น:**

**1. การใช้ Link Tags และ Attributes (40 คะแนน)**
- `<a href="">` รูปแบบถูกต้อง (10)
- `href="tel:"`, `href="mailto:"` ถูกต้อง (10)
- `target="_blank"` ใช้เหมาะสม (10)
- `href="#id"` และ `id=""` ทำงานร่วมกัน (5)
- `download` attribute ใช้ถูกต้อง (5)

**2. การใช้ Image Tags และ Attributes (25 คะแนน)**
- `<img src="" alt="">` ครบถ้วน (10)
- `alt` text มีความหมายเหมาะสม (10)
- `<figure>` และ `<figcaption>` ใช้ถูกต้อง (5)

**3. การใช้ List Tags (25 คะแนน)**
- `<ul>`, `<ol>`, `<li>` ใช้เหมาะสมตามบริบท (15)
- `<dl>`, `<dt>`, `<dd>` ใช้ถูกต้อง (10)

**4. โครงสร้าง HTML และ Semantic (10 คะแนน)**
- Tags เปิด-ปิดถูกต้อง (5)
- การใช้ semantic elements เหมาะสม (5)

### **ข้อผิดพลาดที่หักคะแนน:**

**Links (-5 คะแนนต่อข้อ)**
- ไม่ใส่ `href` หรือใส่ผิดรูปแบบ
- ไม่ใส่ `target="_blank"` เมื่อจำเป็น
- `href="tel:"` หรือ `href="mailto:"` ผิดรูปแบบ

**Images (-3 คะแนนต่อข้อ)**
- ไม่ใส่ `alt` attribute
- `alt` text ไม่เหมาะสมหรือไม่มีความหมาย
- `src` ชี้ไปไฟล์ที่ไม่มี (ถ้ามี)

**Lists (-3 คะแนนต่อข้อ)**
- ใช้ `<ol>` เมื่อควรใช้ `<ul>` หรือในทางกลับกัน
- ไม่ใส่ `<li>` ใน list containers
- `<dt>`, `<dd>` ไม่อยู่ใน `<dl>`

**Structure (-5 คะแนนต่อข้อ)**
- Tags ไม่ปิดหรือ nesting ผิด
- ใช้ elements ไม่เหมาะสมกับบริบท

---

## 🚀 **เทคนิคขั้นสูงสำหรับครู**

### **การขยายผล Lab:**
1. **เพิ่มไฟล์จริง** - สร้างไฟล์รูปภาพและหน้าเว็บที่ลิงก์ไป
2. **เพิ่ม CSS** - ให้นักเรียนตกแต่งผลงาน
3. **การทำ validation** - ใช้ W3C Validator ตรวจสอบ
4. **Accessibility testing** - ทดสอบด้วย screen reader
5. **Responsive design** - ทดสอบในอุปกรณ์ต่างๆ

### **การประเมินเพิ่มเติม:**
- ให้นักเรียนอธิบายเหตุผลในการเลือกใช้ tags
- ทดสอบการทำงานของลิงก์
- ตรวจสอบความเหมาะสมของ `alt` text
- ประเมิน user experience

### **กิจกรรมเสริม:**
- ให้นักเรียนสร้าง sitemap
- การทำ breadcrumb navigation
- การสร้างรูปภาพ thumbnail
- การเขียน `alt` text ที่ดี

**การใช้ Lab นี้จะช่วยให้นักเรียนเข้าใจการสร้างเว็บไซต์ที่มีการนำทางที่ดี, แสดงรูปภาพอย่างเหมาสม, และจัดระเบียบข้อมูลในรูปแบบรายการได้อย่างมีประสิทธิภาพ**