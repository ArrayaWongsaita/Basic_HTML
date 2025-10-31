# Lab Phase 4: Semantic Layout Structure - เฉลย
## 🎯 เฉลยการเติม HTML Semantic Tags

---

## 🏢 **Lab 1: เว็บไซต์บริษัท - เฉลย**

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>บริษัท ABC Technology</title>
</head>
<body>
    <header>
        <h1>ABC Technology</h1>
        <p>โซลูชันเทคโนโลยีสำหรับธุรกิจยุคใหม่</p>
        
        <nav>
            <ul>
                <li><a href="/">หน้าแรก</a></li>
                <li><a href="/about">เกี่ยวกับเรา</a></li>
                <li><a href="/services">บริการ</a></li>
                <li><a href="/contact">ติดต่อเรา</a></li>
            </ul>
        </nav>
    </header>
    
    <main>
        <section>
            <h2>บริการของเรา</h2>
            <p>เราให้บริการพัฒนาซอฟต์แวร์ครบวงจร</p>
            
            <article>
                <h3>พัฒนาเว็บไซต์</h3>
                <p>ออกแบบและพัฒนาเว็บไซต์ที่ทันสมัย</p>
            </article>
            
            <article>
                <h3>พัฒนาแอปมือถือ</h3>
                <p>สร้างแอปพลิเคชันมือถือสำหรับ iOS และ Android</p>
            </article>
        </section>
        
        <section>
            <h2>ข่าวสารล่าสุด</h2>
            
            <article>
                <h3>เปิดตัวบริการใหม่</h3>
                <p>เผยแพร่เมื่อ: <time datetime="2024-01-15">15 มกราคม 2024</time></p>
                <p>เราได้เปิดตัวบริการ Cloud Computing สำหรับลูกค้า</p>
            </article>
        </section>
        
        <aside>
            <h3>ติดต่อเรา</h3>
            <address>
                <p><strong>ABC Technology Co., Ltd.</strong></p>
                <p>123 ถนนเทคโนโลยี<br>
                กรุงเทพมหานคร 10110</p>
                <p>โทร: 02-123-4567</p>
                <p>อีเมล: info@abc-tech.com</p>
            </address>
        </aside>
    </main>
    
    <footer>
        <p>&copy; 2024 ABC Technology. สงวนลิขสิทธิ์.</p>
        <nav>
            <ul>
                <li><a href="/privacy">นโยบายความเป็นส่วนตัว</a></li>
                <li><a href="/terms">ข้อกำหนดการใช้งาน</a></li>
            </ul>
        </nav>
    </footer>
</body>
</html>
```

### **คำอธิบาย:**
- `<header>`: ส่วนหัวของหน้าเว็บ ประกอบด้วยโลโก้ ชื่อเว็บ และเมนูหลัก
- `<nav>`: เมนูนำทาง ใช้สำหรับลิงก์หลักของเว็บไซต์
- `<main>`: เนื้อหาหลักของหน้า มีได้เพียง 1 ตัวต่อหน้า
- `<section>`: กลุ่มเนื้อหาที่มีหัวข้อเฉพาะ
- `<article>`: เนื้อหาที่สมบูรณ์ในตัวเอง สามารถแยกออกไปได้
- `<aside>`: เนื้อหาเสริมข้างเคียง เช่น ข้อมูลติดต่อ
- `<footer>`: ส่วนท้ายของหน้าเว็บ
- `<address>`: ข้อมูลการติดต่อ
- `<time>`: วันที่และเวลา ควรระบุ `datetime` attribute

---

## 📰 **Lab 2: เว็บไซต์ข่าว/บล็อก - เฉลย**

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>TechNews Thailand</title>
</head>
<body>
    <header>
        <h1>TechNews Thailand</h1>
        <p>ข่าวเทคโนโลยีอัปเดตทุกวัน</p>
        
        <nav aria-label="เมนูหลัก">
            <ul>
                <li><a href="/">หน้าแรก</a></li>
                <li><a href="/tech">เทคโนโลยี</a></li>
                <li><a href="/reviews">รีวิว</a></li>
                <li><a href="/tutorials">บทความสอน</a></li>
            </ul>
        </nav>
    </header>
    
    <main>
        <section>
            <h2>ข่าวล่าสุด</h2>
            
            <article>
                <header>
                    <h2>Apple เปิดตัว iPhone 16 Pro Max</h2>
                    <p>โดย <strong>นักข่าวเทคโนโลยี</strong> | 
                    <time datetime="2024-09-10T14:30">10 กันยายน 2024 เวลา 14:30 น.</time></p>
                </header>
                
                <p>Apple ได้เปิดตัว iPhone รุ่นใหม่ล่าสุดพร้อมฟีเจอร์ที่น่าสนใจมากมาย</p>
                
                <p>จุดเด่นของ iPhone 16 Pro Max:</p>
                <ul>
                    <li>ชิป A18 Pro ประสิทธิภาพสูง</li>
                    <li>กล้อง 48MP พร้อม AI</li>
                    <li>แบตเตอรี่ใช้งานได้ 2 วัน</li>
                </ul>
                
                <footer>
                    <p>หมวดหมู่: <a href="/category/smartphone">สมาร์ทโฟน</a></p>
                </footer>
            </article>
            
            <hr>
            
            <article>
                <header>
                    <h2>Google เปิดตัว AI Gemini 2.0</h2>
                    <p>โดย <strong>ทีมข่าว AI</strong> | 
                    <time datetime="2024-09-09">9 กันยายน 2024</time></p>
                </header>
                
                <p>Google ประกาศเปิดตัว Gemini 2.0 โมเดล AI รุ่นใหม่ที่ทรงพลังกว่าเดิม</p>
                
                <footer>
                    <p>หมวดหมู่: <a href="/category/ai">ปัญญาประดิษฐ์</a></p>
                </footer>
            </article>
        </section>
        
        <aside>
            <section>
                <h3>บทความยอดนิยม</h3>
                <ol>
                    <li><a href="/article1">10 เทรนด์เทคโนโลยี 2024</a></li>
                    <li><a href="/article2">รีวิว MacBook Pro M3</a></li>
                    <li><a href="/article3">เรียน Python สำหรับมือใหม่</a></li>
                </ol>
            </section>
            
            <section>
                <h3>ติดตามเรา</h3>
                <ul>
                    <li><a href="https://facebook.com" target="_blank">Facebook</a></li>
                    <li><a href="https://twitter.com" target="_blank">Twitter</a></li>
                    <li><a href="https://youtube.com" target="_blank">YouTube</a></li>
                </ul>
            </section>
        </aside>
    </main>
    
    <footer>
        <section>
            <h3>เกี่ยวกับเรา</h3>
            <p>TechNews Thailand เป็นเว็บไซต์ข่าวเทคโนโลยีอันดับ 1 ของไทย</p>
        </section>
        
        <section>
            <h3>ติดต่อเรา</h3>
            <address>
                <p>อีเมล: <a href="mailto:contact@technews.com">contact@technews.com</a></p>
                <p>โทร: <a href="tel:02-234-5678">02-234-5678</a></p>
            </address>
        </section>
        
        <p><small>&copy; 2024 TechNews Thailand. All rights reserved.</small></p>
    </footer>
</body>
</html>
```

### **คำอธิบาย:**
- `<article>` ภายในมี `<header>` และ `<footer>` ของตัวเองได้
- `<aside>` ใช้สำหรับเนื้อหาเสริม เช่น บทความยอดนิยม โซเชียลมีเดีย
- `<section>` ภายใน `<aside>` แบ่งกลุ่มเนื้อหาเสริมย่อย
- `datetime` attribute ใน `<time>` ควรเป็นรูปแบบ ISO 8601
- `aria-label` ใน `<nav>` ช่วยให้ screen reader เข้าใจบริบทมากขึ้น
- `<hr>` ใช้แบ่งเนื้อหาระหว่างบทความ

---

## 🛒 **Lab 3: เว็บไซต์ E-Commerce - เฉลย**

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>TechStore - ร้านขายอุปกรณ์เทคโนโลยี</title>
</head>
<body>
    <header>
        <img src="logo.png" alt="TechStore Logo">
        <h1>TechStore</h1>
        
        <nav aria-label="เมนูหลัก">
            <ul>
                <li><a href="/">หน้าแรก</a></li>
                <li><a href="/products">สินค้า</a></li>
                <li><a href="/deals">โปรโมชั่น</a></li>
                <li><a href="/cart">ตะกร้า</a></li>
            </ul>
        </nav>
    </header>
    
    <main>
        <section>
            <header>
                <h2>สินค้าแนะนำ</h2>
            </header>
            
            <article>
                <header>
                    <h3>MacBook Pro M3 14"</h3>
                </header>
                
                <img src="macbook.jpg" alt="MacBook Pro M3 14 นิ้ว">
                
                <p><strong>ราคา: 52,900 บาท</strong></p>
                
                <p>คุณสมบัติ:</p>
                <ul>
                    <li>ชิป M3 Pro</li>
                    <li>RAM 18GB</li>
                    <li>SSD 512GB</li>
                </ul>
                
                <footer>
                    <p>เพิ่มเมื่อ: <time datetime="2024-09-01">1 กันยายน 2024</time></p>
                </footer>
            </article>
            
            <article>
                <header>
                    <h3>iPhone 15 Pro Max</h3>
                </header>
                
                <img src="iphone.jpg" alt="iPhone 15 Pro Max">
                
                <p><strong>ราคา: 42,900 บาท</strong></p>
                
                <p>คุณสมบัติ:</p>
                <ul>
                    <li>ชิป A17 Pro</li>
                    <li>กล้อง 48MP</li>
                    <li>จอ 6.7 นิ้ว</li>
                </ul>
            </article>
        </section>
        
        <section>
            <h2>โปรโมชั่นพิเศษ</h2>
            <p><mark>ลดสูงสุด 50%</mark> สำหรับสมาชิก</p>
            <p>ถึงวันที่: <time datetime="2024-12-31">31 ธันวาคม 2024</time></p>
        </section>
        
        <aside>
            <section>
                <h3>ตะกร้าสินค้า</h3>
                <p>สินค้าในตะกร้า: <strong>0</strong> ชิ้น</p>
                <p>รวมทั้งสิ้น: <strong>0</strong> บาท</p>
            </section>
            
            <section>
                <h3>หมวดหมู่สินค้า</h3>
                <nav aria-label="หมวดหมู่">
                    <ul>
                        <li><a href="/laptop">โน้ตบุ๊ก</a></li>
                        <li><a href="/smartphone">สมาร์ทโฟน</a></li>
                        <li><a href="/tablet">แท็บเล็ต</a></li>
                        <li><a href="/accessories">อุปกรณ์เสริม</a></li>
                    </ul>
                </nav>
            </section>
        </aside>
    </main>
    
    <footer>
        <section>
            <h3>ข้อมูลร้านค้า</h3>
            <address>
                <p><strong>TechStore Co., Ltd.</strong></p>
                <p>456 ถนนเทคโนโลยี<br>
                กรุงเทพมหานคร 10110</p>
                <p>โทร: <a href="tel:02-345-6789">02-345-6789</a></p>
                <p>เวลาทำการ: จันทร์-ศุกร์ 9:00-18:00 น.</p>
            </address>
        </section>
        
        <section>
            <h3>ลิงก์ด่วน</h3>
            <nav aria-label="ลิงก์เสริม">
                <ul>
                    <li><a href="/shipping">การจัดส่ง</a></li>
                    <li><a href="/returns">การคืนสินค้า</a></li>
                    <li><a href="/warranty">การรับประกัน</a></li>
                </ul>
            </nav>
        </section>
        
        <p><small>&copy; 2024 TechStore. สงวนลิขสิทธิ์.</small></p>
    </footer>
</body>
</html>
```

### **คำอธิบาย:**
- `<section>` สามารถมี `<header>` ได้เพื่อจัดกลุ่มหัวข้อและข้อมูลเมตา
- `<article>` ใช้สำหรับข้อมูลสินค้าแต่ละรายการ
- `<aside>` มีทั้งตะกร้าสินค้าและหมวดหมู่สินค้า
- สามารถมี `<nav>` หลายตัวได้ แต่ควรใส่ `aria-label` เพื่อแยกแยะ
- `<footer>` ภายใน `<section>` แบ่งข้อมูลเป็นหมวดหมู่
- `<address>` ใช้เฉพาะข้อมูลการติดต่อ ไม่ใช่ที่อยู่ทั่วไป

---

## 📖 **Lab 4: เว็บไซต์การศึกษา - เฉลย**

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>CodeAcademy - เรียนเขียนโปรแกรมออนไลน์</title>
</head>
<body>
    <header>
        <h1>CodeAcademy</h1>
        <p>เรียนเขียนโปรแกรมออนไลน์ฟรี</p>
        
        <nav aria-label="เมนูหลัก">
            <ul>
                <li><a href="/">หน้าแรก</a></li>
                <li><a href="/courses">หลักสูตร</a></li>
                <li><a href="/my-learning">การเรียนของฉัน</a></li>
                <li><a href="/community">ชุมชน</a></li>
            </ul>
        </nav>
    </header>
    
    <main>
        <article>
            <header>
                <h1>หลักสูตร Web Development สำหรับมือใหม่</h1>
                <p>อัปเดตล่าสุด: <time datetime="2024-09-15">15 กันยายน 2024</time></p>
                <p>ผู้สอน: <strong>อาจารย์สมชาย</strong></p>
            </header>
            
            <section>
                <h2>เกี่ยวกับหลักสูตร</h2>
                <p>หลักสูตรนี้จะสอนพื้นฐานการพัฒนาเว็บไซต์ตั้งแต่เริ่มต้น</p>
                
                <p>สิ่งที่จะได้เรียนรู้:</p>
                <ul>
                    <li>HTML และ CSS พื้นฐาน</li>
                    <li>JavaScript เบื้องต้น</li>
                    <li>การทำ Responsive Design</li>
                    <li>การใช้ Git และ GitHub</li>
                </ul>
            </section>
            
            <section>
                <h2>เนื้อหาการเรียน</h2>
                
                <article>
                    <header>
                        <h3>บทที่ 1: รู้จักกับ HTML</h3>
                        <p>ระยะเวลา: <time datetime="PT2H">2 ชั่วโมง</time></p>
                    </header>
                    
                    <p>เนื้อหา:</p>
                    <ol>
                        <li>HTML คืออะไร</li>
                        <li>โครงสร้างพื้นฐาน</li>
                        <li>Elements และ Attributes</li>
                    </ol>
                </article>
                
                <article>
                    <header>
                        <h3>บทที่ 2: CSS Styling</h3>
                        <p>ระยะเวลา: <time datetime="PT3H">3 ชั่วโมง</time></p>
                    </header>
                    
                    <p>เนื้อหา:</p>
                    <ol>
                        <li>CSS Selectors</li>
                        <li>Colors และ Typography</li>
                        <li>Box Model</li>
                    </ol>
                </article>
            </section>
        </article>
        
        <aside>
            <section>
                <h3>ความคืบหน้า</h3>
                <p>เรียนไปแล้ว: <mark>2/10 บท</mark></p>
                <p>ความคืบหน้า: <strong>20%</strong></p>
            </section>
            
            <section>
                <h3>หลักสูตรที่เกี่ยวข้อง</h3>
                <nav aria-label="หลักสูตรแนะนำ">
                    <ul>
                        <li><a href="/course/js">JavaScript Advanced</a></li>
                        <li><a href="/course/react">React.js</a></li>
                        <li><a href="/course/nodejs">Node.js</a></li>
                    </ul>
                </nav>
            </section>
            
            <section>
                <h3>ติดต่ออาจารย์</h3>
                <address>
                    <p><strong>อาจารย์สมชาย ใจดี</strong></p>
                    <p>อีเมล: <a href="mailto:somchai@codeacademy.com">somchai@codeacademy.com</a></p>
                </address>
            </section>
        </aside>
    </main>
    
    <footer>
        <section>
            <h3>เกี่ยวกับ CodeAcademy</h3>
            <p>แพลตฟอร์มเรียนออนไลน์สำหรับผู้ที่ต้องการเป็นโปรแกรมเมอร์</p>
        </section>
        
        <section>
            <h3>ติดต่อเรา</h3>
            <address>
                <p>อีเมล: <a href="mailto:support@codeacademy.com">support@codeacademy.com</a></p>
                <p>เวลาทำการ: <time>จันทร์-ศุกร์ 9:00-17:00 น.</time></p>
            </address>
        </section>
        
        <p><small>&copy; 2024 CodeAcademy. All rights reserved.</small></p>
    </footer>
</body>
</html>
```

### **คำอธิบาย:**
- `<article>` ทั้งหน้าเป็นเนื้อหาหลักสูตรที่สมบูรณ์
- ภายใน `<article>` มี `<section>` แบ่งหมวดหมู่ย่อย
- `<article>` ซ้อนใน `<article>` สำหรับแต่ละบทเรียน
- `datetime="PT2H"` หมายถึง Period Time 2 Hours
- `<address>` ใช้สำหรับข้อมูลติดต่ออาจารย์
- `<aside>` แสดงข้อมูลเสริมเกี่ยวกับความคืบหน้า

---

## 📊 **สรุปการใช้ Semantic Elements**

### **โครงสร้างพื้นฐานของหน้าเว็บ:**

```html
<header>
    <!-- ชื่อเว็บ, โลโก้, เมนูหลัก -->
    <nav><!-- เมนูนำทาง --></nav>
</header>

<main>
    <section>
        <!-- กลุ่มเนื้อหา -->
        <article><!-- เนื้อหาที่สมบูรณ์ --></article>
    </section>
    
    <aside>
        <!-- เนื้อหาเสริม -->
    </aside>
</main>

<footer>
    <!-- ข้อมูลท้ายหน้า -->
</footer>
```

### **กฎสำคัญ:**
1. ✅ มี `<main>` เพียง 1 ตัวต่อหน้า
2. ✅ `<article>` สามารถอยู่ใน `<section>` หรือในทางกลับกัน
3. ✅ `<header>` และ `<footer>` ใช้ได้กับ `<article>` และ `<section>`
4. ✅ `<nav>` ใช้สำหรับเมนูหลักเท่านั้น
5. ✅ `<address>` ใช้เฉพาะข้อมูลการติดต่อ
6. ✅ `<time>` ควรมี `datetime` attribute
7. ❌ ห้ามใส่ `<header>` หรือ `<footer>` ภายใน `<address>`
8. ❌ ห้ามซ้อน `<main>` ภายใน `<article>`, `<aside>`, `<header>`, `<footer>`, `<nav>`

### **ARIA Labels สำหรับ Navigation:**
```html
<nav aria-label="เมนูหลัก"><!-- เมนูหลัก --></nav>
<nav aria-label="หมวดหมู่"><!-- เมนูย่อย --></nav>
<nav aria-label="ลิงก์เสริม"><!-- เมนูท้ายหน้า --></nav>
```

### **Time Element Formats:**
```html
<!-- วันที่ -->
<time datetime="2024-09-15">15 กันยายน 2024</time>

<!-- วันที่และเวลา -->
<time datetime="2024-09-10T14:30">10 กันยายน 2024 เวลา 14:30 น.</time>

<!-- ระยะเวลา -->
<time datetime="PT2H">2 ชั่วโมง</time>
<time datetime="PT3H30M">3 ชั่วโมง 30 นาที</time>
```

---

## 🎯 **Best Practices**

### **การเลือกใช้ Semantic Elements:**

1. **ใช้ `<article>` เมื่อ:**
   - เนื้อหาสามารถแยกออกไปได้อย่างอิสระ
   - สามารถนำไปใช้ซ้ำได้
   - มีความหมายในตัวเอง
   - ตัวอย่าง: blog post, ข่าว, สินค้า, บทความ

2. **ใช้ `<section>` เมื่อ:**
   - เป็นกลุ่มเนื้อหาที่มีหัวข้อ
   - จัดกลุ่มเนื้อหาที่เกี่ยวข้องกัน
   - เป็นส่วนหนึ่งของเนื้อหาที่ใหญ่กว่า
   - ตัวอย่าง: chapters, tabs, หมวดหมู่

3. **ใช้ `<aside>` เมื่อ:**
   - เนื้อหาเสริม ไม่ใช่เนื้อหาหลัก
   - สามารถลบออกไปได้โดยไม่กระทบเนื้อหาหลัก
   - ตัวอย่าง: sidebar, บทความที่เกี่ยวข้อง, โฆษณา

4. **ใช้ `<nav>` เมื่อ:**
   - เป็นกลุ่มลิงก์นำทางหลัก
   - ไม่ใช้กับทุกกลุ่มลิงก์
   - เฉพาะเมนูสำคัญเท่านั้น

### **Accessibility Tips:**
- ✅ ใช้ `aria-label` แยกแยะ `<nav>` หลายตัว
- ✅ ใส่ `alt` attribute ในรูปภาพทุกรูป
- ✅ ใช้ heading hierarchy ที่ถูกต้อง (h1 → h2 → h3)
- ✅ ใส่ `datetime` attribute ใน `<time>`
- ✅ ใช้ semantic HTML แทน `<div>` ทุกครั้งที่ทำได้

---

## 🔍 **เครื่องมือตรวจสอบ**

### **HTML Validation:**
- W3C Validator: https://validator.w3.org/
- Nu Html Checker: https://validator.w3.org/nu/

### **Accessibility Testing:**
- WAVE: https://wave.webaim.org/
- axe DevTools (Browser Extension)
- Lighthouse (Chrome DevTools)

### **Screen Readers:**
- NVDA (Windows - ฟรี)
- JAWS (Windows)
- VoiceOver (macOS/iOS)
- TalkBack (Android)

### **Document Outline:**
- HTML5 Outliner (Browser Extension)
- HeadingsMap (Browser Extension)

---

**สำเร็จแล้ว!** 🎉 ตอนนี้คุณเข้าใจการใช้ Semantic HTML Layout แล้ว ลองนำไปใช้สร้างเว็บไซต์ที่มีโครงสร้างที่ดีและเป็นมิตรกับทุกคนกันเถอะ!