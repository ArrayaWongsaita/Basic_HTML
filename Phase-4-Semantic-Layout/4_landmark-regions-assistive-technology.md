# Landmark Regions สำหรับ Assistive Technology

## ภาพรวม

Landmark regions เป็นส่วนสำคัญของ Web Accessibility ที่ช่วยให้ผู้ใช้ที่พึ่งพา **Assistive Technology** (เช่น Screen Readers) สามารถนำทางและเข้าใจโครงสร้างเว็บไซต์ได้อย่างมีประสิทธิภาพ

### ประโยชน์หลัก

- **การนำทางที่รวดเร็ว**: ผู้ใช้สามารถข้ามไปยังส่วนต่างๆ ได้ทันที
- **ความเข้าใจโครงสร้าง**: เข้าใจว่าเนื้อหาแต่ละส่วนมีหน้าที่อะไร
- **ประสบการณ์ที่ดีขึ้น**: ลดเวลาในการค้นหาข้อมูล
- **มาตรฐาน WCAG**: ปฏิบัติตามแนวทางการเข้าถึง

---

## 1. Landmark Regions หลัก

### 1.1 Banner (`role="banner"`)

**คำอธิบาย**: ส่วนหัวหลักของเว็บไซต์ที่ปรากฏในทุกหน้า

**HTML Semantic**: `<header>` (เมื่ออยู่ใน `<body>` โดยตรง)

```html
<!-- Semantic HTML -->
<header>
  <div class="logo">
    <img src="logo.png" alt="โลโก้บริษัท ABC" />
    <h1>ABC Technology</h1>
  </div>
  <nav aria-label="เมนูหลัก">
    <ul>
      <li><a href="/">หน้าแรก</a></li>
      <li><a href="/about">เกี่ยวกับเรา</a></li>
      <li><a href="/services">บริการ</a></li>
    </ul>
  </nav>
</header>

<!-- หรือใช้ role attribute -->
<div role="banner">
  <h1>ชื่อเว็บไซต์</h1>
  <nav><!-- เมนูหลัก --></nav>
</div>
```

**เมื่อไหร่ควรใช้**:

- ส่วนหัวหลักของเว็บไซต์
- โลโก้และชื่อเว็บไซต์
- เมนูนำทางหลัก
- ข้อมูลติดต่อพื้นฐาน

### 1.2 Navigation (`role="navigation"`)

**คำอธิบาย**: ส่วนที่ประกอบด้วยลิงก์นำทาง

**HTML Semantic**: `<nav>`

```html
<!-- เมนูหลัก -->
<nav aria-label="เมนูหลัก">
  <ul>
    <li><a href="/" aria-current="page">หน้าแรก</a></li>
    <li><a href="/products">สินค้า</a></li>
    <li><a href="/about">เกี่ยวกับเรา</a></li>
  </ul>
</nav>

<!-- Breadcrumb navigation -->
<nav aria-label="breadcrumb">
  <ol>
    <li><a href="/">หน้าแรก</a></li>
    <li><a href="/products">สินค้า</a></li>
    <li aria-current="page">โทรศัพท์มือถือ</li>
  </ol>
</nav>

<!-- เมนูในหน้า -->
<nav aria-label="เมนูในหน้า">
  <h3>เนื้อหาในหน้านี้</h3>
  <ul>
    <li><a href="#section1">บทที่ 1</a></li>
    <li><a href="#section2">บทที่ 2</a></li>
  </ul>
</nav>

<!-- Navigation หลายอัน -->
<nav aria-label="ผลิตภัณฑ์">
  <ul>
    <li><a href="/products/web">เว็บไซต์</a></li>
    <li><a href="/products/mobile">แอพมือถือ</a></li>
  </ul>
</nav>

<nav aria-label="โซเชียลมีเดีย">
  <ul>
    <li><a href="https://facebook.com/company">Facebook</a></li>
    <li><a href="https://twitter.com/company">Twitter</a></li>
  </ul>
</nav>
```

### 1.3 Main (`role="main"`)

**คำอธิบาย**: เนื้อหาหลักของหน้า (ต้องมีเพียง 1 อันต่อหน้า)

**HTML Semantic**: `<main>`

```html
<main>
  <h1>หัวข้อหลักของหน้า</h1>

  <section>
    <h2>ส่วนที่ 1</h2>
    <p>เนื้อหาหลักของหน้า...</p>
  </section>

  <section>
    <h2>ส่วนที่ 2</h2>
    <p>เนื้อหาต่อ...</p>
  </section>
</main>

<!-- กับ skip link -->
<a href="#main" class="skip-link">ข้ามไปเนื้อหาหลัก</a>

<header><!-- header content --></header>

<main id="main">
  <!-- เนื้อหาหลัก -->
</main>
```

### 1.4 Complementary (`role="complementary"`)

**คำอธิบาย**: เนื้อหาเสริมที่เกี่ยวข้องกับเนื้อหาหลัก

**HTML Semantic**: `<aside>`

```html
<!-- Sidebar หลัก -->
<aside aria-label="ข้อมูลเสริม">
  <section>
    <h3>บทความยอดนิยม</h3>
    <ul>
      <li><a href="/popular-1">บทความ 1</a></li>
      <li><a href="/popular-2">บทความ 2</a></li>
    </ul>
  </section>

  <section>
    <h3>หมวดหมู่</h3>
    <ul>
      <li><a href="/category/tech">เทคโนโลยี</a></li>
      <li><a href="/category/design">ดีไซน์</a></li>
    </ul>
  </section>
</aside>

<!-- Aside ภายใน article -->
<article>
  <h2>หัวข้อบทความ</h2>
  <p>เนื้อหาบทความ...</p>

  <aside aria-label="ข้อมูลที่เกี่ยวข้อง">
    <h3>บทความที่เกี่ยวข้อง</h3>
    <ul>
      <li><a href="/related-1">บทความที่เกี่ยวข้อง 1</a></li>
    </ul>
  </aside>
</article>
```

### 1.5 Contentinfo (`role="contentinfo"`)

**คำอธิบาย**: ข้อมูลเกี่ยวกับเว็บไซต์ เช่น copyright, ลิงก์นโยบาย

**HTML Semantic**: `<footer>` (เมื่ออยู่ใน `<body>` โดยตรง)

```html
<footer>
  <div class="footer-content">
    <section>
      <h3>ติดต่อเรา</h3>
      <address>
        <p>โทร: 02-123-4567</p>
        <p>อีเมล: info@company.com</p>
      </address>
    </section>

    <section>
      <h3>ลิงก์สำคัญ</h3>
      <ul>
        <li><a href="/privacy">นโยบายความเป็นส่วนตัว</a></li>
        <li><a href="/terms">ข้อกำหนดการใช้งาน</a></li>
      </ul>
    </section>
  </div>

  <div class="copyright">
    <p>&copy; 2024 บริษัท ABC. สงวนลิขสิทธิ์.</p>
  </div>
</footer>
```

---

## 2. Landmark Regions เพิ่มเติม

### 2.1 Search (`role="search"`)

**คำอธิบาย**: ส่วนการค้นหา

```html
<!-- Search form -->
<form role="search" aria-label="ค้นหาในเว็บไซต์">
  <label for="search-input">ค้นหา:</label>
  <input
    type="search"
    id="search-input"
    name="q"
    placeholder="พิมพ์คำค้นหา..."
  />
  <button type="submit">ค้นหา</button>
</form>

<!-- Search section -->
<section role="search">
  <h2>ค้นหาสินค้า</h2>
  <form>
    <div class="search-filters">
      <label for="category">หมวดหมู่:</label>
      <select id="category" name="category">
        <option value="">ทั้งหมด</option>
        <option value="electronics">อิเล็กทรอนิกส์</option>
      </select>
    </div>

    <div class="search-input">
      <label for="product-search">ชื่อสินค้า:</label>
      <input type="search" id="product-search" name="q" />
      <button type="submit">ค้นหา</button>
    </div>
  </form>
</section>
```

### 2.2 Application (`role="application"`)

**คำอธิบาย**: ส่วนที่ทำงานเหมือนแอปพลิเคชัน

```html
<!-- Calculator app -->
<div role="application" aria-label="เครื่องคิดเลข">
  <h2>เครื่องคิดเลข</h2>
  <div class="calculator">
    <input type="text" readonly aria-label="ผลลัพธ์" />
    <div class="buttons">
      <button type="button">1</button>
      <button type="button">2</button>
      <!-- buttons... -->
    </div>
  </div>
</div>

<!-- Interactive map -->
<div role="application" aria-label="แผนที่โต้ตอบ">
  <h3>แผนที่สาขา</h3>
  <div class="map-container">
    <!-- Interactive map content -->
  </div>
</div>
```

### 2.3 Region (`role="region"`)

**คำอธิบาย**: ส่วนสำคัญที่ผู้ใช้อาจต้องการข้ามไปได้ทันที

```html
<!-- Important content section -->
<section role="region" aria-labelledby="news-heading">
  <h2 id="news-heading">ข่าวสารล่าสุด</h2>
  <article>
    <h3>ข่าวที่ 1</h3>
    <p>เนื้อหาข่าว...</p>
  </article>
</section>

<!-- Tab panel -->
<div role="region" aria-labelledby="tab1" aria-live="polite">
  <h3 id="tab1">แท็บที่ 1</h3>
  <p>เนื้อหาในแท็บ...</p>
</div>
```

---

## 3. การใช้ ARIA Labels กับ Landmarks

### 3.1 aria-label

```html
<!-- ให้ชื่อที่ชัดเจน -->
<nav aria-label="เมนูหลัก">
  <ul>
    <li><a href="/">หน้าแรก</a></li>
  </ul>
</nav>

<nav aria-label="เมนูสินค้า">
  <ul>
    <li><a href="/products/web">เว็บไซต์</a></li>
  </ul>
</nav>

<aside aria-label="โฆษณา">
  <h3>โฆษณา</h3>
  <!-- ads content -->
</aside>
```

### 3.2 aria-labelledby

```html
<!-- อ้างอิงจาก heading -->
<section aria-labelledby="services-heading">
  <h2 id="services-heading">บริการของเรา</h2>
  <p>รายละเอียดบริการ...</p>
</section>

<aside aria-labelledby="related-heading">
  <h3 id="related-heading">บทความที่เกี่ยวข้อง</h3>
  <ul>
    <li><a href="/related-1">บทความ 1</a></li>
  </ul>
</aside>
```

### 3.3 aria-describedby

```html
<!-- คำอธิบายเพิ่มเติม -->
<nav aria-label="เมนูหลัก" aria-describedby="nav-help">
  <ul>
    <li><a href="/">หน้าแรก</a></li>
  </ul>
</nav>
<p id="nav-help">ใช้ปุ่มลูกศรเพื่อนำทางในเมนู</p>

<main aria-describedby="content-intro">
  <h1>หน้าแรก</h1>
  <p id="content-intro">ยินดีต้อนรับสู่เว็บไซต์ของเรา</p>
</main>
```

---

## 4. โครงสร้างหน้าเว็บแบบสมบูรณ์

### ตัวอย่างโครงสร้างที่ถูกต้อง

```html
<!DOCTYPE html>
<html lang="th">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>บริษัท ABC Technology</title>
  </head>
  <body>
    <!-- Skip Links -->
    <div class="skip-links">
      <a href="#main" class="skip-link">ข้ามไปเนื้อหาหลัก</a>
      <a href="#nav" class="skip-link">ข้ามไปเมนูนำทาง</a>
    </div>

    <!-- Banner Landmark -->
    <header role="banner">
      <div class="logo">
        <img src="logo.png" alt="โลโก้บริษัท ABC Technology" />
        <h1>ABC Technology</h1>
      </div>

      <!-- Search Landmark -->
      <form role="search" aria-label="ค้นหาในเว็บไซต์">
        <label for="site-search" class="visually-hidden">ค้นหา:</label>
        <input type="search" id="site-search" placeholder="ค้นหา..." />
        <button type="submit">ค้นหา</button>
      </form>
    </header>

    <!-- Navigation Landmark -->
    <nav id="nav" aria-label="เมนูหลัก">
      <ul>
        <li><a href="/" aria-current="page">หน้าแรก</a></li>
        <li><a href="/about">เกี่ยวกับเรา</a></li>
        <li><a href="/services">บริการ</a></li>
        <li><a href="/portfolio">ผลงาน</a></li>
        <li><a href="/contact">ติดต่อ</a></li>
      </ul>
    </nav>

    <!-- Breadcrumb Navigation -->
    <nav aria-label="breadcrumb">
      <ol>
        <li><a href="/">หน้าแรก</a></li>
        <li><a href="/services">บริการ</a></li>
        <li aria-current="page">พัฒนาเว็บไซต์</li>
      </ol>
    </nav>

    <!-- Main Content Landmark -->
    <main id="main">
      <h1>บริการพัฒนาเว็บไซต์</h1>

      <!-- Important Region -->
      <section role="region" aria-labelledby="intro-heading">
        <h2 id="intro-heading">เกี่ยวกับบริการ</h2>
        <p>เราให้บริการพัฒนาเว็บไซต์ที่ทันสมัย...</p>
      </section>

      <!-- Article Content -->
      <article>
        <header>
          <h2>ขั้นตอนการพัฒนา</h2>
          <p>กระบวนการพัฒนาเว็บไซต์ของเรา</p>
        </header>

        <section>
          <h3>1. วางแผนและออกแบบ</h3>
          <p>เริ่มต้นด้วยการวิเคราะห์ความต้องการ...</p>
        </section>

        <!-- Related Content -->
        <aside aria-labelledby="related-heading">
          <h3 id="related-heading">บริการที่เกี่ยวข้อง</h3>
          <ul>
            <li><a href="/services/design">ออกแบบ UI/UX</a></li>
            <li><a href="/services/seo">SEO</a></li>
          </ul>
        </aside>
      </article>
    </main>

    <!-- Complementary Content -->
    <aside role="complementary" aria-label="ข้อมูลเสริม">
      <section>
        <h3>บริการยอดนิยม</h3>
        <ul>
          <li><a href="/services/ecommerce">พัฒนา E-commerce</a></li>
          <li><a href="/services/mobile">แอพมือถือ</a></li>
        </ul>
      </section>

      <section>
        <h3>ติดต่อเรา</h3>
        <address>
          <p>โทร: <a href="tel:+6621234567">02-123-4567</a></p>
          <p>อีเมล: <a href="mailto:info@abc.com">info@abc.com</a></p>
        </address>
      </section>
    </aside>

    <!-- Content Info Landmark -->
    <footer role="contentinfo">
      <div class="footer-content">
        <section>
          <h3>บริษัท ABC Technology</h3>
          <p>ผู้เชี่ยวชาญด้านการพัฒนาเว็บไซต์</p>
        </section>

        <!-- Footer Navigation -->
        <nav aria-label="ลิงก์ในส่วนท้าย">
          <h3>ลิงก์สำคัญ</h3>
          <ul>
            <li><a href="/privacy">นโยบายความเป็นส่วนตัว</a></li>
            <li><a href="/terms">ข้อกำหนดการใช้งาน</a></li>
            <li><a href="/sitemap">แผนที่เว็บไซต์</a></li>
          </ul>
        </nav>

        <!-- Social Media Navigation -->
        <nav aria-label="โซเชียลมีเดีย">
          <h3>ติดตามเรา</h3>
          <ul>
            <li><a href="https://facebook.com/abc">Facebook</a></li>
            <li><a href="https://twitter.com/abc">Twitter</a></li>
          </ul>
        </nav>
      </div>

      <div class="copyright">
        <p>&copy; 2024 บริษัท ABC Technology จำกัด สงวนลิขสิทธิ์</p>
      </div>
    </footer>
  </body>
</html>
```

---

## 5. Skip Links

### การสร้าง Skip Links

```html
<!-- Skip Links ที่จำเป็น -->
<div class="skip-links">
  <a href="#main" class="skip-link">ข้ามไปเนื้อหาหลัก</a>
  <a href="#nav" class="skip-link">ข้ามไปเมนูนำทาง</a>
  <a href="#search" class="skip-link">ข้ามไปการค้นหา</a>
  <a href="#footer" class="skip-link">ข้ามไปส่วนท้าย</a>
</div>
```

### CSS สำหรับ Skip Links

```css
/* ซ่อน skip links จนกว่าจะ focus */
.skip-link {
  position: absolute;
  top: -40px;
  left: 6px;
  background: #000;
  color: #fff;
  padding: 8px;
  text-decoration: none;
  z-index: 1000;
  border-radius: 0 0 4px 4px;
}

.skip-link:focus {
  top: 0;
}

/* ทำให้มองเห็นได้เสมอสำหรับ testing */
.skip-links-visible .skip-link {
  top: 0;
  position: static;
  display: block;
}
```

---

## 6. การทดสอบ Landmarks

### เครื่องมือทดสอบ

#### 6.1 Screen Readers

```html
<!-- คำสั่งใน NVDA (Windows) -->
<!-- D = ข้ามไป landmark ถัดไป -->
<!-- Shift + D = กลับไป landmark ก่อนหน้า -->

<!-- คำสั่งใน VoiceOver (macOS) -->
<!-- VO + U = เปิด rotor -->
<!-- เลือก Landmarks จาก rotor -->
```

#### 6.2 Browser Extensions

- **Accessibility Insights**: Microsoft
- **axe DevTools**: Deque Systems
- **WAVE**: WebAIM
- **Lighthouse**: Google Chrome

#### 6.3 Keyboard Testing

```html
<!-- ทดสอบการ navigate ด้วย keyboard -->
<!-- Tab = ข้ามไปลิงก์ถัดไป -->
<!-- Shift + Tab = กลับไปลิงก์ก่อนหน้า -->
<!-- Enter = เปิดลิงก์ -->
```

---

## 7. ข้อผิดพลาดที่พบบ่อย

### ❌ ข้อผิดพลาด

```html
<!-- ผิด: ไม่มี landmark หลัก -->
<body>
  <div class="header">
    <h1>ชื่อเว็บไซต์</h1>
  </div>
  <div class="content">
    <p>เนื้อหา</p>
  </div>
</body>

<!-- ผิด: มี main หลายอัน -->
<body>
  <main>
    <h1>หน้า 1</h1>
  </main>
  <main>
    <h1>หน้า 2</h1>
  </main>
</body>

<!-- ผิด: ไม่มี aria-label สำหรับ nav หลายอัน -->
<nav>
  <ul>
    <li><a href="/">หน้าแรก</a></li>
  </ul>
</nav>
<nav>
  <ul>
    <li><a href="/about">เกี่ยวกับ</a></li>
  </ul>
</nav>
```

### ✅ การแก้ไข

```html
<!-- ถูก: มี landmark ครบถ้วน -->
<body>
  <header>
    <h1>ชื่อเว็บไซต์</h1>
  </header>
  <nav aria-label="เมนูหลัก">
    <ul>
      <li><a href="/">หน้าแรก</a></li>
    </ul>
  </nav>
  <main>
    <h2>เนื้อหาหลัก</h2>
    <p>เนื้อหา</p>
  </main>
  <footer>
    <p>&copy; 2024</p>
  </footer>
</body>

<!-- ถูก: แยก nav ด้วย aria-label -->
<nav aria-label="เมนูหลัก">
  <ul>
    <li><a href="/">หน้าแรก</a></li>
  </ul>
</nav>
<nav aria-label="โซเชียลมีเดีย">
  <ul>
    <li><a href="/facebook">Facebook</a></li>
  </ul>
</nav>
```

---

## 8. Checklist สำหรับ Landmarks

### ✅ รายการตรวจสอบ

- [ ] มี `<header>` หรือ `role="banner"` สำหรับส่วนหัว
- [ ] มี `<nav>` หรือ `role="navigation"` สำหรับเมนู
- [ ] มี `<main>` หรือ `role="main"` เพียง 1 อันต่อหน้า
- [ ] มี `<footer>` หรือ `role="contentinfo"` สำหรับส่วนท้าย
- [ ] ใช้ `aria-label` สำหรับ landmarks ที่ซ้ำกัน
- [ ] มี skip links สำหรับการ navigate
- [ ] ทุก landmark มี heading ที่เหมาะสม
- [ ] ไม่มี landmark ที่ว่างเปล่า
- [ ] ทดสอบด้วย screen reader
- [ ] ทดสอบการ navigate ด้วย keyboard

---

## สรุป

### Landmarks สำคัญ

1. **Banner** (`<header>`) - ส่วนหัวหลัก
2. **Navigation** (`<nav>`) - เมนูนำทาง
3. **Main** (`<main>`) - เนื้อหาหลัก (1 อันต่อหน้า)
4. **Complementary** (`<aside>`) - เนื้อหาเสริม
5. **Contentinfo** (`<footer>`) - ข้อมูลเว็บไซต์

### หลักการสำคัญ

- **ใช้ semantic HTML เป็นหลัก**
- **เพิ่ม aria-label เมื่อมี landmarks ซ้ำกัน**
- **จัดทำ skip links สำหรับการ navigate**
- **ทดสอบด้วย assistive technology**

การใช้ landmarks อย่างถูกต้องจะทำให้เว็บไซต์เข้าถึงได้ง่ายสำหรับผู้ใช้ทุกคน และปฏิบัติตามมาตรฐาน Web Accessibility
