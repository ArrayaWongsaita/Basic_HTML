# Semantic Elements อื่นๆ: `<address>` และ `<time>`

## ภาพรวม

นอกจาก layout elements หลักแล้ว HTML ยังมี semantic elements อื่นๆ ที่ช่วยให้เนื้อหามีความหมายชัดเจนขึ้น โดยเฉพาะ:

1. **`<address>`** - สำหรับข้อมูลการติดต่อ
2. **`<time>`** - สำหรับข้อมูลวันที่และเวลา

Elements เหล่านี้ช่วยให้:

- **Search Engines** เข้าใจข้อมูลได้ดีขึ้น
- **Screen Readers** อ่านข้อมูลได้ถูกต้อง
- **Browsers** สามารถจัดการข้อมูลได้อย่างเหมาะสม

---

## 1. `<address>` Element

### คำอธิบาย

`<address>` element ใช้สำหรับแสดงข้อมูลการติดต่อของ:

- **เจ้าของเอกสาร** หรือ **ผู้เขียนบทความ**
- **บุคคลหรือองค์กร** ที่เกี่ยวข้องกับเนื้อหา
- **ข้อมูลติดต่อของเว็บไซต์**

### สิ่งที่ควรใส่ใน `<address>`

✅ **เหมาะสม:**

- ที่อยู่ทางไปรษณีย์
- หมายเลขโทรศัพท์
- อีเมล
- URL ของเว็บไซต์
- ข้อมูลโซเชียลมีเดีย

❌ **ไม่เหมาะสม:**

- ที่อยู่ในบทความ (เช่น ที่อยู่ของสถานที่ท่องเที่ยว)
- ข้อมูลการติดต่อของบุคคลอื่นที่ไม่เกี่ยวข้องกับเนื้อหา

### ไวยากรณ์

```html
<address>
  <!-- ข้อมูลการติดต่อ -->
</address>
```

### ตัวอย่างการใช้งาน

#### ข้อมูลติดต่อของเว็บไซต์

```html
<address>
  <strong>บริษัท ABC Technology จำกัด</strong><br />
  123 ถนนสุขุมวิท แขวงคลองเตย<br />
  เขตคลองเตย กรุงเทพมหานคร 10110<br />
  โทรศัพท์: <a href="tel:+6621234567">02-123-4567</a><br />
  อีเมล: <a href="mailto:info@abc.com">info@abc.com</a><br />
  เว็บไซต์: <a href="https://www.abc.com">www.abc.com</a>
</address>
```

#### ข้อมูลติดต่อของผู้เขียนบทความ

```html
<article>
  <header>
    <h1>เทคนิคการเขียน HTML ที่มีประสิทธิภาพ</h1>
  </header>

  <div class="content">
    <!-- เนื้อหาบทความ -->
    <p>HTML เป็นภาษาพื้นฐานที่สำคัญสำหรับการสร้างเว็บไซต์...</p>
  </div>

  <footer>
    <address>
      เขียนโดย: <a href="mailto:john@example.com">จอห์น สมิธ</a><br />
      นักพัฒนาเว็บไซต์อาวุโส<br />
      ติดต่อ: <a href="tel:+66812345678">081-234-5678</a><br />
      LinkedIn:
      <a href="https://linkedin.com/in/johnsmith">linkedin.com/in/johnsmith</a>
    </address>
  </footer>
</article>
```

#### ข้อมูลติดต่อในส่วน Footer

```html
<footer class="site-footer">
  <div class="contact-section">
    <h3>ติดต่อเรา</h3>
    <address>
      <div class="address-line">
        <strong>สำนักงานใหญ่</strong><br />
        456 ถนนพระราม 4 แขวงสุริยวงศ์<br />
        เขตบางรัก กรุงเทพมหานคร 10500
      </div>

      <div class="contact-methods">
        <p>📞 โทรศัพท์: <a href="tel:+6622345678">02-234-5678</a></p>
        <p>📠 แฟกซ์: <a href="tel:+6622345679">02-234-5679</a></p>
        <p>
          📧 อีเมล: <a href="mailto:contact@company.com">contact@company.com</a>
        </p>
        <p>
          🌐 เว็บไซต์: <a href="https://www.company.com">www.company.com</a>
        </p>
      </div>

      <div class="business-hours">
        <strong>เวลาทำการ:</strong><br />
        จันทร์ - ศุกร์: 9:00 - 18:00 น.<br />
        เสาร์: 9:00 - 12:00 น.<br />
        อาทิตย์: ปิด
      </div>
    </address>
  </div>
</footer>
```

#### ข้อมูลติดต่อหลายสาขา

```html
<section class="branches">
  <h2>สาขาของเรา</h2>

  <div class="branch">
    <h3>สาขากรุงเทพฯ</h3>
    <address>
      789 ถนนสีลม แขวงสีลม<br />
      เขตบางรัก กรุงเทพมหานคร 10500<br />
      โทร: <a href="tel:+6622876543">02-287-6543</a><br />
      อีเมล: <a href="mailto:bangkok@company.com">bangkok@company.com</a>
    </address>
  </div>

  <div class="branch">
    <h3>สาขาเชียงใหม่</h3>
    <address>
      321 ถนนนิมมานเหมินท์<br />
      ตำบลสุเทพ อำเภอเมือง เชียงใหม่ 50200<br />
      โทร: <a href="tel:+6653123456">053-123-456</a><br />
      อีเมล: <a href="mailto:chiangmai@company.com">chiangmai@company.com</a>
    </address>
  </div>
</section>
```

### การจัดรูปแบบ `<address>` ด้วย CSS

```css
/* รูปแบบพื้นฐาน */
address {
  font-style: normal; /* ลบ italic ที่เป็นค่าเริ่มต้น */
  line-height: 1.6;
  margin: 1rem 0;
}

/* สไตล์สำหรับ footer */
.site-footer address {
  background-color: #f8f9fa;
  padding: 1.5rem;
  border-left: 4px solid #007bff;
  border-radius: 0.25rem;
}

/* สไตล์สำหรับลิงก์ในข้อมูลติดต่อ */
address a {
  color: #007bff;
  text-decoration: none;
}

address a:hover {
  text-decoration: underline;
}

/* ไอคอนสำหรับข้อมูลติดต่อ */
.contact-methods p:before {
  content: attr(data-icon);
  margin-right: 0.5rem;
}
```

---

## 2. `<time>` Element

### คำอธิบาย

`<time>` element ใช้สำหรับแสดงข้อมูลวันที่และเวลาในรูปแบบที่เครื่องจักรอ่านได้ ประกอบด้วย:

- **วันที่และเวลา**
- **ช่วงเวลา**
- **ปีหรือเดือน**

### Attributes สำคัญ

#### `datetime`

ระบุวันที่และเวลาในรูปแบบมาตรฐาน ISO 8601

```html
<time datetime="2024-01-15">15 มกราคม 2024</time>
<time datetime="2024-01-15T14:30:00">15 มกราคม 2024 เวลา 14:30</time>
```

#### `pubdate` (เลิกใช้แล้ว)

ใน HTML5 เดิมมี `pubdate` attribute แต่ปัจจุบันเลิกใช้แล้ว

### รูปแบบ datetime ที่ถูกต้อง

```html
<!-- วันที่เท่านั้น -->
<time datetime="2024-01-15">15 มกราคม 2024</time>

<!-- วันที่และเวลา -->
<time datetime="2024-01-15T14:30:00">15 มกราคม 2024 เวลา 14:30</time>

<!-- วันที่และเวลาพร้อม timezone -->
<time datetime="2024-01-15T14:30:00+07:00"
  >15 มกราคม 2024 เวลา 14:30 (เวลาไทย)</time
>

<!-- เดือนและปี -->
<time datetime="2024-01">มกราคม 2024</time>

<!-- ปีเท่านั้น -->
<time datetime="2024">ปี 2024</time>

<!-- เวลาเท่านั้น -->
<time datetime="14:30">14:30 น.</time>

<!-- ระยะเวลา (Duration) -->
<time datetime="PT2H30M">2 ชั่วโมง 30 นาที</time>
```

### ตัวอย่างการใช้งาน

#### วันที่เผยแพร่บทความ

```html
<article>
  <header>
    <h1>ข่าวสารล่าสุดเกี่ยวกับเทคโนโลยี</h1>
    <p class="meta">
      เผยแพร่เมื่อ:
      <time datetime="2024-01-15T09:00:00+07:00">
        15 มกราคม 2024 เวลา 9:00 น.
      </time>
    </p>
  </header>

  <div class="content">
    <!-- เนื้อหาบทความ -->
  </div>

  <footer>
    <p>
      อัปเดตล่าสุด:
      <time datetime="2024-01-16T16:45:00+07:00">
        16 มกราคม 2024 เวลา 16:45 น.
      </time>
    </p>
  </footer>
</article>
```

#### กำหนดการและอีเวนต์

```html
<section class="events">
  <h2>กิจกรรมที่จะมาถึง</h2>

  <article class="event">
    <h3>สัมมนาเรื่อง Web Development</h3>
    <p class="event-details">
      วันที่: <time datetime="2024-02-20">20 กุมภาพันธ์ 2024</time><br />
      เวลา: <time datetime="13:00">13:00</time> -
      <time datetime="17:00">17:00 น.</time><br />
      ระยะเวลา: <time datetime="PT4H">4 ชั่วโมง</time>
    </p>
  </article>

  <article class="event">
    <h3>Workshop: React Fundamentals</h3>
    <p class="event-details">
      วันที่: <time datetime="2024-03-15">15 มีนาคม 2024</time><br />
      เวลา: <time datetime="09:00">09:00</time> -
      <time datetime="16:00">16:00 น.</time><br />
      ระยะเวลา: <time datetime="PT7H">7 ชั่วโมง</time> (รวมพักเที่ยง)
    </p>
  </article>
</section>
```

#### ประวัติและไทม์ไลน์

```html
<section class="timeline">
  <h2>ประวัติของบริษัท</h2>

  <div class="timeline-item">
    <time datetime="2010">2010</time>
    <h3>ก่อตั้งบริษัท</h3>
    <p>เริ่มต้นธุรกิจด้วยทีมงาน 5 คน</p>
  </div>

  <div class="timeline-item">
    <time datetime="2015-06">มิถุนายน 2015</time>
    <h3>ขยายสาขา</h3>
    <p>เปิดสาขาใหม่ในเชียงใหม่</p>
  </div>

  <div class="timeline-item">
    <time datetime="2020-01-15">15 มกราคม 2020</time>
    <h3>เปิดตัวผลิตภัณฑ์ใหม่</h3>
    <p>เปิดตัวแพลตฟอร์ม SaaS สำหรับ SME</p>
  </div>
</section>
```

#### ความคิดเห็นและรีวิว

```html
<section class="reviews">
  <h2>รีวิวจากลูกค้า</h2>

  <article class="review">
    <header>
      <h3>รีวิวเยี่ยมมาก!</h3>
      <div class="review-meta">
        <span class="reviewer">โดย: สมชาย ใจดี</span>
        <time datetime="2024-01-10T14:20:00+07:00">
          10 มกราคม 2024 เวลา 14:20
        </time>
      </div>
    </header>

    <div class="review-content">
      <p>บริการดีมาก ทีมงานใส่ใจในรายละเอียด...</p>
    </div>
  </article>

  <article class="review">
    <header>
      <h3>แนะนำเลย</h3>
      <div class="review-meta">
        <span class="reviewer">โดย: สมหญิง สวยงาม</span>
        <time datetime="2024-01-08T11:45:00+07:00">
          8 มกราคม 2024 เวลา 11:45
        </time>
      </div>
    </header>

    <div class="review-content">
      <p>ได้ผลลัพธ์ตามที่ต้องการ จะใช้บริการอีก...</p>
    </div>
  </article>
</section>
```

### การจัดรูปแบบ `<time>` ด้วย CSS

```css
/* รูปแบบพื้นฐาน */
time {
  font-weight: 500;
  color: #6c757d;
}

/* สไตล์สำหรับวันที่เผยแพร่ */
.meta time {
  background-color: #e9ecef;
  padding: 0.25rem 0.5rem;
  border-radius: 0.25rem;
  font-size: 0.875rem;
}

/* สไตล์สำหรับไทม์ไลน์ */
.timeline-item time {
  display: inline-block;
  background-color: #007bff;
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 1rem;
  font-weight: bold;
  margin-bottom: 0.5rem;
}

/* สไตล์สำหรับอีเวนต์ */
.event-details time {
  font-family: 'Courier New', monospace;
  background-color: #f8f9fa;
  padding: 0.125rem 0.25rem;
  border: 1px solid #dee2e6;
  border-radius: 0.125rem;
}

/* เอฟเฟ็กต์ hover */
time:hover {
  background-color: #007bff;
  color: white;
  transition: all 0.3s ease;
  cursor: help;
}
```

---

## 3. การใช้งานร่วมกับ JavaScript

### การจัดการ `<time>` element

```javascript
// หาทุก time elements
const timeElements = document.querySelectorAll('time[datetime]');

// แปลงเป็นรูปแบบที่อ่านง่าย
timeElements.forEach((timeEl) => {
  const datetime = timeEl.getAttribute('datetime');
  const date = new Date(datetime);

  // แสดงเวลาแบบ relative (เช่น "2 ชั่วโมงที่แล้ว")
  timeEl.title = getRelativeTime(date);
});

function getRelativeTime(date) {
  const now = new Date();
  const diffInMs = now - date;
  const diffInMinutes = Math.floor(diffInMs / (1000 * 60));

  if (diffInMinutes < 60) {
    return `${diffInMinutes} นาทีที่แล้ว`;
  } else if (diffInMinutes < 1440) {
    const hours = Math.floor(diffInMinutes / 60);
    return `${hours} ชั่วโมงที่แล้ว`;
  } else {
    const days = Math.floor(diffInMinutes / 1440);
    return `${days} วันที่แล้ว`;
  }
}
```

### การจัดการ `<address>` element

```javascript
// เพิ่มฟังก์ชันคลิกสำหรับข้อมูลติดต่อ
document.querySelectorAll('address a[href^="tel:"]').forEach((link) => {
  link.addEventListener('click', function (e) {
    // ตรวจสอบว่าอุปกรณ์รองรับการโทรหรือไม่
    if (!('ontouchstart' in window)) {
      e.preventDefault();
      alert('หมายเลขโทรศัพท์: ' + this.textContent);
    }
  });
});

// คัดลอกข้อมูลติดต่อ
function copyContactInfo(addressElement) {
  const contactText = addressElement.textContent.trim();
  navigator.clipboard.writeText(contactText).then(() => {
    alert('คัดลอกข้อมูลติดต่อแล้ว');
  });
}
```

---

## 4. Accessibility และ SEO

### การทำให้ `<address>` เข้าถึงได้

```html
<!-- เพิ่ม aria-label สำหรับความชัดเจน -->
<address aria-label="ข้อมูลติดต่อบริษัท">
  <strong>บริษัท ABC จำกัด</strong><br />
  <span itemprop="streetAddress">123 ถนนสุขุมวิท</span><br />
  <span itemprop="addressLocality">กรุงเทพมหานคร</span>
  <span itemprop="postalCode">10110</span><br />
  โทร: <a href="tel:+6621234567" itemprop="telephone">02-123-4567</a><br />
  อีเมล: <a href="mailto:info@abc.com" itemprop="email">info@abc.com</a>
</address>
```

### การทำให้ `<time>` เข้าถึงได้

```html
<!-- เพิ่ม aria-label สำหรับ screen readers -->
<time
  datetime="2024-01-15T14:30:00+07:00"
  aria-label="15 มกราคม พ.ศ. 2567 เวลา 14 นาฬิกา 30 นาที"
>
  15/01/2024 14:30
</time>

<!-- ใช้ title attribute สำหรับข้อมูลเพิ่มเติม -->
<time datetime="2024-01-15" title="วันจันทร์ที่ 15 มกราคม พ.ศ. 2567">
  15 ม.ค. 67
</time>
```

### Schema.org Microdata

```html
<!-- การใช้ microdata สำหรับ SEO -->
<div itemscope itemtype="https://schema.org/Organization">
  <h1 itemprop="name">บริษัท ABC จำกัด</h1>

  <address
    itemprop="address"
    itemscope
    itemtype="https://schema.org/PostalAddress"
  >
    <span itemprop="streetAddress">123 ถนนสุขุมวิท</span><br />
    <span itemprop="addressLocality">กรุงเทพมหานคร</span>
    <span itemprop="postalCode">10110</span><br />
    <span itemprop="addressCountry">ประเทศไทย</span>
  </address>

  <p>โทร: <span itemprop="telephone">02-123-4567</span></p>
  <p>อีเมล: <span itemprop="email">info@abc.com</span></p>
</div>

<!-- Event schema -->
<div itemscope itemtype="https://schema.org/Event">
  <h2 itemprop="name">สัมมนา Web Development</h2>
  <time itemprop="startDate" datetime="2024-02-20T13:00:00+07:00">
    20 กุมภาพันธ์ 2024 เวลา 13:00
  </time>
  <time itemprop="endDate" datetime="2024-02-20T17:00:00+07:00">
    ถึง 17:00 น.
  </time>
</div>
```

---

## 5. เคล็ดลับและแนวทางปฏิบัติที่ดี

### สำหรับ `<address>`

✅ **ควรทำ:**

- ใช้สำหรับข้อมูลติดต่อที่เกี่ยวข้องกับเนื้อหา
- รวมลิงก์ที่ใช้งานได้ (tel:, mailto:)
- จัดรูปแบบให้อ่านง่าย
- เพิ่ม microdata สำหรับ SEO

❌ **ไม่ควรทำ:**

- ใช้สำหรับที่อยู่ในบทความทั่วไป
- ใส่ข้อมูลที่ไม่เกี่ยวกับการติดต่อ
- ทิ้งข้อมูลไว้ล้าสมัย

### สำหรับ `<time>`

✅ **ควรทำ:**

- ใช้ datetime attribute เสมอ
- ใช้รูปแบบ ISO 8601
- เพิ่ม timezone เมื่อจำเป็น
- ทำให้เข้าใจได้ง่ายสำหรับผู้ใช้

❌ **ไม่ควรทำ:**

- ลืมใส่ datetime attribute
- ใช้รูปแบบวันที่ที่ไม่ถูกต้อง
- ใส่ข้อมูลที่ไม่เกี่ยวกับเวลา

---

## สรุป

### `<address>` Element

- **วัตถุประสงค์**: แสดงข้อมูลการติดต่อที่เกี่ยวข้องกับเนื้อหา
- **ใช้สำหรับ**: ข้อมูลติดต่อของผู้เขียน, องค์กร, เว็บไซต์
- **ประโยชน์**: SEO ดีขึ้น, screen readers อ่านได้ดีขึ้น

### `<time>` Element

- **วัตถุประสงค์**: แสดงข้อมูลวันที่และเวลาที่เครื่องจักรอ่านได้
- **ใช้สำหรับ**: วันที่เผยแพร่, กำหนดการ, ไทม์ไลน์
- **ประโยชน์**: Search engines เข้าใจได้ดีขึ้น, JavaScript จัดการได้ง่าย

การใช้ semantic elements เหล่านี้อย่างถูกต้องจะทำให้เว็บไซต์มีความหมายชัดเจน เข้าถึงได้ง่าย และเป็นมิตรกับเครื่องมือค้นหา
