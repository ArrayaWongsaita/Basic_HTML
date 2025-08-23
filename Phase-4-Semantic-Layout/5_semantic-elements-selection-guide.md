# การเลือกใช้ Semantic Elements ให้ถูกต้อง

## ภาพรวม

การเลือกใช้ semantic elements ให้ถูกต้องเป็นพื้นฐานสำคัญของ HTML ที่ดี ช่วยให้โครงสร้างเอกสารมีความหมาย เข้าใจง่าย และเข้าถึงได้สำหรับทุกคน

### ประโยชน์ของ Semantic HTML

- **ความหมายที่ชัดเจน**: เข้าใจโครงสร้างและบทบาทของเนื้อหา
- **การเข้าถึง**: Screen readers เข้าใจโครงสร้างได้ดีขึ้น
- **SEO**: Search engines เข้าใจเนื้อหาได้ดีขึ้น
- **การบำรุงรักษา**: โค้ดอ่านและแก้ไขง่ายขึ้น
- **มาตรฐาน**: ปฏิบัติตามมาตรฐาน Web Standards

---

## 1. `<section>` vs `<div>` - เมื่อไหร่ควรใช้อะไร

### 1.1 `<section>` - ส่วนของเนื้อหาที่มีความหมาย

**เมื่อไหร่ควรใช้**:

- เนื้อหามีหัวข้อที่ชัดเจน
- เป็นส่วนที่มีความหมายในตัวเอง
- สามารถอยู่ใน outline ของเอกสารได้
- มีเนื้อหาที่เกี่ยวข้องกันในกลุ่มเดียว

```html
<!-- ✅ ถูกต้อง: section พร้อม heading -->
<section>
  <h2>เกี่ยวกับบริษัท</h2>
  <p>บริษัทเราก่อตั้งขึ้นในปี 2020...</p>
  <p>เรามีประสบการณ์ในการพัฒนา...</p>
</section>

<section>
  <h2>บริการของเรา</h2>
  <div class="services-grid">
    <div class="service-item">
      <h3>พัฒนาเว็บไซต์</h3>
      <p>รายละเอียดบริการ...</p>
    </div>
    <div class="service-item">
      <h3>ออกแบบ UI/UX</h3>
      <p>รายละเอียดบริการ...</p>
    </div>
  </div>
</section>

<!-- กรณีที่มี section ซ้อนกัน -->
<section>
  <h2>ผลิตภัณฑ์</h2>

  <section>
    <h3>เว็บแอปพลิเคชัน</h3>
    <p>รายละเอียดเว็บแอป...</p>
  </section>

  <section>
    <h3>แอปมือถือ</h3>
    <p>รายละเอียดแอปมือถือ...</p>
  </section>
</section>
```

### 1.2 `<div>` - Container สำหรับจัดกลุ่มและ styling

**เมื่อไหร่ควรใช้**:

- ต้องการจัดกลุ่มเพื่อ styling
- ไม่มีความหมายเชิงเนื้อหา
- เป็น wrapper หรือ container
- สำหรับ layout purposes

```html
<!-- ✅ ถูกต้อง: div สำหรับ layout และ styling -->
<section>
  <h2>ทีมงาน</h2>

  <!-- div สำหรับ layout -->
  <div class="team-grid">
    <div class="team-member">
      <img src="person1.jpg" alt="สมชาย ใจดี" />
      <h3>สมชาย ใจดี</h3>
      <p>นักพัฒนา Frontend</p>
    </div>

    <div class="team-member">
      <img src="person2.jpg" alt="สมหญิง สวยงาม" />
      <h3>สมหญิง สวยงาม</h3>
      <p>นักออกแบบ UI/UX</p>
    </div>
  </div>
</section>

<!-- div สำหรับ wrapper -->
<div class="container">
  <div class="row">
    <div class="col-md-8">
      <main>
        <!-- เนื้อหาหลัก -->
      </main>
    </div>
    <div class="col-md-4">
      <aside>
        <!-- sidebar -->
      </aside>
    </div>
  </div>
</div>
```

### 1.3 เปรียบเทียบ `<section>` vs `<div>`

| แง่มุม            | `<section>`           | `<div>`              |
| ----------------- | --------------------- | -------------------- |
| **ความหมาย**      | มีความหมายเชิงเนื้อหา | ไม่มีความหมาย        |
| **Heading**       | ควรมี heading         | ไม่จำเป็น            |
| **Outline**       | สร้าง outline section | ไม่สร้าง outline     |
| **Screen Reader** | อ่านเป็น landmark     | ไม่อ่านเป็น landmark |
| **การใช้งาน**     | เนื้อหาที่มีหัวข้อ    | Layout, styling      |

```html
<!-- ❌ ผิด: ใช้ div แทน section -->
<div>
  <h2>ข่าวสาร</h2>
  <p>ข่าวสารล่าสุด...</p>
</div>

<!-- ✅ ถูก: ใช้ section เพราะมี heading และเนื้อหาที่มีความหมาย -->
<section>
  <h2>ข่าวสาร</h2>
  <p>ข่าวสารล่าสุด...</p>
</section>

<!-- ❌ ผิด: ใช้ section เพื่อ styling -->
<section class="red-background">
  <p>ข้อความสีแดง</p>
</section>

<!-- ✅ ถูก: ใช้ div เพื่อ styling -->
<div class="red-background">
  <p>ข้อความสีแดง</p>
</div>
```

---

## 2. `<article>` vs `<section>` - เมื่อไหร่ควรใช้อะไร

### 2.1 `<article>` - เนื้อหาที่สมบูรณ์และแยกได้

**เมื่อไหร่ควรใช้**:

- เนื้อหาสมบูรณ์ในตัวเอง
- สามารถนำไปใช้ที่อื่นได้ (syndicated)
- เป็นโพสต์, บทความ, ข่าว, ความคิดเห็น
- มีความหมายแม้จะแยกออกจากเว็บไซต์

```html
<!-- ✅ ถูกต้อง: article สำหรับบทความ -->
<article>
  <header>
    <h2>วิธีการพัฒนาเว็บไซต์ที่ดี</h2>
    <p class="meta">
      โดย <span class="author">นาย ก.</span> เมื่อ
      <time datetime="2024-01-15">15 มกราคม 2024</time>
    </p>
  </header>

  <section>
    <h3>บทนำ</h3>
    <p>การพัฒนาเว็บไซต์ที่ดีต้องมีหลายปัจจัย...</p>
  </section>

  <section>
    <h3>ขั้นตอนการพัฒนา</h3>
    <ol>
      <li>วางแผนและวิเคราะห์</li>
      <li>ออกแบบ UI/UX</li>
      <li>พัฒนาระบบ</li>
    </ol>
  </section>

  <footer>
    <p>แท็ก: #webdev #html #css</p>
  </footer>
</article>

<!-- article สำหรับข่าว -->
<article>
  <h2>บริษัทเปิดตัวผลิตภัณฑ์ใหม่</h2>
  <p class="dateline">กรุงเทพฯ, 15 มกราคม 2024</p>
  <p>บริษัท ABC ประกาศเปิดตัวผลิตภัณฑ์ใหม่...</p>
</article>

<!-- article สำหรับ comment -->
<article class="comment">
  <header>
    <h4>ความคิดเห็นโดย สมชาย</h4>
    <time datetime="2024-01-15T10:30">10:30 น.</time>
  </header>
  <p>บทความนี้มีประโยชน์มาก ขอบคุณครับ</p>
</article>
```

### 2.2 `<section>` - ส่วนของเนื้อหาในบริบทเดียวกัน

**เมื่อไหร่ควรใช้**:

- เป็นส่วนหนึ่งของเนื้อหาใหญ่
- แยกจากบริบทแล้วอาจไม่มีความหมาย
- เป็นการแบ่งส่วนเนื้อหาตามหัวข้อ
- ใช้ภายใน article หรือ main

```html
<!-- ✅ ถูกต้อง: section ภายใน article -->
<article>
  <h1>คู่มือการใช้งาน JavaScript</h1>

  <section>
    <h2>พื้นฐาน JavaScript</h2>
    <p>JavaScript เป็นภาษาโปรแกรมมิ่ง...</p>
  </section>

  <section>
    <h2>Variables และ Data Types</h2>
    <p>การประกาศตัวแปรใน JavaScript...</p>
  </section>

  <section>
    <h2>Functions</h2>
    <p>การสร้างและใช้งาน function...</p>
  </section>
</article>

<!-- section ในหน้าหลัก -->
<main>
  <section>
    <h2>บริการหลัก</h2>
    <p>เราให้บริการด้านเทคโนโลยี...</p>
  </section>

  <section>
    <h2>ทำไมเลือกเรา</h2>
    <p>เหตุผลที่ลูกค้าเลือกใช้บริการ...</p>
  </section>
</main>
```

### 2.3 เปรียบเทียบ `<article>` vs `<section>`

| แง่มุม          | `<article>`          | `<section>`              |
| --------------- | -------------------- | ------------------------ |
| **ความสมบูรณ์** | สมบูรณ์ในตัวเอง      | ส่วนหนึ่งของเนื้อหาใหญ่  |
| **การแยกใช้**   | แยกไปใช้ที่อื่นได้   | ต้องอยู่ในบริบทเดิม      |
| **ตัวอย่าง**    | บทความ, ข่าว, โพสต์  | บทใน article, ส่วนในหน้า |
| **ความซ้อน**    | อาจมี section ข้างใน | ไม่ควรมี article ข้างใน  |

```html
<!-- ❌ ผิด: ใช้ section แทน article -->
<section>
  <h2>บทความเรื่อง CSS Grid</h2>
  <p>โดย นาย ข. เมื่อ 15 ม.ค. 2024</p>
  <p>CSS Grid เป็นเครื่องมือที่ทรงพลัง...</p>
  <!-- บทความสมบูรณ์ ควรใช้ article -->
</section>

<!-- ✅ ถูก: ใช้ article สำหรับบทความ -->
<article>
  <h2>บทความเรื่อง CSS Grid</h2>
  <p>โดย นาย ข. เมื่อ 15 ม.ค. 2024</p>
  <p>CSS Grid เป็นเครื่องมือที่ทรงพลัง...</p>
</article>

<!-- ❌ ผิด: ใช้ article แทน section -->
<article>
  <h2>ขั้นตอนที่ 1: การวางแผน</h2>
  <p>ขั้นตอนแรกในการพัฒนา...</p>
  <!-- เป็นเพียงส่วนหนึ่ง ควรใช้ section -->
</article>

<!-- ✅ ถูก: ใช้ section สำหรับส่วนหนึ่ง -->
<section>
  <h2>ขั้นตอนที่ 1: การวางแผน</h2>
  <p>ขั้นตอนแรกในการพัฒนา...</p>
</section>
```

---

## 3. ข้อผิดพลาดที่พบบ่อย

### 3.1 ❌ ใช้ `<div>` ไปหมดทุกอย่าง (Div Soup)

**ปัญหา**: ไม่ใช้ semantic elements ทำให้สูญเสียความหมาย

```html
<!-- ❌ ผิด: ใช้ div ทุกอย่าง -->
<div class="header">
  <div class="logo">
    <h1>ชื่อเว็บไซต์</h1>
  </div>
  <div class="navigation">
    <ul>
      <li><a href="/">หน้าแรก</a></li>
      <li><a href="/about">เกี่ยวกับ</a></li>
    </ul>
  </div>
</div>

<div class="main-content">
  <div class="article">
    <div class="article-header">
      <h2>หัวข้อบทความ</h2>
      <div class="meta">วันที่ 15 มกราคม 2024</div>
    </div>
    <div class="article-content">
      <p>เนื้อหาบทความ...</p>
    </div>
  </div>

  <div class="sidebar">
    <div class="widget">
      <h3>บทความยอดนิยม</h3>
      <ul>
        <li><a href="/popular-1">บทความ 1</a></li>
      </ul>
    </div>
  </div>
</div>

<div class="footer">
  <div class="copyright">
    <p>&copy; 2024 บริษัท</p>
  </div>
</div>
```

**✅ การแก้ไข**: ใช้ semantic elements

```html
<!-- ✅ ถูก: ใช้ semantic elements -->
<header>
  <div class="logo">
    <h1>ชื่อเว็บไซต์</h1>
  </div>
  <nav>
    <ul>
      <li><a href="/">หน้าแรก</a></li>
      <li><a href="/about">เกี่ยวกับ</a></li>
    </ul>
  </nav>
</header>

<main>
  <article>
    <header>
      <h2>หัวข้อบทความ</h2>
      <p class="meta">วันที่ 15 มกราคม 2024</p>
    </header>
    <div class="article-content">
      <p>เนื้อหาบทความ...</p>
    </div>
  </article>

  <aside>
    <section>
      <h3>บทความยอดนิยม</h3>
      <ul>
        <li><a href="/popular-1">บทความ 1</a></li>
      </ul>
    </section>
  </aside>
</main>

<footer>
  <div class="copyright">
    <p>&copy; 2024 บริษัท</p>
  </div>
</footer>
```

### 3.2 ❌ มีหลาย `<main>` ในหน้าเดียว

**ปัญหา**: แต่ละหน้าควรมี `<main>` เพียง 1 อันเท่านั้น

```html
<!-- ❌ ผิด: มี main หลายอัน -->
<!DOCTYPE html>
<html>
  <body>
    <header>
      <h1>เว็บไซต์</h1>
    </header>

    <main>
      <h2>ข่าวสาร</h2>
      <article>
        <h3>ข่าวที่ 1</h3>
        <p>เนื้อหาข่าว...</p>
      </article>
    </main>

    <main>
      <h2>บทความ</h2>
      <article>
        <h3>บทความที่ 1</h3>
        <p>เนื้อหาบทความ...</p>
      </article>
    </main>

    <footer>
      <p>&copy; 2024</p>
    </footer>
  </body>
</html>
```

**✅ การแก้ไข**: ใช้ `<main>` เพียงอันเดียวและใช้ `<section>` แบ่งส่วน

```html
<!-- ✅ ถูก: main เพียงอันเดียว -->
<!DOCTYPE html>
<html>
  <body>
    <header>
      <h1>เว็บไซต์</h1>
    </header>

    <main>
      <section>
        <h2>ข่าวสาร</h2>
        <article>
          <h3>ข่าวที่ 1</h3>
          <p>เนื้อหาข่าว...</p>
        </article>
      </section>

      <section>
        <h2>บทความ</h2>
        <article>
          <h3>บทความที่ 1</h3>
          <p>เนื้อหาบทความ...</p>
        </article>
      </section>
    </main>

    <footer>
      <p>&copy; 2024</p>
    </footer>
  </body>
</html>
```

**กรณีพิเศษ**: หน้าที่มีเนื้อหาหลักหลายส่วนที่แยกกันอย่างชัดเจน

```html
<!-- ✅ ทางเลือก: ใช้ multiple sections ใน main เดียว -->
<main>
  <div class="content-wrapper">
    <section class="news-section">
      <h2>ข่าวสาร</h2>
      <!-- ข่าวสาร -->
    </section>

    <section class="articles-section">
      <h2>บทความ</h2>
      <!-- บทความ -->
    </section>
  </div>
</main>
```

### 3.3 ❌ ใช้ `<section>` โดยไม่มี heading ภายใน

**ปัญหา**: `<section>` ควรมี heading เพื่อระบุหัวข้อของส่วนนั้น

```html
<!-- ❌ ผิด: section ไม่มี heading -->
<section>
  <p>นี่คือข้อความบางส่วน</p>
  <p>และข้อความเพิ่มเติม</p>
</section>

<section>
  <div class="image-gallery">
    <img src="photo1.jpg" alt="รูปที่ 1" />
    <img src="photo2.jpg" alt="รูปที่ 2" />
  </div>
</section>

<section class="red-background">
  <p>ข้อความที่มีพื้นหลังสีแดง</p>
</section>
```

**✅ การแก้ไข**: เพิ่ม heading หรือใช้ `<div>` แทน

```html
<!-- ✅ ถูก: section พร้อม heading -->
<section>
  <h2>คำอธิบาย</h2>
  <p>นี่คือข้อความบางส่วน</p>
  <p>และข้อความเพิ่มเติม</p>
</section>

<section>
  <h2>แกลเลอรี่ภาพ</h2>
  <div class="image-gallery">
    <img src="photo1.jpg" alt="รูปที่ 1" />
    <img src="photo2.jpg" alt="รูปที่ 2" />
  </div>
</section>

<!-- หรือใช้ div หากไม่มี heading -->
<div class="red-background">
  <p>ข้อความที่มีพื้นหลังสีแดง</p>
</div>
```

**กรณีพิเศษ**: หาก heading ไม่เหมาะสมกับ design

```html
<!-- ใช้ visually hidden heading -->
<section>
  <h2 class="visually-hidden">ข้อมูลติดต่อ</h2>
  <address>
    <p>โทร: 02-123-4567</p>
    <p>อีเมล: info@company.com</p>
  </address>
</section>

<!-- CSS สำหรับ visually hidden -->
<style>
  .visually-hidden {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border: 0;
  }
</style>
```

### 3.4 ❌ ข้อผิดพลาดอื่นๆ

#### การใช้ `<header>` และ `<footer>` ผิดที่

```html
<!-- ❌ ผิด: header/footer ในที่ผิด -->
<article>
  <p>เนื้อหาบทความ...</p>
  <header>
    <h2>หัวข้อบทความ</h2>
  </header>
  <!-- header ควรอยู่ด้านบน -->
</article>

<!-- ✅ ถูก: header ด้านบน, footer ด้านล่าง -->
<article>
  <header>
    <h2>หัวข้อบทความ</h2>
    <p class="meta">วันที่ 15 มกราคม 2024</p>
  </header>

  <p>เนื้อหาบทความ...</p>

  <footer>
    <p>แท็ก: #เทคโนโลยี #เว็บไซต์</p>
  </footer>
</article>
```

#### การใช้ semantic elements เพื่อ styling

```html
<!-- ❌ ผิด: ใช้ semantic elements เพื่อ styling -->
<section class="blue-box">
  <p>ข้อความในกล่องสีน้ำเงิน</p>
</section>

<article class="card">
  <p>ข้อความในการ์ด</p>
</article>

<!-- ✅ ถูก: ใช้ div เพื่อ styling -->
<div class="blue-box">
  <p>ข้อความในกล่องสีน้ำเงิน</p>
</div>

<div class="card">
  <p>ข้อความในการ์ด</p>
</div>
```

---

## 4. แนวทางปฏิบัติที่ดี

### 4.1 การตัดสินใจเลือก Element

**ลำดับการพิจารณา**:

1. **มีความหมายเชิงเนื้อหาหรือไม่?**

   - ใช่ → เลือก semantic element
   - ไม่ → ใช้ `<div>` หรือ `<span>`

2. **เป็นเนื้อหาที่สมบูรณ์หรือไม่?**

   - ใช่ → `<article>`
   - ไม่ → `<section>` หรือ element อื่น

3. **มีหัวข้อหรือไม่?**

   - ใช่ → `<section>`
   - ไม่ → `<div>`

4. **เป็น navigation หรือไม่?**

   - ใช่ → `<nav>`

5. **เป็นเนื้อหาเสริมหรือไม่?**
   - ใช่ → `<aside>`

```html
<!-- ตัวอย่างการตัดสินใจ -->

<!-- เนื้อหาสมบูรณ์ + มีหัวข้อ = article -->
<article>
  <h2>วิธีทำอาหารไทย</h2>
  <p>ส่วนผสม: ...</p>
  <p>วิธีทำ: ...</p>
</article>

<!-- เนื้อหาไม่สมบูรณ์ + มีหัวข้อ = section -->
<section>
  <h2>ขั้นตอนที่ 1</h2>
  <p>เตรียมส่วนผสม</p>
</section>

<!-- ไม่มีความหมายเชิงเนื้อหา = div -->
<div class="container">
  <div class="row">
    <!-- layout elements -->
  </div>
</div>
```

### 4.2 โครงสร้างที่แนะนำ

```html
<!DOCTYPE html>
<html lang="th">
  <head>
    <meta charset="UTF-8" />
    <title>ตัวอย่างโครงสร้างที่ดี</title>
  </head>
  <body>
    <!-- Banner landmark -->
    <header>
      <div class="container">
        <div class="logo">
          <h1>ชื่อเว็บไซต์</h1>
        </div>

        <!-- Navigation landmark -->
        <nav aria-label="เมนูหลัก">
          <ul>
            <li><a href="/">หน้าแรก</a></li>
            <li><a href="/about">เกี่ยวกับ</a></li>
          </ul>
        </nav>
      </div>
    </header>

    <!-- Main content landmark -->
    <main>
      <div class="container">
        <!-- Article for complete content -->
        <article>
          <header>
            <h1>หัวข้อบทความหลัก</h1>
            <p class="meta">วันที่ 15 มกราคม 2024</p>
          </header>

          <!-- Sections within article -->
          <section>
            <h2>บทนำ</h2>
            <p>เนื้อหาบทนำ...</p>
          </section>

          <section>
            <h2>เนื้อหาหลัก</h2>

            <!-- Subsections -->
            <section>
              <h3>หัวข้อย่อย 1</h3>
              <p>รายละเอียด...</p>
            </section>

            <section>
              <h3>หัวข้อย่อย 2</h3>
              <p>รายละเอียด...</p>
            </section>
          </section>

          <section>
            <h2>สรุป</h2>
            <p>สรุปเนื้อหา...</p>
          </section>

          <footer>
            <p>แท็ก: #html #semantic</p>
          </footer>
        </article>
      </div>
    </main>

    <!-- Complementary content -->
    <aside>
      <div class="container">
        <section>
          <h2>บทความที่เกี่ยวข้อง</h2>
          <ul>
            <li><a href="/article-1">บทความ 1</a></li>
            <li><a href="/article-2">บทความ 2</a></li>
          </ul>
        </section>

        <section>
          <h2>หมวดหมู่</h2>
          <ul>
            <li><a href="/category/html">HTML</a></li>
            <li><a href="/category/css">CSS</a></li>
          </ul>
        </section>
      </div>
    </aside>

    <!-- Content info landmark -->
    <footer>
      <div class="container">
        <section>
          <h2>ติดต่อเรา</h2>
          <address>
            <p>โทร: 02-123-4567</p>
            <p>อีเมล: info@example.com</p>
          </address>
        </section>

        <div class="copyright">
          <p>&copy; 2024 ชื่อบริษัท สงวนลิขสิทธิ์</p>
        </div>
      </div>
    </footer>
  </body>
</html>
```

---

## 5. เครื่องมือตรวจสอบ

### 5.1 HTML Validator

```html
<!-- ตรวจสอบ syntax และ structure -->
<!-- https://validator.w3.org/ -->

<!-- ตัวอย่างที่ผิด -->
<section>
  <article>
    <section>
      <p>เนื้อหาโดยไม่มี heading</p>
    </section>
  </article>
</section>
```

### 5.2 Accessibility Checkers

```html
<!-- ใช้ tools เช่น -->
<!-- - axe DevTools -->
<!-- - WAVE -->
<!-- - Lighthouse -->

<!-- ตรวจสอบ landmarks และ headings structure -->
```

### 5.3 HTML5 Outliner

```html
<!-- ตรวจสอบ document outline -->
<!-- https://gsnedders.html5.org/outliner/ -->

<!-- ควรได้ outline ที่ชัดเจน -->
<!--
1. หัวข้อหลัก
   1.1 หัวข้อย่อย 1
   1.2 หัวข้อย่อย 2
2. หัวข้อที่ 2
-->
```

---

## 6. Checklist การตรวจสอบ

### ✅ รายการตรวจสอบ Semantic Elements

- [ ] ใช้ `<header>`, `<nav>`, `<main>`, `<aside>`, `<footer>` แทน `<div>`
- [ ] มี `<main>` เพียง 1 อันต่อหน้า
- [ ] ทุก `<section>` มี heading (h1-h6)
- [ ] ใช้ `<article>` สำหรับเนื้อหาที่สมบูรณ์
- [ ] ใช้ `<section>` สำหรับส่วนที่มีหัวข้อ
- [ ] ใช้ `<div>` เฉพาะเมื่อไม่มี semantic meaning
- [ ] Headings มีลำดับที่ถูกต้อง (h1 → h2 → h3)
- [ ] Document outline สมเหตุสมผล
- [ ] ผ่านการตรวจสอบ HTML validator
- [ ] ผ่านการทดสอบ accessibility tools

### ❌ สิ่งที่ควรหลีกเลี่ยง

- [ ] ไม่ใช้ `<div>` ทุกอย่าง (div soup)
- [ ] ไม่มี `<main>` หลายอัน
- [ ] ไม่ใช้ `<section>` โดยไม่มี heading
- [ ] ไม่ใช้ semantic elements เพื่อ styling
- [ ] ไม่ข้าม heading levels (h1 → h3)
- [ ] ไม่ใช้ `<article>` สำหรับเนื้อหาที่ไม่สมบูรณ์

---

## สรุป

### หลักการสำคัญ

1. **ความหมายเป็นสำคัญ**: เลือก element ตามความหมายของเนื้อหา ไม่ใช่ลักษณะการแสดงผล

2. **Headings structure**: ทุก `<section>` ควรมี heading และรักษาลำดับ h1-h6

3. **Document outline**: โครงสร้างเอกสารควรสมเหตุสมผล

4. **Accessibility**: ช่วยให้ assistive technology เข้าใจโครงสร้างได้ดี

5. **Maintainability**: โค้ดอ่านและบำรุงรักษาง่าย

### การเลือกใช้

- **`<div>`**: Layout, styling, grouping ที่ไม่มีความหมาย
- **`<section>`**: ส่วนที่มีหัวข้อ, เป็นส่วนหนึ่งของเนื้อหาใหญ่
- **`<article>`**: เนื้อหาสมบูรณ์, สามารถแยกไปใช้ที่อื่นได้

การใช้ semantic elements อย่างถูกต้องจะทำให้เว็บไซต์มีคุณภาพ เข้าถึงได้ และปฏิบัติตามมาตรฐานสากล
