# โครงสร้างหน้าเว็บด้วย Semantic HTML Layout

## ภาพรวม

Semantic HTML Layout เป็นการใช้ HTML tags ที่มีความหมายเฉพาะเพื่อสร้างโครงสร้างหน้าเว็บที่มีความหมาย ช่วยให้:

- **Search Engines** เข้าใจโครงสร้างเว็บไซต์ได้ดีขึ้น
- **Screen Readers** อ่านเนื้อหาได้ถูกต้อง
- **Developers** เข้าใจโค้ดได้ง่ายขึ้น
- **Maintainability** บำรุงรักษาโค้ดได้ง่าย

## โครงสร้างพื้นฐานของหน้าเว็บ

```
┌─────────────────────┐
│      <header>       │  ← ส่วนหัวของหน้า
├─────────────────────┤
│       <nav>         │  ← เมนูนำทาง
├─────────────────────┤
│      <main>         │  ← เนื้อหาหลัก
│  ┌───────┬───────┐  │
│  │<sect> │<aside>│  │  ← ส่วนเนื้อหา + แถบข้าง
│  │<art>  │       │  │
│  └───────┴───────┘  │
├─────────────────────┤
│      <footer>       │  ← ส่วนท้ายของหน้า
└─────────────────────┘
```

---

## 1. `<header>` - ส่วนหัวของหน้า

### คำอธิบาย

`<header>` ใช้สำหรับกำหนดส่วนหัวของเอกสาร หรือส่วนหัวของ section โดยทั่วไปจะประกอบด้วย:

- โลโก้ของเว็บไซต์
- ชื่อเว็บไซต์
- เมนูนำทางหลัก
- ข้อมูลการติดต่อ
- แบนเนอร์โฆษณา

### ไวยากรณ์

```html
<header>
  <!-- เนื้อหาส่วนหัว -->
</header>
```

### ตัวอย่างการใช้งาน

#### Header แบบพื้นฐาน

```html
<header>
  <h1>ชื่อเว็บไซต์</h1>
  <p>คำอธิบายสั้นๆ เกี่ยวกับเว็บไซต์</p>
</header>
```

#### Header แบบครบครัน

```html
<header>
  <div class="logo">
    <img src="logo.png" alt="โลโก้บริษัท ABC" />
    <h1>ABC Technology</h1>
  </div>

  <nav class="main-nav">
    <ul>
      <li><a href="/">หน้าแรก</a></li>
      <li><a href="/about">เกี่ยวกับเรา</a></li>
      <li><a href="/services">บริการ</a></li>
      <li><a href="/contact">ติดต่อ</a></li>
    </ul>
  </nav>

  <div class="contact-info">
    <p>โทร: 02-123-4567</p>
    <p>อีเมล: info@abc.com</p>
  </div>
</header>
```

#### Header ภายใน Article

```html
<article>
  <header>
    <h2>ชื่อบทความ</h2>
    <p class="meta">
      โดย: <span class="author">นาย A</span> | วันที่:
      <time datetime="2024-01-15">15 มกราคม 2024</time>
    </p>
  </header>

  <div class="content">
    <!-- เนื้อหาบทความ -->
  </div>
</article>
```

---

## 2. `<nav>` - เมนูนำทาง

### คำอธิบาย

`<nav>` ใช้สำหรับกำหนดส่วนที่เป็นลิงก์นำทางหลัก เช่น:

- เมนูหลักของเว็บไซต์
- breadcrumb navigation
- เมนูย่อยในหน้า
- ปุ่ม previous/next

### ไวยากรณ์

```html
<nav>
  <!-- ลิงก์นำทาง -->
</nav>
```

### ตัวอย่างการใช้งาน

#### เมนูหลัก

```html
<nav class="main-navigation" aria-label="เมนูหลัก">
  <ul>
    <li><a href="/" aria-current="page">หน้าแรก</a></li>
    <li><a href="/products">สินค้า</a></li>
    <li><a href="/about">เกี่ยวกับเรา</a></li>
    <li><a href="/contact">ติดต่อ</a></li>
  </ul>
</nav>
```

#### Breadcrumb Navigation

```html
<nav aria-label="breadcrumb">
  <ol class="breadcrumb">
    <li><a href="/">หน้าแรก</a></li>
    <li><a href="/products">สินค้า</a></li>
    <li><a href="/products/electronics">อิเล็กทรอนิกส์</a></li>
    <li aria-current="page">โทรศัพท์มือถือ</li>
  </ol>
</nav>
```

#### เมนูย่อยในหน้า

```html
<nav class="page-navigation" aria-label="เมนูในหน้า">
  <h3>เนื้อหาในหน้านี้</h3>
  <ul>
    <li><a href="#introduction">บทนำ</a></li>
    <li><a href="#features">คุณสมบัติ</a></li>
    <li><a href="#examples">ตัวอย่าง</a></li>
    <li><a href="#conclusion">สรุป</a></li>
  </ul>
</nav>
```

#### เมนูแบบ Dropdown

```html
<nav class="main-nav">
  <ul>
    <li><a href="/">หน้าแรก</a></li>
    <li class="dropdown">
      <a href="/products">สินค้า</a>
      <ul class="dropdown-menu">
        <li><a href="/products/electronics">อิเล็กทรอนิกส์</a></li>
        <li><a href="/products/clothing">เสื้อผ้า</a></li>
        <li><a href="/products/books">หนังสือ</a></li>
      </ul>
    </li>
    <li><a href="/about">เกี่ยวกับเรา</a></li>
  </ul>
</nav>
```

---

## 3. `<main>` - เนื้อหาหลัก

### คำอธิบาย

`<main>` ใช้สำหรับกำหนดเนื้อหาหลักของเอกสาร โดย:

- ต้องมีเพียง 1 อัน ต่อหน้า (ไม่ซ้ำ)
- ต้องไม่อยู่ภายใน `<article>`, `<aside>`, `<header>`, `<footer>`, `<nav>`
- เป็นเนื้อหาที่เฉพาะเจาะจงของหน้านั้นๆ

### ไวยากรณ์

```html
<main>
  <!-- เนื้อหาหลักของหน้า -->
</main>
```

### ตัวอย่างการใช้งาน

#### Main แบบพื้นฐาน

```html
<main>
  <h1>ยินดีต้อนรับสู่เว็บไซต์ของเรา</h1>
  <p>นี่คือเนื้อหาหลักของหน้าแรก</p>

  <section>
    <h2>บริการของเรา</h2>
    <!-- เนื้อหาบริการ -->
  </section>

  <section>
    <h2>ข่าวสารล่าสุด</h2>
    <!-- เนื้อหาข่าวสาร -->
  </section>
</main>
```

#### Main สำหรับหน้าบทความ

```html
<main>
  <article>
    <header>
      <h1>วิธีการเรียนรู้ HTML อย่างมีประสิทธิภาพ</h1>
      <p class="meta">
        เผยแพร่เมื่อ: <time datetime="2024-01-15">15 มกราคม 2024</time>
      </p>
    </header>

    <div class="content">
      <p>HTML เป็นภาษาพื้นฐานสำหรับการสร้างเว็บไซต์...</p>
      <!-- เนื้อหาบทความ -->
    </div>
  </article>
</main>
```

#### Main สำหรับหน้ารายการสินค้า

```html
<main>
  <h1>รายการสินค้า</h1>

  <div class="filters">
    <h2>กรองสินค้า</h2>
    <!-- ฟิลเตอร์ -->
  </div>

  <section class="products">
    <h2>สินค้าทั้งหมด</h2>
    <div class="product-grid">
      <!-- รายการสินค้า -->
    </div>
  </section>
</main>
```

---

## 4. `<section>` - ส่วนของเนื้อหา

### คำอธิบาย

`<section>` ใช้สำหรับจัดกลุ่มเนื้อหาที่เกี่ยวข้องกัน โดย:

- ควรมี heading (h1-h6) เสมอ
- ใช้เมื่อไม่มี semantic element อื่นที่เหมาะสมกว่า
- เป็นส่วนที่มีความหมายในตัวเอง

### ไวยากรณ์

```html
<section>
  <h2>หัวข้อของ section</h2>
  <!-- เนื้อหา -->
</section>
```

### ตัวอย่างการใช้งาน

#### Section แบบพื้นฐาน

```html
<section>
  <h2>เกี่ยวกับบริษัท</h2>
  <p>บริษัทเราก่อตั้งขึ้นในปี 2010...</p>
  <img src="company-photo.jpg" alt="ภาพบริษัท" />
</section>

<section>
  <h2>บริการของเรา</h2>
  <ul>
    <li>พัฒนาเว็บไซต์</li>
    <li>ออกแบบ UI/UX</li>
    <li>ให้คำปรึกษา IT</li>
  </ul>
</section>
```

#### Section ที่มี Article ซ้อน

```html
<section>
  <h2>บทความล่าสุด</h2>

  <article>
    <h3>เทคนิคการเขียน CSS</h3>
    <p>เรียนรู้เทคนิคการเขียน CSS ให้มีประสิทธิภาพ...</p>
  </article>

  <article>
    <h3>การใช้งาน JavaScript</h3>
    <p>พื้นฐานการใช้งาน JavaScript สำหรับมือใหม่...</p>
  </article>
</section>
```

#### Section สำหรับแบบฟอร์ม

```html
<section>
  <h2>ติดต่อเรา</h2>

  <form>
    <div class="form-group">
      <label for="name">ชื่อ:</label>
      <input type="text" id="name" name="name" required />
    </div>

    <div class="form-group">
      <label for="email">อีเมล:</label>
      <input type="email" id="email" name="email" required />
    </div>

    <div class="form-group">
      <label for="message">ข้อความ:</label>
      <textarea id="message" name="message" required></textarea>
    </div>

    <button type="submit">ส่งข้อความ</button>
  </form>
</section>
```

---

## 5. `<article>` - บทความหรือเนื้อหาอิสระ

### คำอธิบาย

`<article>` ใช้สำหรับเนื้อหาที่:

- สามารถแยกออกมาอ่านได้อย่างอิสระ
- สามารถเผยแพร่ซ้ำได้ (เช่น RSS feed)
- มีความหมายในตัวเอง

### การใช้งานที่เหมาะสม

- บทความในบล็อก
- ข่าวสาร
- รีวิวสินค้า
- โพสต์ในฟอรั่ม
- ความคิดเห็น

### ไวยากรณ์

```html
<article>
  <header>
    <h2>หัวข้อบทความ</h2>
    <!-- metadata -->
  </header>

  <!-- เนื้อหาบทความ -->

  <footer>
    <!-- ข้อมูลเพิ่มเติม -->
  </footer>
</article>
```

### ตัวอย่างการใช้งาน

#### บทความในบล็อก

```html
<article>
  <header>
    <h2>10 เทคนิคการเขียน HTML ให้มีประสิทธิภาพ</h2>
    <p class="meta">
      โดย: <span class="author">จอห์น โด</span> |
      <time datetime="2024-01-15" pubdate>15 มกราคม 2024</time> | หมวด:
      <span class="category">Web Development</span>
    </p>
  </header>

  <div class="content">
    <p>การเขียน HTML ที่ดีไม่ใช่แค่การทำให้เว็บไซต์แสดงผลได้...</p>

    <h3>1. ใช้ Semantic HTML</h3>
    <p>การใช้ semantic elements ช่วยให้...</p>

    <h3>2. เขียน Alt Text ที่ดี</h3>
    <p>Alt text ที่ดีควรอธิบาย...</p>

    <!-- เนื้อหาต่อ -->
  </div>

  <footer>
    <p class="tags">
      แท็ก:
      <a href="/tags/html">#HTML</a>
      <a href="/tags/web-development">#Web Development</a>
      <a href="/tags/best-practices">#Best Practices</a>
    </p>

    <div class="social-share">
      <a href="#" class="share-facebook">แชร์บน Facebook</a>
      <a href="#" class="share-twitter">แชร์บน Twitter</a>
    </div>
  </footer>
</article>
```

#### รีวิวสินค้า

```html
<article>
  <header>
    <h3>รีวิว iPhone 15 Pro</h3>
    <div class="rating">
      <span class="stars">★★★★☆</span>
      <span class="score">4.5/5</span>
    </div>
    <p class="reviewer">
      โดย: <span class="author">แอนนา สมิท</span> |
      <time datetime="2024-01-10">10 มกราคม 2024</time>
    </p>
  </header>

  <div class="review-content">
    <p>iPhone 15 Pro เป็นมือถือที่น่าประทับใจมาก...</p>

    <h4>ข้อดี:</h4>
    <ul>
      <li>กล้องถ่ายภาพคมชัด</li>
      <li>ประสิทธิภาพสูง</li>
      <li>ดีไซน์สวยงาม</li>
    </ul>

    <h4>ข้อเสีย:</h4>
    <ul>
      <li>ราคาค่อนข้างสูง</li>
      <li>แบตเตอรี่อาจไม่เพียงพอสำหรับผู้ใช้หนัก</li>
    </ul>
  </div>

  <footer>
    <p class="recommendation">แนะนำสำหรับ: ผู้ที่ต้องการมือถือประสิทธิภาพสูง</p>
  </footer>
</article>
```

#### ความคิดเห็น

```html
<article class="comment">
  <header>
    <img src="avatar.jpg" alt="รูปโปรไฟล์ของ สมชาย" class="avatar" />
    <h4 class="commenter">สมชาย ใจดี</h4>
    <time datetime="2024-01-15T14:30:00">15 มกราคม 2024 เวลา 14:30</time>
  </header>

  <div class="comment-content">
    <p>บทความนี้มีประโยชน์มากครับ ขอบคุณสำหรับข้อมูลดีๆ</p>
  </div>

  <footer>
    <button class="reply-btn">ตอบกลับ</button>
    <button class="like-btn">ถูกใจ (12)</button>
  </footer>
</article>
```

---

## 6. `<aside>` - เนื้อหาเสริม

### คำอธิบาย

`<aside>` ใช้สำหรับเนื้อหาที่:

- เป็นข้อมูลเสริมหรือข้อมูลเพิ่มเติม
- ไม่ใช่เนื้อหาหลัก
- เกี่ยวข้องกับเนื้อหาโดยรอบ (แต่ไม่จำเป็น)

### การใช้งานที่เหมาะสม

- Sidebar ของเว็บไซต์
- กล่องข้อมูลเสริม
- โฆษณา
- เมนูย่อย
- ลิงก์ที่เกี่ยวข้อง

### ไวยากรณ์

```html
<aside>
  <!-- เนื้อหาเสริม -->
</aside>
```

### ตัวอย่างการใช้งาน

#### Sidebar หลัก

```html
<aside class="main-sidebar">
  <section class="widget">
    <h3>หมวดหมู่</h3>
    <ul>
      <li><a href="/category/web-development">Web Development (25)</a></li>
      <li><a href="/category/design">Design (18)</a></li>
      <li><a href="/category/javascript">JavaScript (12)</a></li>
      <li><a href="/category/css">CSS (15)</a></li>
    </ul>
  </section>

  <section class="widget">
    <h3>บทความยอดนิยม</h3>
    <ol>
      <li><a href="/popular-1">เรียนรู้ CSS Grid ใน 30 นาที</a></li>
      <li><a href="/popular-2">JavaScript ES6 สำหรับมือใหม่</a></li>
      <li><a href="/popular-3">วิธีทำ Responsive Design</a></li>
    </ol>
  </section>

  <section class="widget">
    <h3>ติดตามเรา</h3>
    <div class="social-links">
      <a href="#" class="facebook">Facebook</a>
      <a href="#" class="twitter">Twitter</a>
      <a href="#" class="instagram">Instagram</a>
    </div>
  </section>
</aside>
```

#### Aside ภายใน Article

```html
<article>
  <header>
    <h2>การใช้งาน CSS Flexbox</h2>
  </header>

  <div class="content">
    <p>CSS Flexbox เป็นเครื่องมือที่ทรงพลังสำหรับการจัดวาง...</p>

    <aside class="tip">
      <h4>💡 เคล็ดลับ</h4>
      <p>ใช้ `justify-content: center` เพื่อจัดวางให้อยู่ตรงกลางในแนวนอน</p>
    </aside>

    <p>นอกจากนี้เรายังสามารถใช้ align-items เพื่อ...</p>

    <aside class="related">
      <h4>บทความที่เกี่ยวข้อง</h4>
      <ul>
        <li><a href="/css-grid">เรียนรู้ CSS Grid</a></li>
        <li><a href="/responsive-design">Responsive Design พื้นฐาน</a></li>
      </ul>
    </aside>
  </div>
</article>
```

#### กล่องโฆษณา

```html
<aside class="advertisement">
  <h4>โฆษณา</h4>
  <div class="ad-content">
    <img src="ad-banner.jpg" alt="โฆษณาคอร์สเรียน Web Development" />
    <p>เรียน Web Development จากศูนย์ ลงทะเบียนเลย!</p>
    <a href="/course" class="ad-link">ดูรายละเอียด</a>
  </div>
</aside>
```

---

## 7. `<footer>` - ส่วนท้าย

### คำอธิบาย

`<footer>` ใช้สำหรับส่วนท้ายของ:

- เอกสารทั้งหมด (site footer)
- Section หรือ Article

### เนื้อหาที่เหมาะสม

- ข้อมูลลิขสิทธิ์
- ลิงก์นโยบาย
- ข้อมูลติดต่อ
- แผนที่เว็บไซต์
- ลิงก์โซเชียลมีเดีย

### ไวยากรณ์

```html
<footer>
  <!-- เนื้อหาส่วนท้าย -->
</footer>
```

### ตัวอย่างการใช้งาน

#### Footer หลักของเว็บไซต์

```html
<footer class="site-footer">
  <div class="footer-content">
    <div class="footer-section">
      <h3>เกี่ยวกับเรา</h3>
      <p>
        บริษัท ABC Technology ผู้เชี่ยวชาญด้านการพัฒนาเว็บไซต์และแอปพลิเคชัน
      </p>
      <div class="social-links">
        <a href="#" aria-label="Facebook">📘</a>
        <a href="#" aria-label="Twitter">🐦</a>
        <a href="#" aria-label="LinkedIn">💼</a>
      </div>
    </div>

    <div class="footer-section">
      <h3>บริการ</h3>
      <ul>
        <li><a href="/services/web-design">ออกแบบเว็บไซต์</a></li>
        <li><a href="/services/web-development">พัฒนาเว็บไซต์</a></li>
        <li><a href="/services/seo">SEO</a></li>
        <li><a href="/services/maintenance">บำรุงรักษาเว็บไซต์</a></li>
      </ul>
    </div>

    <div class="footer-section">
      <h3>ติดต่อเรา</h3>
      <address>
        <p>📍 123 ถนนสุขุมวิท กรุงเทพฯ 10110</p>
        <p>📞 <a href="tel:+6621234567">02-123-4567</a></p>
        <p>📧 <a href="mailto:info@abc.com">info@abc.com</a></p>
      </address>
    </div>

    <div class="footer-section">
      <h3>จดหมายข่าว</h3>
      <p>รับข่าวสารและเคล็ดลับใหม่ๆ</p>
      <form class="newsletter-form">
        <input type="email" placeholder="อีเมลของคุณ" required />
        <button type="submit">สมัครรับ</button>
      </form>
    </div>
  </div>

  <div class="footer-bottom">
    <div class="footer-links">
      <a href="/privacy">นโยบายความเป็นส่วนตัว</a>
      <a href="/terms">ข้อกำหนดการใช้งาน</a>
      <a href="/sitemap">แผนที่เว็บไซต์</a>
    </div>

    <p class="copyright">© 2024 ABC Technology. สงวนลิขสิทธิ์.</p>
  </div>
</footer>
```

#### Footer ภายใน Article

```html
<article>
  <header>
    <h2>วิธีการเรียนรู้ Programming</h2>
  </header>

  <div class="content">
    <!-- เนื้อหาบทความ -->
  </div>

  <footer class="article-footer">
    <div class="author-info">
      <img src="author-avatar.jpg" alt="รูปผู้เขียน" class="author-avatar" />
      <div class="author-details">
        <h4>เกี่ยวกับผู้เขียน</h4>
        <p><strong>จอห์น โด</strong> - นักพัฒนาเว็บไซต์ที่มีประสบการณ์ 10 ปี</p>
        <p>ติดตาม: <a href="/author/john">บทความอื่นๆ</a></p>
      </div>
    </div>

    <div class="article-meta">
      <p>เผยแพร่: <time datetime="2024-01-15">15 มกราคม 2024</time></p>
      <p>แก้ไขล่าสุด: <time datetime="2024-01-16">16 มกราคม 2024</time></p>
      <p>หมวดหมู่: <a href="/category/programming">Programming</a></p>
    </div>

    <div class="share-buttons">
      <h4>แชร์บทความนี้:</h4>
      <a href="#" class="share-facebook">Facebook</a>
      <a href="#" class="share-twitter">Twitter</a>
      <a href="#" class="share-linkedin">LinkedIn</a>
    </div>
  </footer>
</article>
```

---

## 8. การรวม Semantic Elements เข้าด้วยกัน

### ตัวอย่างโครงสร้างหน้าเว็บแบบสมบูรณ์

```html
<!DOCTYPE html>
<html lang="th">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>ABC Technology - หน้าแรก</title>
  </head>
  <body>
    <!-- ส่วนหัวของเว็บไซต์ -->
    <header class="site-header">
      <div class="logo">
        <img src="logo.png" alt="โลโก้ ABC Technology" />
        <h1>ABC Technology</h1>
      </div>

      <!-- เมนูหลัก -->
      <nav class="main-navigation" aria-label="เมนูหลัก">
        <ul>
          <li><a href="/" aria-current="page">หน้าแรก</a></li>
          <li><a href="/about">เกี่ยวกับเรา</a></li>
          <li><a href="/services">บริการ</a></li>
          <li><a href="/portfolio">ผลงาน</a></li>
          <li><a href="/blog">บล็อก</a></li>
          <li><a href="/contact">ติดต่อ</a></li>
        </ul>
      </nav>
    </header>

    <!-- เนื้อหาหลัก -->
    <main>
      <!-- ส่วนแนะนำ -->
      <section class="hero">
        <h2>ยินดีต้อนรับสู่ ABC Technology</h2>
        <p>เราเป็นผู้เชี่ยวชาญด้านการพัฒนาเว็บไซต์และแอปพลิเคชัน</p>
        <a href="/contact" class="cta-button">ติดต่อเราเลย</a>
      </section>

      <!-- ส่วนบริการ -->
      <section class="services">
        <h2>บริการของเรา</h2>

        <article class="service">
          <h3>พัฒนาเว็บไซต์</h3>
          <p>สร้างเว็บไซต์ที่ทันสมัยและมีประสิทธิภาพ</p>
        </article>

        <article class="service">
          <h3>ออกแบบ UI/UX</h3>
          <p>ออกแบบประสบการณ์ผู้ใช้ที่น่าประทับใจ</p>
        </article>

        <article class="service">
          <h3>ให้คำปรึกษา IT</h3>
          <p>คำปรึกษาด้านเทคโนโลยีสารสนเทศ</p>
        </article>
      </section>

      <!-- ส่วนบทความล่าสุด -->
      <section class="latest-posts">
        <h2>บทความล่าสุด</h2>

        <article class="post-preview">
          <header>
            <h3><a href="/blog/html-tips">10 เทคนิค HTML ที่ควรรู้</a></h3>
            <time datetime="2024-01-15">15 มกราคม 2024</time>
          </header>
          <p>เรียนรู้เทคนิคการเขียน HTML ที่จะทำให้เว็บไซต์ของคุณดีขึ้น...</p>
        </article>

        <article class="post-preview">
          <header>
            <h3><a href="/blog/css-flexbox">CSS Flexbox สำหรับมือใหม่</a></h3>
            <time datetime="2024-01-12">12 มกราคม 2024</time>
          </header>
          <p>
            เรียนรู้วิธีการใช้ CSS Flexbox
            เพื่อจัดวางเลย์เอาต์ได้อย่างง่ายดาย...
          </p>
        </article>
      </section>
    </main>

    <!-- แถบข้าง -->
    <aside class="sidebar">
      <section class="widget">
        <h3>หมวดหมู่</h3>
        <ul>
          <li><a href="/category/web-development">Web Development</a></li>
          <li><a href="/category/design">Design</a></li>
          <li><a href="/category/javascript">JavaScript</a></li>
        </ul>
      </section>

      <section class="widget">
        <h3>ติดตามเรา</h3>
        <div class="social-links">
          <a href="#" class="facebook">Facebook</a>
          <a href="#" class="twitter">Twitter</a>
        </div>
      </section>
    </aside>

    <!-- ส่วนท้าย -->
    <footer class="site-footer">
      <div class="footer-content">
        <div class="company-info">
          <h3>ABC Technology</h3>
          <p>ผู้เชี่ยวชาญด้านการพัฒนาเว็บไซต์</p>
        </div>

        <div class="contact-info">
          <h3>ติดต่อเรา</h3>
          <address>
            <p>โทร: 02-123-4567</p>
            <p>อีเมล: info@abc.com</p>
          </address>
        </div>
      </div>

      <div class="footer-bottom">
        <p>&copy; 2024 ABC Technology. สงวนลิขสิทธิ์.</p>
      </div>
    </footer>
  </body>
</html>
```

---

## 9. แนวทางปฏิบัติที่ดี

### 1. การเลือกใช้ Element ให้เหมาะสม

```html
<!-- ดี - ใช้ semantic elements -->
<article>
  <header>
    <h2>หัวข้อบทความ</h2>
  </header>
  <section>
    <p>เนื้อหา...</p>
  </section>
</article>

<!-- หลีกเลี่ยง - ใช้ div ทั้งหมด -->
<div class="article">
  <div class="header">
    <h2>หัวข้อบทความ</h2>
  </div>
  <div class="content">
    <p>เนื้อหา...</p>
  </div>
</div>
```

### 2. การใช้ Heading อย่างถูกต้อง

```html
<!-- ดี - ลำดับ heading ที่ถูกต้อง -->
<main>
  <h1>หัวข้อหลัก</h1>
  <section>
    <h2>หัวข้อรอง</h2>
    <h3>หัวข้อย่อย</h3>
  </section>
</main>

<!-- หลีกเลี่ยง - ข้าม level -->
<main>
  <h1>หัวข้อหลัก</h1>
  <section>
    <h4>หัวข้อรอง</h4>
    <!-- ข้าม h2, h3 -->
  </section>
</main>
```

### 3. การใช้ ARIA attributes

```html
<!-- เพิ่ม accessibility -->
<nav aria-label="เมนูหลัก">
  <ul>
    <li><a href="/" aria-current="page">หน้าแรก</a></li>
    <li><a href="/about">เกี่ยวกับ</a></li>
  </ul>
</nav>

<main aria-label="เนื้อหาหลัก">
  <!-- เนื้อหา -->
</main>
```

### 4. การใช้ Landmark Roles

```html
<!-- เพิ่ม landmark roles สำหรับ screen readers -->
<header role="banner">
  <!-- ส่วนหัว -->
</header>

<nav role="navigation">
  <!-- เมนู -->
</nav>

<main role="main">
  <!-- เนื้อหาหลัก -->
</main>

<aside role="complementary">
  <!-- เนื้อหาเสริม -->
</aside>

<footer role="contentinfo">
  <!-- ส่วนท้าย -->
</footer>
```

---

## 10. การทดสอบ Semantic Structure

### เครื่องมือตรวจสอบ

1. **HTML5 Outliner**: ตรวจสอบโครงสร้าง heading
2. **WAVE**: ตรวจสอบ accessibility
3. **axe DevTools**: ตรวจสอบ semantic structure
4. **Lighthouse**: ตรวจสอบ SEO และ accessibility

### Checklist

- [ ] มี `<main>` เพียง 1 อัน ต่อหน้า
- [ ] ใช้ heading (h1-h6) อย่างเป็นลำดับ
- [ ] ทุก `<section>` มี heading
- [ ] `<article>` สามารถอยู่อย่างอิสระได้
- [ ] `<aside>` เป็นเนื้อหาเสริม ไม่ใช่หลัก
- [ ] `<nav>` ใช้สำหรับลิงก์นำทางจริงๆ
- [ ] `<header>` และ `<footer>` ใช้อย่างเหมาะสม

---

## สรุป

Semantic HTML Layout ช่วยให้:

### ประโยชน์หลัก

1. **SEO ดีขึ้น**: Search engines เข้าใจโครงสร้างได้ดีขึ้น
2. **Accessibility**: Screen readers ทำงานได้ดีขึ้น
3. **Code Quality**: โค้ดอ่านง่าย เข้าใจง่าย
4. **Maintenance**: บำรุงรักษาง่ายขึ้น

### Elements หลัก

- **`<header>`**: ส่วนหัวของหน้าหรือ section
- **`<nav>`**: เมนูนำทางหลัก
- **`<main>`**: เนื้อหาหลักของหน้า (1 อันต่อหน้า)
- **`<section>`**: ส่วนของเนื้อหาที่เกี่ยวข้องกัน
- **`<article>`**: เนื้อหาอิสระที่สามารถแยกออกมาได้
- **`<aside>`**: เนื้อหาเสริมหรือแถบข้าง
- **`<footer>`**: ส่วนท้ายของหน้าหรือ section

การใช้ semantic elements อย่างถูกต้องจะทำให้เว็บไซต์มีคุณภาพและเป็นมิตรกับผู้ใช้ทุกคน
