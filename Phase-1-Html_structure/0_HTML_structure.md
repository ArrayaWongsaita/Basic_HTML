# โครงสร้าง HTML5 (HTML5 Structure)

## โครงสร้างพื้นฐานของ HTML5

### 📋 โครงสร้างมาตรฐาน HTML5

```html
<!DOCTYPE html>
<html lang="th">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>ชื่อหน้าเว็บ</title>
  </head>
  <body>
    <!-- เนื้อหาหน้าเว็บ -->
  </body>
</html>
```

## การวิเคราะห์โครงสร้างแต่ละส่วน

### 1. **DOCTYPE Declaration**

```html
<!DOCTYPE html>
```

- **หน้าที่**: บอก browser ว่าใช้ HTML5
- **จำเป็น**: ต้องมีเสมอ บรรทัดแรก
- **เปรียบเทียบ**: HTML4 ใช้ `<!DOCTYPE HTML PUBLIC...` (ยาวมาก)

### 2. **HTML Element**

```html
<html lang="th">
  <!-- เนื้อหาทั้งหมด -->
</html>
```

- **หน้าที่**: element รากของเอกสาร
- **lang attribute**: ระบุภาษา (th=ไทย, en=อังกฤษ)
- **ประโยชน์**: ช่วย screen readers และ SEO

### 3. **HEAD Section**

```html
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="description" content="คำอธิบายหน้าเว็บ" />
  <title>ชื่อหน้าเว็บ</title>
  <link rel="stylesheet" href="style.css" />
  <script src="script.js"></script>
</head>
```

#### 3.1 **Meta Tags สำคัญ**

```html
<!-- การเข้ารหัสตัวอักษร -->
<meta charset="UTF-8" />

<!-- การแสดงผลบนมือถือ -->
<meta name="viewport" content="width=device-width, initial-scale=1.0" />

<!-- คำอธิบายสำหรับ SEO -->
<meta name="description" content="คำอธิบายหน้าเว็บไม่เกิน 160 ตัวอักษร" />

<!-- คำสำคัญ (ไม่แนะนำแล้ว) -->
<meta name="keywords" content="html, css, javascript" />

<!-- ผู้เขียน -->
<meta name="author" content="ชื่อผู้เขียน" />
```

##### **การอธิบาย Meta Tags แต่ละตัวอย่างละเอียด**

###### 🔤 **Meta Charset**

```html
<meta charset="UTF-8" />
```

- **หน้าที่**: กำหนดการเข้ารหัสตัวอักษรของเอกสาร
- **UTF-8**: รองรับตัวอักษรทุกภาษาในโลก รวมทั้งภาษาไทย
- **ความสำคัญ**: ป้องกันตัวอักษรแสดงผลผิด (เช่น ภาษาไทยเป็นสัญลักษณ์แปลกๆ)
- **ตำแหน่ง**: ต้องอยู่ใน 1024 bytes แรกของไฟล์ HTML
- **ตัวเลือกอื่น**: ISO-8859-1, Windows-1252 (ไม่แนะนำ)

**ตัวอย่างปัญหาหากไม่มี charset:**

```html
<!-- ❌ ไม่มี charset -->
<head>
  <title>สวัสดี</title>
</head>
<!-- ผลลัพธ์: àÊÇÑÊ´Õ -->

<!-- ✅ มี charset -->
<head>
  <meta charset="UTF-8" />
  <title>สวัสดี</title>
</head>
<!-- ผลลัพธ์: สวัสดี -->
```

###### 📱 **Meta Viewport**

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

- **หน้าที่**: ควบคุมการแสดงผลบนอุปกรณ์มือถือ
- **width=device-width**: กำหนดความกว้างให้เท่ากับความกว้างของหน้าจอ
- **initial-scale=1.0**: กำหนดระดับการซูมเริ่มต้นเป็น 100%
- **ความสำคัญ**: จำเป็นสำหรับ Responsive Web Design

**ตัวเลือกเพิ่มเติม:**

```html
<!-- ควบคุมการซูม -->
<meta
  name="viewport"
  content="width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=2.0"
/>

<!-- ป้องกันการซูม -->
<meta
  name="viewport"
  content="width=device-width, initial-scale=1.0, user-scalable=no"
/>

<!-- กำหนดความกว้างเฉพาะ -->
<meta name="viewport" content="width=320" />
```

**ความแตกต่างของการมี/ไม่มี viewport:**

```html
<!-- ❌ ไม่มี viewport -->
<!-- เว็บแสดงผลเล็กมากบนมือถือ ต้องซูมเพื่อดู -->

<!-- ✅ มี viewport -->
<!-- เว็บแสดงผลขนาดพอดีกับหน้าจอมือถือ -->
```

###### 🔍 **Meta Description**

```html
<meta name="description" content="คำอธิบายหน้าเว็บไม่เกิน 160 ตัวอักษร" />
```

- **หน้าที่**: อธิบายเนื้อหาของหน้าเว็บสำหรับ Search Engines
- **ความยาว**: 150-160 ตัวอักษร (Google แสดงได้ประมาณ 160 ตัวอักษร)
- **การใช้งาน**: แสดงใน Google Search Results
- **ความสำคัญ**: ช่วยเพิ่ม Click-through Rate (CTR)

**ตัวอย่างที่ดี:**

```html
<!-- ✅ ดี - อธิบายชัดเจน, มีคำสำคัญ -->
<meta
  name="description"
  content="เรียนรู้ HTML5 ฟรี พร้อมตัวอย่างโค้ด เทคนิคการพัฒนาเว็บไซต์สำหรับมือใหม่ บทเรียนภาษาไทยง่ายต่อการเข้าใจ"
/>

<!-- ❌ ไม่ดี - สั้นเกินไป -->
<meta name="description" content="เรียน HTML" />

<!-- ❌ ไม่ดี - ยาวเกินไป -->
<meta
  name="description"
  content="เรียนรู้การพัฒนาเว็บไซต์ด้วย HTML5 CSS3 JavaScript jQuery Bootstrap React Angular Vue.js Node.js Express MongoDB MySQL..."
/>
```

###### 🏷️ **Meta Keywords (ไม่แนะนำแล้ว)**

```html
<meta name="keywords" content="html, css, javascript" />
```

- **สถานะ**: Google ไม่ใช้แล้วตั้งแต่ปี 2009
- **เหตุผล**: ถูกใช้ในทางที่ผิด (Keyword Stuffing)
- **ข้อแนะนำ**: ไม่จำเป็นต้องใช้ หรือใช้เฉพาะ Search Engines อื่นๆ
- **ทางเลือก**: โฟกัสที่เนื้อหาคุณภาพและ meta description

###### 👤 **Meta Author**

```html
<meta name="author" content="ชื่อผู้เขียน" />
```

- **หน้าที่**: ระบุผู้เขียนหรือผู้สร้างหน้าเว็บ
- **การใช้งาน**: ไม่ส่งผลต่อ SEO โดยตรง
- **ประโยชน์**: ช่วยในการติดตามลิขสิทธิ์และการติดต่อ

**Meta Tags เพิ่มเติมที่สำคัญ:**

###### 🌐 **Open Graph (Facebook)**

```html
<!-- สำหรับการแชร์บน Facebook -->
<meta property="og:title" content="ชื่อหน้าเว็บ" />
<meta property="og:description" content="คำอธิบายสำหรับ Social Media" />
<meta property="og:image" content="https://example.com/image.jpg" />
<meta property="og:url" content="https://example.com/page" />
<meta property="og:type" content="website" />
<meta property="og:site_name" content="ชื่อเว็บไซต์" />
```

###### 🐦 **Twitter Card**

```html
<!-- สำหรับการแชร์บน Twitter -->
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:title" content="ชื่อหน้าเว็บ" />
<meta name="twitter:description" content="คำอธิบาย" />
<meta name="twitter:image" content="https://example.com/image.jpg" />
<meta name="twitter:site" content="@username" />
```

###### 🤖 **Robots**

```html
<!-- ควบคุมการทำงานของ Search Engine Robots -->
<meta name="robots" content="index, follow" />
<meta name="robots" content="noindex, nofollow" />
<meta name="robots" content="index, nofollow" />
<meta name="robots" content="noindex, follow" />
```

###### 🔄 **Refresh**

```html
<!-- รีเฟรชหน้าอัตโนมัติ (ไม่แนะนำ) -->
<meta http-equiv="refresh" content="30" />

<!-- เปลี่ยนเส้นทางอัตโนมัติ -->
<meta http-equiv="refresh" content="5; url=https://newsite.com" />
```

###### 📱 **Mobile Specific**

```html
<!-- สำหรับ iOS -->
<meta name="apple-mobile-web-app-capable" content="yes" />
<meta name="apple-mobile-web-app-status-bar-style" content="black" />
<meta name="apple-mobile-web-app-title" content="ชื่อแอป" />

<!-- สำหรับ Android -->
<meta name="mobile-web-app-capable" content="yes" />
<meta name="theme-color" content="#000000" />
```

###### 🔒 **Security**

```html
<!-- Content Security Policy -->
<meta http-equiv="Content-Security-Policy" content="default-src 'self'" />

<!-- X-Frame-Options -->
<meta http-equiv="X-Frame-Options" content="DENY" />
```

##### **ตัวอย่าง Meta Tags แบบสมบูรณ์**

```html
<head>
  <!-- พื้นฐาน -->
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>บทเรียน HTML5 - เว็บไซต์เรียนรู้ฟรี</title>

  <!-- SEO -->
  <meta
    name="description"
    content="เรียนรู้ HTML5 ฟรี พร้อมตัวอย่างโค้ด เทคนิคการพัฒนาเว็บไซต์สำหรับมือใหม่ บทเรียนภาษาไทย"
  />
  <meta name="author" content="ครูนนท์" />
  <meta name="robots" content="index, follow" />

  <!-- Open Graph -->
  <meta property="og:title" content="บทเรียน HTML5 - เว็บไซต์เรียนรู้ฟรี" />
  <meta
    property="og:description"
    content="เรียนรู้ HTML5 ฟรี พร้อมตัวอย่างโค้ด เทคนิคการพัฒนาเว็บไซต์"
  />
  <meta property="og:image" content="https://example.com/html5-course.jpg" />
  <meta property="og:url" content="https://example.com/html5-course" />
  <meta property="og:type" content="article" />

  <!-- Twitter Card -->
  <meta name="twitter:card" content="summary_large_image" />
  <meta name="twitter:title" content="บทเรียน HTML5 ฟรี" />
  <meta name="twitter:description" content="เรียนรู้ HTML5 พร้อมตัวอย่างโค้ด" />
  <meta name="twitter:image" content="https://example.com/html5-course.jpg" />

  <!-- Mobile -->
  <meta name="theme-color" content="#3498db" />
  <meta name="apple-mobile-web-app-capable" content="yes" />

  <!-- Links -->
  <link rel="icon" href="/favicon.ico" />
  <link rel="canonical" href="https://example.com/html5-course" />
</head>
```

#### 3.2 **Elements สำหรับเชื่อมโยงและจัดรูปแบบ**

##### 🔗 **Link Element**

```html
<link rel="stylesheet" href="style.css" />
<link rel="icon" href="favicon.ico" />
<link rel="canonical" href="https://example.com/page" />
```

- **หน้าที่**: เชื่อมโยงไฟล์ภายนอกเข้ากับหน้าเว็บ
- **ตำแหน่ง**: ใช้ใน `<head>` เท่านั้น
- **ความสำคัญ**: ไม่แสดงเนื้อหาโดยตรง แต่ส่งผลต่อการทำงานของหน้าเว็บ

**ประเภทการใช้งาน link:**

###### **CSS Stylesheet**

```html
<!-- เชื่อมโยงไฟล์ CSS -->
<link rel="stylesheet" href="css/style.css" />
<link rel="stylesheet" href="css/responsive.css" />

<!-- เชื่อมโยง CSS จาก CDN -->
<link
  rel="stylesheet"
  href="https://cdnjs.cloudflare.com/ajax/libs/bootstrap/5.3.0/css/bootstrap.min.css"
/>
```

###### **Favicon (ไอคอนเว็บไซต์)**

```html
<!-- Favicon พื้นฐาน -->
<link rel="icon" href="/favicon.ico" />
<link rel="icon" type="image/png" href="/favicon.png" />

<!-- Favicon สำหรับอุปกรณ์ต่างๆ -->
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png" />
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png" />
<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png" />
```

###### **SEO และ Navigation**

```html
<!-- URL หลักของหน้า (ป้องกัน Duplicate Content) -->
<link rel="canonical" href="https://example.com/page" />

<!-- หน้าก่อนหน้า/หน้าถัดไป -->
<link rel="prev" href="https://example.com/page1" />
<link rel="next" href="https://example.com/page3" />

<!-- DNS Prefetch (เพิ่มความเร็ว) -->
<link rel="dns-prefetch" href="//fonts.googleapis.com" />
```

##### 🎨 **Style Element**

```html
<style>
  body {
    font-family: Arial, sans-serif;
    background-color: #f5f5f5;
  }

  h1 {
    color: #333;
    text-align: center;
  }
</style>
```

- **หน้าที่**: เขียน CSS โดยตรงในหน้าเว็บ
- **ตำแหน่ง**: ใช้ใน `<head>` หรือ `<body>` ก็ได้ (แนะนำใน head)
- **การใช้งาน**: CSS เฉพาะหน้านี้เท่านั้น

**ตัวอย่างการใช้งาน Style:**

###### **CSS Reset/Normalize**

```html
<style>
  /* CSS Reset พื้นฐาน */
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body {
    font-family: 'Sarabun', sans-serif;
    line-height: 1.6;
  }
</style>
```

###### **Critical CSS (สำคัญ)**

```html
<style>
  /* CSS สำคัญที่ต้องโหลดก่อน */
  .header {
    background: #333;
    color: white;
    padding: 1rem;
  }

  .loading {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }
</style>
```

##### ⚡ **Script Element**

```html
<script src="script.js"></script>
<script>
  console.log('Hello World!');
  alert('ยินดีต้อนรับ!');
</script>
```

- **หน้าที่**: เชื่อมโยงหรือเขียน JavaScript
- **ตำแหน่ง**: ใช้ใน `<head>` หรือ `<body>` (แนะนำก่อนปิด body)
- **การทำงาน**: เพิ่มความสามารถและการโต้ตอบให้เว็บไซต์

**ประเภทการใช้งาน Script:**

###### **External JavaScript**

```html
<!-- JavaScript ไฟล์ภายนอก -->
<script src="js/main.js"></script>
<script src="js/utils.js"></script>

<!-- JavaScript จาก CDN -->
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
```

###### **Inline JavaScript**

```html
<script>
  // JavaScript เบื้องต้น
  function sayHello() {
    alert('สวัสดี!');
  }

  // เมื่อหน้าเว็บโหลดเสร็จ
  document.addEventListener('DOMContentLoaded', function () {
    console.log('หน้าเว็บพร้อมใช้งาน');
  });
</script>
```

###### **Script Attributes สำคัญ**

```html
<!-- โหลดแบบ Async (ไม่รอ) -->
<script async src="analytics.js"></script>

<!-- โหลดแบบ Defer (รอ HTML เสร็จก่อน) -->
<script defer src="main.js"></script>

<!-- ระบุ Type -->
<script type="text/javascript" src="script.js"></script>
<script type="module" src="module.js"></script>
```

##### **ลำดับการโหลดและ Performance**

###### **📍 ตำแหน่งที่แนะนำ**

```html
<head>
  <!-- CSS ควรอยู่ใน head -->
  <link rel="stylesheet" href="style.css" />

  <!-- Critical CSS -->
  <style>
    /* CSS สำคัญ */
  </style>

  <!-- JavaScript ที่จำเป็นต้องโหลดก่อน -->
  <script src="critical.js"></script>
</head>
<body>
  <!-- เนื้อหา HTML -->

  <!-- JavaScript ทั่วไปควรอยู่ก่อนปิด body -->
  <script src="main.js"></script>
  <script>
    // JavaScript เพิ่มเติม
  </script>
</body>
```

###### **⚡ เทคนิคเพิ่มความเร็ว**

```html
<head>
  <!-- Preload ไฟล์สำคัญ -->
  <link rel="preload" href="style.css" as="style" />
  <link rel="preload" href="main.js" as="script" />

  <!-- Prefetch ไฟล์ที่อาจใช้ภายหลัง -->
  <link rel="prefetch" href="next-page.css" />

  <!-- DNS Prefetch -->
  <link rel="dns-prefetch" href="//fonts.googleapis.com" />
</head>
```

##### **ตัวอย่างการใช้งานรวม**

```html
<!DOCTYPE html>
<html lang="th">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>ตัวอย่างการใช้ Link, Style, Script</title>

    <!-- Favicon -->
    <link rel="icon" href="/favicon.ico" />

    <!-- CSS External -->
    <link rel="stylesheet" href="css/style.css" />

    <!-- Critical CSS -->
    <style>
      body {
        font-family: 'Sarabun', sans-serif;
        margin: 0;
        padding: 20px;
      }

      .header {
        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        color: white;
        padding: 2rem;
        text-align: center;
        border-radius: 10px;
      }
    </style>

    <!-- JavaScript ที่จำเป็น -->
    <script>
      // ตัวแปรสำคัญ
      const siteName = 'เว็บไซต์ตัวอย่าง';
    </script>
  </head>
  <body>
    <header class="header">
      <h1>ยินดีต้อนรับ</h1>
      <p>ตัวอย่างการใช้ Link, Style, Script</p>
    </header>

    <main>
      <button onclick="showMessage()">คลิกที่นี่</button>
    </main>

    <!-- JavaScript หลัก -->
    <script>
      function showMessage() {
        alert('สวัสดีจาก ' + siteName);
      }

      console.log('หน้าเว็บโหลดเสร็จแล้ว');
    </script>
  </body>
</html>
```

##### **❌ ข้อผิดพลาดที่พบบ่อย**

###### **1. ลำดับการโหลดผิด**

```html
<!-- ❌ ผิด - CSS หลัง JavaScript -->
<script src="main.js"></script>
<link rel="stylesheet" href="style.css" />

<!-- ✅ ถูก - CSS ก่อน JavaScript -->
<link rel="stylesheet" href="style.css" />
<script src="main.js"></script>
```

###### **2. Path ไฟล์ผิด**

```html
<!-- ❌ ผิด - Path ไม่ถูกต้อง -->
<link rel="stylesheet" href="style.css" />
<script src="script.js"></script>

<!-- ✅ ถูก - Path ชัดเจน -->
<link rel="stylesheet" href="css/style.css" />
<script src="js/script.js"></script>
```

###### **3. ลืม attributes สำคัญ**

```html
<!-- ❌ ผิด - ไม่มี rel ใน link -->
<link href="style.css" />

<!-- ✅ ถูก - มี rel -->
<link rel="stylesheet" href="style.css" />
```

<!-- ...existing code... -->
  <meta property="og:title" content="ชื่อสำหรับ Social Media" />
  <meta property="og:description" content="คำอธิบายสำหรับ Social Media" />
</head>
```

## ข้อผิดพลาดที่พบบ่อย

### ❌ **Common Mistakes**

#### 1. **ใช้ div แทน semantic elements**

```html
<!-- ❌ ไม่ดี -->
<div class="header">
  <div class="nav">
    <div class="main">
      <div class="footer">
        <!-- ✅ ดี -->
        <header>
          <nav>
            <main>
              <footer></footer>
            </main>
          </nav>
        </header>
      </div>
    </div>
  </div>
</div>
```

#### 2. **ลืม meta viewport**

```html
<!-- ❌ ขาด viewport -->
<head>
  <meta charset="UTF-8" />
  <title>ชื่อ</title>
</head>

<!-- ✅ ครบ -->
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>ชื่อ</title>
</head>
```

#### 3. **ใช้หลาย main elements**

```html
<!-- ❌ ผิด - main ซ้ำ -->
<main>เนื้อหาส่วน 1</main>
<main>เนื้อหาส่วน 2</main>

<!-- ✅ ถูก - main เดียว -->
<main>
  <section>เนื้อหาส่วน 1</section>
  <section>เนื้อหาส่วน 2</section>
</main>
```

## สรุป

### 🎯 **จุดสำคัญ**

1. **HTML5** มีโครงสร้างที่ง่ายกว่า HTML4
2. **Semantic Elements** ช่วย SEO และ Accessibility
3. **Meta tags** สำคัญสำหรับ responsive และ SEO
4. **DOCTYPE html** เพียงพอสำหรับ HTML5
5. **โครงสร้างที่ดี** ช่วยการพัฒนาและบำรุงรักษา

### 💡 **ข้อแนะนำ**

- ใช้ semantic elements แทน div เมื่อเป็นไปได้
- ตรวจสอบ HTML validation เสมอ
- ทดสอบบนอุปกรณ์และเบราว์เซอร์ต่างๆ
- เรียนรู้การใช้ DevTools ในการตรวจสอบโครงสร้าง

การเข้าใจโครงสร้าง HTML5 เป็นพื้นฐานสำคัญในการพัฒนาเว็บไซต์ที่ทันสมัยและมีคุณภาพ
