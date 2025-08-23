# รูปภาพใน HTML: `<img>` Tag และ Attributes สำคัญ

## แนวคิดพื้นฐานของรูปภาพในเว็บ

### 🖼️ **รูปภาพในเว็บไซต์คืออะไร?**

รูปภาพเป็นองค์ประกอบสำคัญของเว็บไซต์ที่ช่วย:

- **สื่อสารข้อมูล** - บอกเล่าเรื่องราวผ่านภาพ
- **เพิ่มความน่าสนใจ** - ทำให้เนื้อหาดูน่าอ่าน
- **อธิบายเนื้อหา** - แสดงตัวอย่าง แผนภูมิ กราฟ
- **สร้างบรรยากาศ** - กำหนด mood ของเว็บไซต์
- **ปรับปรุง UX** - ช่วยให้ผู้ใช้เข้าใจง่ายขึ้น

### 🎯 **ความสำคัญของการใช้รูปภาพ**

- **Visual Communication**: การสื่อสารด้วยภาพ
- **SEO Benefits**: รูปภาพช่วย SEO ถ้าใช้ถูกต้อง
- **Accessibility**: ต้องเป็นมิตรกับผู้พิการทางสายตา
- **Performance**: ต้องโหลดเร็วไม่ให้เว็บช้า
- **Responsive**: ต้องแสดงผลดีในทุกอุปกรณ์

---

## 1. `<img>` Tag - Image Element

### 📝 **ความหมายและการใช้งาน**

- **ชื่อเต็ม**: Image Element
- **ประเภท**: Empty Element (ไม่มี closing tag)
- **วัตถุประสงค์**: แสดงรูปภาพในหน้าเว็บ
- **การแสดงผล**: Inline-block element

### 🏗️ **โครงสร้างพื้นฐาน**

```html
<img src="path/to/image.jpg" alt="คำอธิบายรูปภาพ" />
```

#### **โครงสร้างสมบูรณ์**

```html
<img
  src="images/photo.jpg"
  alt="รูปภาพตัวอย่าง"
  width="300"
  height="200"
  loading="lazy"
  title="คำอธิบายเพิ่มเติม"
  class="responsive-image"
  id="main-photo"
/>
```

### ✅ **ตัวอย่างพื้นฐาน**

```html
<!-- รูปภาพในโฟลเดอร์เดียวกัน -->
<img src="logo.png" alt="โลโก้บริษัท ABC" />

<!-- รูปภาพในโฟลเดอร์ย่อย -->
<img src="images/products/phone.jpg" alt="สมาร์ทโฟนรุ่นใหม่" />

<!-- รูปภาพจากอินเทอร์เน็ต -->
<img src="https://example.com/photo.jpg" alt="รูปภาพจากเว็บไซต์ภายนอก" />
```

---

## 2. `src` Attribute - แหล่งที่มาของรูปภาพ

### 📝 **ความหมายและการใช้งาน**

- **ชื่อเต็ม**: Source
- **วัตถุประสงค์**: กำหนดตำแหน่งไฟล์รูปภาพ
- **ความจำเป็น**: **บังคับต้องมี** (Required)
- **ค่า**: URL หรือ path ไปยังไฟล์รูปภาพ

### 🌐 **ประเภทของ src**

#### **1. Relative Path (เส้นทางสัมพัทธ์)**

```html
<!-- ไฟล์ในโฟลเดอร์เดียวกัน -->
<img src="logo.png" alt="โลโก้" />

<!-- ไฟล์ในโฟลเดอร์ย่อย -->
<img src="images/photo.jpg" alt="รูปภาพ" />
<img src="assets/icons/star.svg" alt="ไอคอนดาว" />

<!-- ไฟล์ในโฟลเดอร์ระดับบน -->
<img src="../images/header.jpg" alt="ส่วนหัว" />
<img src="../../assets/logo.png" alt="โลโก้" />

<!-- โครงสร้างโฟลเดอร์ตัวอย่าง -->
<!--
project/
├── index.html
├── about/
│   └── team.html
├── images/
│   ├── logo.png
│   ├── hero.jpg
│   └── products/
│       └── phone.jpg
└── assets/
    └── icons/
        └── star.svg
-->
```

#### **2. Absolute Path (เส้นทางสมบูรณ์)**

```html
<!-- เส้นทางจากรากของเว็บไซต์ -->
<img src="/images/logo.png" alt="โลโก้" />
<img src="/assets/photos/team.jpg" alt="ทีมงาน" />

<!-- URL สมบูรณ์ -->
<img src="https://www.example.com/images/photo.jpg" alt="รูปภาพ" />
```

#### **3. Data URLs (Base64)**

```html
<!-- รูปภาพเล็กๆ ที่เข้ารหัสเป็น Base64 -->
<img
  src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVR42mP8/5+hHgAHggJ/PchI7wAAAABJRU5ErkJggg=="
  alt="จุดเล็กๆ"
/>

<!-- ใช้สำหรับไอคอนเล็กๆ หรือรูปภาพขนาดเล็ก -->
```

### 🖼️ **รูปแบบไฟล์ที่รองรับ**

```html
<!-- รูปแบบพื้นฐาน -->
<img src="photo.jpg" alt="JPEG" />
<img src="logo.png" alt="PNG" />
<img src="animation.gif" alt="GIF" />

<!-- รูปแบบใหม่ (HTML5) -->
<img src="vector.svg" alt="SVG" />
<img src="modern.webp" alt="WebP" />
<img src="future.avif" alt="AVIF" />

<!-- รูปแบบอื่นๆ -->
<img src="bitmap.bmp" alt="BMP" />
<img src="icon.ico" alt="ICO" />
```

---

## 3. `alt` Attribute - **สำคัญที่สุด!**

### 📝 **ความหมายและความสำคัญ**

- **ชื่อเต็ม**: Alternative Text
- **วัตถุประสงค์**: อธิบายเนื้อหาของรูปภาพ
- **ความจำเป็น**: **สำคัญมาก** แม้ไม่บังคับ
- **ผลกระทบ**: SEO, Accessibility, User Experience

### ♿ **ความสำคัญด้าน Accessibility**

#### **1. Screen Readers**

```html
<!-- Screen reader จะอ่าน alt text ให้ผู้พิการทางสายตาฟัง -->
<img src="chart.png" alt="กราฟแสดงยอดขายเพิ่มขึ้น 25% ในปี 2024" />

<!-- ผู้ใช้จะได้ยิน: "กราฟแสดงยอดขายเพิ่มขึ้น 25% ในปี 2024" -->
```

#### **2. เมื่อรูปภาพโหลดไม่ได้**

```html
<!-- หากรูปโหลดไม่ได้ จะแสดง alt text แทน -->
<img src="broken-link.jpg" alt="รูปภาพผลิตภัณฑ์ใหม่ของเรา" />
<!-- ผู้ใช้จะเห็น: รูปภาพผลิตภัณฑ์ใหม่ของเรา -->
```

#### **3. ใช้งานแบบ Text-only**

```html
<!-- ผู้ใช้ที่ปิดการแสดงรูปภาพจะเห็น alt text -->
<img src="infographic.png" alt="อินโฟกราฟิก: 5 ขั้นตอนการทำเค้ก" />
```

### 🔍 **ความสำคัญด้าน SEO**

#### **1. Google Image Search**

```html
<!-- Google ใช้ alt text ในการจัดอันดับ Google Images -->
<img src="iphone-15-pro.jpg" alt="iPhone 15 Pro สีทิไทเนียมธรรมชาติ 256GB" />
```

#### **2. Context ของหน้าเว็บ**

```html
<!-- Google ใช้ alt text เพื่อเข้าใจเนื้อหาของหน้า -->
<img src="recipe-steps.jpg" alt="ขั้นตอนการทำต้มยำกุ้ง แบบไทยแท้" />
```

### ✍️ **วิธีเขียน alt text ที่ดี**

#### **1. อธิบายสิ่งที่เห็นในรูป**

```html
<!-- ✅ ดี - อธิบายชัดเจน -->
<img src="sunset.jpg" alt="พระอาทิตย์ตกเหนือทะเลในตอนเย็น สีฟ้าส้มสวยงาม" />

<!-- ❌ ไม่ดี - ไม่ได้อธิบายภาพ -->
<img src="sunset.jpg" alt="รูปสวย" />
```

#### **2. อธิบายฟังก์ชันของรูป**

```html
<!-- ✅ ดี - อธิบายวัตถุประสงค์ -->
<img src="search-icon.png" alt="ไอคอนค้นหา - คลิกเพื่อเปิดหน้าต่างค้นหา" />

<!-- ❌ ไม่ดี - อธิบายแค่ชื่อไฟล์ -->
<img src="search-icon.png" alt="search-icon.png" />
```

#### **3. ให้บริบทที่เหมาะสม**

```html
<!-- ในบทความเกี่ยวกับการทำอาหาร -->
<img
  src="chopping-onions.jpg"
  alt="การหั่นหอมใหญ่เป็นชิ้นเล็กๆ เตรียมสำหรับทำแกงเขียวหวาน"
/>

<!-- ในแกลเลอรี่รูปภาพ -->
<img src="chopping-onions.jpg" alt="ภาพถ่ายการหั่นหอมใหญ่ในครัว" />
```

### 🎯 **Alt text สำหรับประเภทรูปภาพต่างๆ**

#### **1. รูปภาพที่ให้ข้อมูล (Informative Images)**

```html
<!-- กราฟ/แผนภูมิ -->
<img
  src="sales-chart.png"
  alt="กราฟแสดงยอดขายรายเดือน: มกราคม 100,000 บาท กุมภาพันธ์ 120,000 บาท มีนาคม 150,000 บาท"
/>

<!-- แผนที่ -->
<img
  src="office-map.jpg"
  alt="แผนที่ตำแหน่งสำนักงาน: ชั้น 5 อาคาร ABC ถนนสุขุมวิท กรุงเทพฯ"
/>

<!-- สกรีนช็อต -->
<img
  src="app-screenshot.png"
  alt="หน้าจอแอปพลิเคชัน แสดงเมนูหลัก 4 ตัวเลือก: โปรไฟล์ การตั้งค่า ประวัติ ออกจากระบบ"
/>
```

#### **2. รูปภาพประกอบ (Decorative Images)**

```html
<!-- รูปประกอบที่ไม่ได้ให้ข้อมูลสำคัญ -->
<img src="decorative-border.png" alt="" />
<img src="background-pattern.jpg" alt="" />

<!-- ⚠️ สำคัญ: ใช้ alt="" (เปล่า) สำหรับรูปประกอบ -->
<!-- ไม่ใช่ alt="decorative image" -->
```

#### **3. รูปภาพผลิตภัณฑ์ (Product Images)**

```html
<!-- สินค้า e-commerce -->
<img src="nike-shoes.jpg" alt="รองเท้าผ้าใบ Nike Air Max 270 สีดำขาว ไซส์ 42" />

<!-- บริการ -->
<img src="massage-service.jpg" alt="บริการนวดแผนไทย ห้องส่วนตัว บรรยากาศสบาย" />

<!-- อาหาร -->
<img
  src="pad-thai.jpg"
  alt="ผัดไทยกุ้งใหญ่ ใส่ถั่วงอก หอมหัวใหญ่ โรยถั่วลิสงคั่ว เสิร์ฟพร้อมมะนาว"
/>
```

#### **4. รูปภาพบุคคล (People Images)**

```html
<!-- ทีมงาน -->
<img
  src="john-doe.jpg"
  alt="นาย จอห์น โด ผู้จัดการฝ่ายขาย ยิ้มแย้มใส่เสื้อเชิ้ตสีฟ้า"
/>

<!-- ผู้ใช้บริการ -->
<img
  src="customer-review.jpg"
  alt="คุณสมหญิง อายุ 35 ปี ลูกค้าที่ใช้บริการคลีนิคความงาม ยิ้มมั่นใจ"
/>
```

#### **5. รูปภาพที่มีข้อความ (Images with Text)**

```html
<!-- ข้อความในรูป ต้องใส่ข้อความนั้นใน alt -->
<img src="sale-banner.jpg" alt="ลดราคาสูงสุด 50% วันที่ 15-20 มกราคม 2024" />

<!-- โลโก้ที่มีข้อความ -->
<img src="company-logo.png" alt="ABC Learning - แพลตฟอร์มเรียนออนไลน์" />
```

### ❌ **สิ่งที่ไม่ควรทำกับ alt text**

#### **1. อย่าเริ่มต้นด้วย "รูปภาพ" "ภาพ" "image"**

```html
<!-- ❌ ไม่ดี -->
<img src="cat.jpg" alt="รูปภาพแมวขาว" />
<img src="graph.png" alt="ภาพกราฟยอดขาย" />

<!-- ✅ ดี -->
<img src="cat.jpg" alt="แมวขาวนั่งบนโซฟา" />
<img src="graph.png" alt="กราฟยอดขายเพิ่มขึ้น 15%" />
```

#### **2. อย่าใส่คำสำคัญโดยไม่เกี่ยวข้อง (Keyword Stuffing)**

```html
<!-- ❌ ไม่ดี - keyword stuffing -->
<img
  src="phone.jpg"
  alt="โทรศัพท์ สมาร์ทโฟน มือถือ ราคาถูก ซื้อออนไลน์ ส่งฟรี"
/>

<!-- ✅ ดี -->
<img src="phone.jpg" alt="สมาร์ทโฟน Samsung Galaxy S24 สีดำ" />
```

#### **3. อย่าอธิบายยาวเกินไป**

```html
<!-- ❌ ไม่ดี - ยาวเกิน -->
<img
  src="office.jpg"
  alt="สำนักงานของเราตั้งอยู่ในอาคารสูง 20 ชั้น ที่มีพนักงานหลากหลายแผนกทำงานด้วยความตั้งใจและมีคอมพิวเตอร์ที่ทันสมัยพร้อมเฟอร์นิเจอร์ที่สวยงาม"
/>

<!-- ✅ ดี -->
<img
  src="office.jpg"
  alt="สำนักงานทันสมัย พนักงานทำงานบนคอมพิวเตอร์ บรรยากาศเปิดโล่ง"
/>
```

---

## 4. `width` และ `height` Attributes - การกำหนดขนาด

### 📝 **ความหมายและการใช้งาน**

- **วัตถุประสงค์**: กำหนดขนาดของรูปภาพ
- **หน่วย**: พิกเซล (ค่าเริ่มต้น)
- **ประโยชน์**: ป้องกัน layout shift, เพิ่มประสิทธิภาพ

### 📐 **การใช้งานพื้นฐาน**

```html
<!-- กำหนดขนาดเต็ม -->
<img src="photo.jpg" alt="รูปภาพ" width="300" height="200" />

<!-- กำหนดแค่ความกว้าง (ความสูงจะปรับตามสัดส่วน) -->
<img src="photo.jpg" alt="รูปภาพ" width="300" />

<!-- กำหนดแค่ความสูง (ความกว้างจะปรับตามสัดส่วน) -->
<img src="photo.jpg" alt="รูปภาพ" height="200" />
```

### 🎯 **เชิงสัดส่วน (Aspect Ratio)**

#### **1. รักษาสัดส่วนเดิม**

```html
<!-- รูปต้นฉบับ: 800x600 (สัดส่วน 4:3) -->

<!-- ✅ ถูกต้อง - รักษาสัดส่วน 4:3 -->
<img src="photo.jpg" alt="รูปภาพ" width="400" height="300" />
<img src="photo.jpg" alt="รูปภาพ" width="200" height="150" />

<!-- ❌ ผิด - ทำให้รูปบิดเบี้ยว -->
<img src="photo.jpg" alt="รูปภาพ" width="400" height="200" />
```

#### **2. การคำนวณสัดส่วน**

```html
<!-- สูตรคำนวณ: ความสูงใหม่ = (ความกว้างใหม่ × ความสูงเดิม) ÷ ความกว้างเดิม -->

<!-- รูปต้นฉบับ: 1200x800 -->
<!-- ต้องการความกว้าง 300 พิกเซล -->
<!-- ความสูงใหม่ = (300 × 800) ÷ 1200 = 200 พิกเซล -->

<img src="landscape.jpg" alt="ภาพทิวทัศน์" width="300" height="200" />
```

### 🚀 **ประโยชน์ของการกำหนด width/height**

#### **1. ป้องกัน Layout Shift**

```html
<!-- ✅ ดี - เบราว์เซอร์รู้ขนาดล่วงหน้า ไม่เกิด layout shift -->
<img src="hero-image.jpg" alt="รูปหลัก" width="800" height="400" />

<!-- ❌ ไม่ดี - เบราว์เซอร์ไม่รู้ขนาด จะมี layout shift เมื่อรูปโหลดเสร็จ -->
<img src="hero-image.jpg" alt="รูปหลัก" />
```

#### **2. เพิ่มประสิทธิภาพการโหลด**

```html
<!-- เบราว์เซอร์จองพื้นที่ไว้ก่อน ผู้ใช้ไม่เห็นเนื้อหากระโดด -->
<img src="large-image.jpg" alt="รูปขนาดใหญ่" width="600" height="400" />
```

### 📱 **Responsive Images กับ CSS**

```html
<!-- HTML กำหนดขนาดสูงสุด -->
<img
  src="responsive.jpg"
  alt="รูปภาพ responsive"
  width="800"
  height="600"
  class="responsive-img"
/>

<style>
  .responsive-img {
    max-width: 100%; /* ไม่เกินขนาด container */
    height: auto; /* รักษาสัดส่วน */
  }

  /* Mobile */
  @media (max-width: 768px) {
    .responsive-img {
      width: 100%;
    }
  }
</style>
```

---

## 5. `loading` Attribute - การโหลดแบบ Lazy

### 📝 **ความหมายและการใช้งาน**

- **ใหม่ใน HTML5**: รองรับในเบราว์เซอร์ใหม่
- **วัตถุประสงค์**: ควบคุมการโหลดรูปภาพ
- **ประโยชน์**: เพิ่มความเร็วเว็บไซต์

### 🚀 **ค่าของ loading attribute**

#### **1. `loading="lazy"` - โหลดเมื่อจำเป็น**

```html
<!-- โหลดเมื่อใกล้จะปรากฏในหน้าจอ -->
<img src="image-below-fold.jpg" alt="รูปภาพด้านล่าง" loading="lazy" />

<!-- เหมาะสำหรับรูปที่อยู่ด้านล่างของหน้า -->
<img
  src="footer-image.jpg"
  alt="รูปภาพ footer"
  loading="lazy"
  width="300"
  height="200"
/>
```

#### **2. `loading="eager"` - โหลดทันที (ค่าเริ่มต้น)**

```html
<!-- โหลดทันทีแม้ยังไม่เห็น -->
<img src="hero-image.jpg" alt="รูปหลัก" loading="eager" />

<!-- ใช้สำหรับรูปสำคัญที่ต้องเห็นทันที -->
<img src="logo.png" alt="โลโก้" loading="eager" />
```

### 🎯 **การใช้งาน Lazy Loading อย่างถูกต้อง**

#### **1. รูปที่ควรใช้ lazy loading**

```html
<!-- รูปภาพในเนื้อหาบทความ -->
<img src="content-image-1.jpg" alt="ภาพประกอบบทความ" loading="lazy" />

<!-- รูปภาพในแกลเลอรี่ -->
<img src="gallery-photo-10.jpg" alt="รูปภาพที่ 10" loading="lazy" />

<!-- รูปภาพผลิตภัณฑ์ที่อยู่ด้านล่าง -->
<img src="product-details.jpg" alt="รายละเอียดสินค้า" loading="lazy" />

<!-- รูปภาพใน footer -->
<img src="partner-logos.jpg" alt="โลโก้พาร์ทเนอร์" loading="lazy" />
```

#### **2. รูปที่ไม่ควรใช้ lazy loading**

```html
<!-- รูปหลักที่ต้องเห็นทันที -->
<img src="hero-banner.jpg" alt="แบนเนอร์หลัก" loading="eager" />

<!-- โลโก้ -->
<img src="logo.svg" alt="โลโก้บริษัท" />

<!-- รูปที่อยู่ "above the fold" (เห็นทันทีที่เปิดหน้า) -->
<img src="featured-product.jpg" alt="สินค้าแนะนำ" />
```

### 📊 **ประโยชน์ของ Lazy Loading**

#### **1. ลดเวลาโหลดหน้าเริ่มต้น**

```html
<!-- แทนที่จะโหลดรูป 50 รูปพร้อมกัน -->
<!-- จะโหลดเฉพาะรูปที่เห็นก่อน -->

<div class="product-grid">
  <img src="product-1.jpg" alt="สินค้า 1" />
  <!-- โหลดทันที -->
  <img src="product-2.jpg" alt="สินค้า 2" />
  <!-- โหลดทันที -->
  <img src="product-3.jpg" alt="สินค้า 3" loading="lazy" />
  <!-- โหลดเมื่อจำเป็น -->
  <img src="product-4.jpg" alt="สินค้า 4" loading="lazy" />
  <!-- ... -->
</div>
```

#### **2. ประหยัด Bandwidth**

```html
<!-- ผู้ใช้ที่ไม่เลื่อนลงจะไม่โหลดรูปด้านล่าง -->
<section class="hero">
  <img src="main-banner.jpg" alt="แบนเนอร์หลัก" />
</section>

<section class="content">
  <!-- รูปเหล่านี้โหลดเมื่อจำเป็น -->
  <img src="article-image-1.jpg" alt="ภาพประกอบ 1" loading="lazy" />
  <img src="article-image-2.jpg" alt="ภาพประกอบ 2" loading="lazy" />
</section>
```

---

## 6. Attributes อื่นๆ ที่สำคัญ

### 📝 **Attributes เพิ่มเติม**

#### **1. `title` - คำอธิบายเพิ่มเติม**

```html
<!-- แสดง tooltip เมื่อ hover -->
<img
  src="complex-chart.png"
  alt="กราฟยอดขาย"
  title="คลิกเพื่อดูรายละเอียดเพิ่มเติม"
/>

<!-- ข้อมูลเพิ่มเติมสำหรับรูปศิลปะ -->
<img
  src="painting.jpg"
  alt="ภาพวาดสีน้ำ"
  title="วาดโดย นายกรรม ศิลปิน เมื่อปี 2023"
/>
```

#### **2. `class` และ `id` - สำหรับ CSS และ JavaScript**

```html
<!-- ใช้กับ CSS -->
<img src="product.jpg" alt="สินค้า" class="product-image" id="main-product" />

<style>
  .product-image {
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease;
  }

  .product-image:hover {
    transform: scale(1.05);
  }

  #main-product {
    border: 2px solid #007bff;
  }
</style>
```

#### **3. `srcset` - รูปภาพหลายขนาด**

```html
<!-- รูปภาพสำหรับ responsive design -->
<img
  src="image-800w.jpg"
  srcset="image-400w.jpg 400w, image-800w.jpg 800w, image-1200w.jpg 1200w"
  sizes="(max-width: 768px) 400px, 800px"
  alt="รูปภาพ responsive"
/>
```

#### **4. `crossorigin` - การโหลดจากโดเมนอื่น**

```html
<!-- โหลดรูปจากโดเมนอื่นอย่างปลอดภัย -->
<img
  src="https://cdn.example.com/image.jpg"
  alt="รูปจาก CDN"
  crossorigin="anonymous"
/>
```

#### **5. `decoding` - การถอดรหัสรูปภาพ**

```html
<!-- ถอดรหัสแบบ async (ไม่บล็อก UI) -->
<img src="large-image.jpg" alt="รูปขนาดใหญ่" decoding="async" />

<!-- ถอดรหัสแบบ sync (รอให้เสร็จก่อน) -->
<img src="critical-image.jpg" alt="รูปสำคัญ" decoding="sync" />
```

---

## 7. Responsive Images และ Performance

### 📱 **Responsive Images**

#### **1. CSS สำหรับ Responsive**

```html
<img src="responsive.jpg" alt="รูป responsive" class="responsive-image" />

<style>
  .responsive-image {
    max-width: 100%;
    height: auto;
    display: block;
  }

  /* สำหรับ container เฉพาะ */
  .image-container {
    width: 100%;
    max-width: 600px;
  }

  .image-container img {
    width: 100%;
    height: auto;
  }
</style>
```

#### **2. Picture Element สำหรับ Art Direction**

```html
<picture>
  <!-- Mobile: รูปแนวตั้ง -->
  <source media="(max-width: 768px)" srcset="mobile-portrait.jpg" />

  <!-- Desktop: รูปแนวนอน -->
  <source media="(min-width: 769px)" srcset="desktop-landscape.jpg" />

  <!-- Fallback -->
  <img src="default.jpg" alt="รูปภาพ responsive" />
</picture>
```

#### **3. Object-fit สำหรับควบคุมการแสดงผล**

```html
<img src="photo.jpg" alt="รูปภาพ" class="fitted-image" />

<style>
  .fitted-image {
    width: 300px;
    height: 200px;
    object-fit: cover; /* ครอบคลุมพื้นที่โดยตัดส่วนเกิน */
    /* object-fit: contain; ใส่ให้พอดีโดยไม่ตัด */
    /* object-fit: fill; ยืดให้เต็มพื้นที่ */
  }
</style>
```

### 🚀 **Performance Optimization**

#### **1. Image Formats ที่เหมาะสม**

```html
<!-- WebP สำหรับเบราว์เซอร์ใหม่ -->
<picture>
  <source srcset="photo.webp" type="image/webp" />
  <source srcset="photo.jpg" type="image/jpeg" />
  <img src="photo.jpg" alt="รูปภาพ" />
</picture>

<!-- AVIF สำหรับเบราว์เซอร์ที่รองรับ -->
<picture>
  <source srcset="photo.avif" type="image/avif" />
  <source srcset="photo.webp" type="image/webp" />
  <img src="photo.jpg" alt="รูปภาพ" />
</picture>
```

#### **2. การบีบอัดและขนาดที่เหมาะสม**

```html
<!-- ขนาดแตกต่างกันสำหรับอุปกรณ์ต่างๆ -->
<img
  src="image-800w.jpg"
  srcset="
    image-400w.jpg   400w,
    image-800w.jpg   800w,
    image-1200w.jpg 1200w,
    image-1600w.jpg 1600w
  "
  sizes="
    (max-width: 480px) 400px,
    (max-width: 768px) 800px,
    (max-width: 1200px) 1200px,
    1600px
  "
  alt="รูปภาพ responsive"
  loading="lazy"
/>
```

#### **3. Critical Images vs Non-Critical Images**

```html
<!-- Critical: โหลดทันที -->
<img src="hero-banner.jpg" alt="แบนเนอร์หลัก" loading="eager" />
<img src="logo.svg" alt="โลโก้" />

<!-- Non-Critical: lazy load -->
<img src="content-image.jpg" alt="เนื้อหา" loading="lazy" />
<img src="gallery-photo.jpg" alt="แกลเลอรี่" loading="lazy" />
```

---

## 8. การใช้รูปภาพในบริบทต่างๆ

### 🛍️ **E-commerce**

```html
<!-- รูปสินค้าหลัก -->
<img
  src="iphone-main.jpg"
  alt="iPhone 15 Pro Max 256GB สีทิไทเนียมธรรมชาติ หน้าจอ 6.7 นิ้ว"
  width="500"
  height="500"
  loading="eager"
/>

<!-- รูปสินค้าเพิ่มเติม -->
<img
  src="iphone-back.jpg"
  alt="iPhone 15 Pro Max ด้านหลัง แสดงกล้อง 3 ตัว และโลโก้ Apple"
  width="200"
  height="200"
  loading="lazy"
/>

<!-- รูปแสดงขนาด -->
<img
  src="iphone-size-comparison.jpg"
  alt="เปรียบเทียบขนาด iPhone 15 Pro Max กับ iPhone 14 Pro Max"
  loading="lazy"
/>
```

### 📰 **Blog/News**

```html
<!-- รูปหลักของบทความ -->
<img
  src="article-hero.jpg"
  alt="นักเดินทางยืนชมวิวพระอาทิตย์ขึ้นบนยอดดอยอินทนนท์"
  width="800"
  height="400"
  loading="eager"
/>

<!-- รูปประกอบในเนื้อหา -->
<img
  src="travel-tip-1.jpg"
  alt="การเตรียมอุปกรณ์เดินป่า: เป้สะพาย ไฟฉาย น้ำดื่ม และแผนที่"
  loading="lazy"
/>

<!-- รูปโปรไฟล์ผู้เขียน -->
<img
  src="author-profile.jpg"
  alt="นายสมชาย ใจดี นักเดินทางและนักเขียน"
  width="60"
  height="60"
  class="author-avatar"
/>
```

### 🏢 **Corporate Website**

```html
<!-- รูปทีมงาน -->
<img
  src="team-photo.jpg"
  alt="ทีมงาน ABC Company ยืนยิ้มหน้าอาคารสำนักงาน 15 คน"
  loading="lazy"
/>

<!-- รูปผลงาน -->
<img
  src="project-showcase.jpg"
  alt="โปรเจกต์พัฒนาแอปพลิเคชันธนาคารออนไลน์ แสดงหน้าจอบนมือถือ"
  loading="lazy"
/>

<!-- รูปโลโก้ลูกค้า -->
<img
  src="client-logo-microsoft.png"
  alt="Microsoft - ลูกค้าของเรา"
  width="120"
  height="40"
  loading="lazy"
/>
```

### 🍕 **Restaurant/Food**

```html
<!-- รูปเมนูอาหาร -->
<img
  src="pizza-margherita.jpg"
  alt="พิซซ่ามาการิต้า โรยชีสมอซซาเรลล่า ใบโหระพา มะเขือเทศสด"
  width="300"
  height="300"
  loading="lazy"
/>

<!-- รูปร้านอาหาร -->
<img
  src="restaurant-interior.jpg"
  alt="บรรยากาศภายในร้าน โต๊ะไม้ แสงไฟอบอุ่น ตกแต่งสไตล์อิตาเลียน"
  loading="lazy"
/>
```

---

## 9. Accessibility และ SEO Best Practices

### ♿ **Accessibility Guidelines**

#### **1. Alt text ที่เป็นมิตรกับ Screen Reader**

```html
<!-- ✅ ดี - อธิบายเนื้อหาและบริบท -->
<img
  src="weather-chart.png"
  alt="กราฟแสดงอุณหภูมิรายวัน: จันทร์ 28°C อังคาร 30°C พุธ 32°C พฤหัสฯ 29°C"
/>

<!-- ❌ ไม่ดี - ไม่ให้ข้อมูลเพียงพอ -->
<img src="weather-chart.png" alt="กราฟอากาศ" />
```

#### **2. การใช้ Empty Alt สำหรับรูปประกอบ**

```html
<!-- รูปประกอบที่ไม่ให้ข้อมูลเพิ่ม -->
<div class="article">
  <h2>วิธีการทำเค้ก</h2>
  <img src="decorative-border.png" alt="" role="presentation" />
  <p>วิธีทำเค้กช็อกโกแลต...</p>
</div>
```

#### **3. Long Description สำหรับรูปซับซ้อน**

```html
<!-- รูปที่มีข้อมูลซับซ้อน -->
<img
  src="complex-infographic.png"
  alt="อินโฟกราฟิกแสดงสถิติการใช้อินเทอร์เน็ตในไทย"
  longdesc="#infographic-description"
/>

<div id="infographic-description">
  <h3>รายละเอียดอินโฟกราฟิก</h3>
  <p>ผู้ใช้อินเทอร์เน็ตในไทย 2024:</p>
  <ul>
    <li>กรุงเทพฯ: 85% ของประชากร</li>
    <li>ภาคเหนือ: 72% ของประชากร</li>
    <li>ภาคใต้: 68% ของประชากร</li>
  </ul>
</div>
```

### 🔍 **SEO Best Practices**

#### **1. File Names ที่มีความหมาย**

```html
<!-- ✅ ดี - ชื่อไฟล์อธิบายเนื้อหา -->
<img src="iphone-15-pro-max-review.jpg" alt="รีวิว iPhone 15 Pro Max" />

<!-- ❌ ไม่ดี - ชื่อไฟล์ไม่มีความหมาย -->
<img src="IMG_1234.jpg" alt="รีวิว iPhone 15 Pro Max" />
```

#### **2. Alt text ที่เหมาะสมกับ SEO**

```html
<!-- ใส่คำสำคัญตามธรรมชาติ -->
<img
  src="wordpress-tutorial-beginners.jpg"
  alt="คู่มือเรียน WordPress สำหรับมือใหม่ ตั้งแต่ติดตั้งจนทำเว็บไซต์"
/>

<!-- อย่ายัดคำสำคัญ -->
<!-- ❌ alt="WordPress WordPress ติดตั้ง WordPress เรียน WordPress" -->
```

#### **3. Image Sitemap**

```html
<!-- เพิ่มรูปภาพใน sitemap เพื่อ SEO -->
<!-- sitemap.xml -->
<url>
  <loc>https://example.com/article/</loc>
  <image:image>
    <image:loc>https://example.com/images/main-photo.jpg</image:loc>
    <image:caption>คำอธิบายรูปภาพสำหรับ Google</image:caption>
    <image:title>ชื่อรูปภาพ</image:title>
  </image:image>
</url>
```

---

## 10. การ Debug และแก้ไขปัญหา

### 🐛 **ปัญหาที่พบบ่อย**

#### **1. รูปภาพไม่แสดง**

```html
<!-- ตรวจสอบปัญหาเหล่านี้ -->

<!-- ❌ Path ผิด -->
<img src="imges/photo.jpg" alt="รูปภาพ" />
<!-- แก้: "images" ไม่ใช่ "imges" -->

<!-- ❌ ไฟล์ไม่มีจริง -->
<img src="images/nonexistent.jpg" alt="รูปภาพ" />

<!-- ❌ Case sensitivity (Linux/Mac) -->
<img src="images/Photo.JPG" alt="รูปภาพ" />
<!-- แก้: ตรวจสอบตัวพิมพ์เล็ก-ใหญ่ -->

<!-- ✅ ถูกต้อง -->
<img src="images/photo.jpg" alt="รูปภาพ" />
```

#### **2. รูปภาพบิดเบี้ยว**

```html
<!-- ❌ ไม่รักษาสัดส่วน -->
<img src="photo.jpg" alt="รูปภาพ" width="300" height="100" />

<!-- ✅ รักษาสัดส่วนด้วย CSS -->
<img src="photo.jpg" alt="รูปภาพ" width="300" style="height: auto;" />
```

#### **3. รูปภาพโหลดช้า**

```html
<!-- ปัญหา: รูปขนาดใหญ่เกิน -->
<!-- แก้: บีบอัดรูป หรือใช้ lazy loading -->

<img
  src="optimized-image.webp"
  alt="รูปที่ปรับขนาดแล้ว"
  loading="lazy"
  width="800"
  height="600"
/>
```

### 🔧 **เครื่องมือตรวจสอบ**

#### **1. Browser Developer Tools**

```html
<!-- เปิด Dev Tools (F12) และตรวจสอบ -->
<!-- Network tab: ดูการโหลดรูปภาพ -->
<!-- Elements tab: ตรวจสอบ HTML และ CSS -->
<!-- Console: ดู error messages -->
```

#### **2. Accessibility Tools**

```html
<!-- WAVE Web Accessibility Evaluator -->
<!-- axe DevTools -->
<!-- Lighthouse Accessibility Audit -->
```

#### **3. SEO Tools**

```html
<!-- Google PageSpeed Insights -->
<!-- GTmetrix -->
<!-- Screaming Frog SEO Spider -->
```

---

## 11. Best Practices สรุป

### ✅ **แนวทางปฏิบัติที่ดี**

#### **1. Alt Text**

```html
<!-- ✅ สิ่งที่ควรทำ -->
<img src="product.jpg" alt="สมาร์ทโฟน Samsung Galaxy S24 สีม่วง 256GB" />

<!-- ❌ สิ่งที่ไม่ควรทำ -->
<img src="product.jpg" alt="รูปสินค้า" />
<img src="product.jpg" />
<!-- ไม่มี alt -->
```

#### **2. Performance**

```html
<!-- ✅ ปรับปรุงประสิทธิภาพ -->
<img
  src="optimized.webp"
  alt="รูปภาพ"
  width="400"
  height="300"
  loading="lazy"
/>

<!-- ❌ ไม่เอาใจใส่ประสิทธิภาพ -->
<img src="huge-unoptimized.png" alt="รูปภาพ" />
```

#### **3. Responsive**

```html
<!-- ✅ รองรับทุกอุปกรณ์ -->
<img src="responsive.jpg" alt="รูปภาพ" style="max-width: 100%; height: auto;" />

<!-- ❌ ไม่ responsive -->
<img src="fixed.jpg" alt="รูปภาพ" width="800" />
```

### 📋 **Checklist สำหรับรูปภาพ**

- [ ] มี `alt` attribute ที่อธิบายได้ชัดเจน
- [ ] ใช้ `alt=""` สำหรับรูปประกอบ
- [ ] กำหนด `width` และ `height` เพื่อป้องกัน layout shift
- [ ] ใช้ `loading="lazy"` สำหรับรูปที่ไม่สำคัญ
- [ ] เลือกรูปแบบไฟล์ที่เหมาะสม (WebP, AVIF)
- [ ] บีบอัดรูปให้เหมาะสม
- [ ] ตรวจสอบการทำงานบนมือถือ
- [ ] ทดสอบกับ screen reader
- [ ] ใช้ชื่อไฟล์ที่มีความหมาย
- [ ] ทดสอบความเร็วการโหลด

### 🎯 **สรุปสำคัญ**

1. **Alt attribute** คือสิ่งสำคัญที่สุด - ต้องมีและต้องอธิบายได้ชัดเจน
2. **Performance** สำคัญ - ใช้ lazy loading และบีบอัดรูป
3. **Responsive** จำเป็น - ต้องแสดงผลดีในทุกอุปกรณ์
4. **Accessibility** ต้องคำนึงถึง - เป็นมิตรกับผู้พิการ
5. **SEO** ช่วยได้ - Alt text และชื่อไฟล์ที่ดีช่วย ranking

การใช้รูปภาพอย่างถูกต้องจะช่วยให้เว็บไซต์มีประสิทธิภาพ เข้าถึงได้ และเป็นมิตรกับผู้ใช้ทุกกลุ่ม
