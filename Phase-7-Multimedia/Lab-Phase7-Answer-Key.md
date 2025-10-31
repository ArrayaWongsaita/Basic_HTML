# เฉลย Lab Phase 7: HTML Multimedia

## 🎵 **เฉลย Lab 1: เว็บไซต์เพลงออนไลน์**

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>MusicStream - เพลงออนไลน์</title>
</head>
<body>
    <h1>MusicStream - ฟังเพลงออนไลน์</h1>
    
    <section>
        <h2>กำลังเล่น: เพลง "ฤดูฝน"</h2>
        
        <img src="album-cover.jpg" alt="ปกอัลบั้ม ฤดูฝน - ศิลปิน ABC" width="300" height="300">
        
        <audio controls>
            <source src="rainy-season.mp3" type="audio/mpeg">
            <source src="rainy-season.ogg" type="audio/ogg">
            <source src="rainy-season.wav" type="audio/wav">
            <p>เบราว์เซอร์ของคุณไม่รองรับการเล่นเสียง <a href="rainy-season.mp3" download>ดาวน์โหลดเพลง</a></p>
        </audio>
        
        <p>
            <strong>ศิลปิน:</strong> ABC Band<br>
            <strong>อัลบั้ม:</strong> ฤดูของเรา<br>
            <strong>ระยะเวลา:</strong> 3:45
        </p>
    </section>
    
    <hr>
    
    <section>
        <h2>เพลงยอดนิยม</h2>
        
        <article>
            <h3>1. เพลง "แสงแรก"</h3>
            <audio controls preload="metadata">
                <source src="first-light.mp3" type="audio/mpeg">
                <source src="first-light.ogg" type="audio/ogg">
                เบราว์เซอร์ไม่รองรับ
            </audio>
        </article>
        
        <article>
            <h3>2. เพลง "ดาวเหนือ"</h3>
            <audio controls preload="none">
                <source src="north-star.mp3" type="audio/mpeg">
                <source src="north-star.ogg" type="audio/ogg">
                เบราว์เซอร์ไม่รองรับ
            </audio>
        </article>
        
        <article>
            <h3>3. เพลง "ทะเลใจ"</h3>
            <audio controls loop>
                <source src="ocean-heart.mp3" type="audio/mpeg">
                <source src="ocean-heart.ogg" type="audio/ogg">
                เบราว์เซอร์ไม่รองรับ
            </audio>
        </article>
    </section>
    
    <hr>
    
    <section>
        <h2>Podcast ยอดนิยม</h2>
        
        <article>
            <h3>EP.15 - เทคโนโลยีในอนาคต</h3>
            <p><small>ระยะเวลา: 45 นาที | วันที่: 25 ตุลาคม 2567</small></p>
            <audio controls preload="metadata">
                <source src="podcast-ep15.mp3" type="audio/mpeg">
                <source src="podcast-ep15.ogg" type="audio/ogg">
            </audio>
            <p>
                <details>
                    <summary>รายละเอียด Podcast</summary>
                    <p>ในตอนนี้เราจะพูดถึงเทคโนโลยี AI, Machine Learning และอนาคตของการทำงานในยุคดิจิทัล</p>
                </details>
            </p>
        </article>
    </section>
</body>
</html>
```

---

## 🎬 **เฉลย Lab 2: เว็บไซต์วิดีโอออนไลน์**

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>VideoHub - วิดีโอออนไลน์</title>
</head>
<body>
    <h1>VideoHub - คลังวิดีโอออนไลน์</h1>
    
    <section>
        <h2>วิดีโอแนะนำ: "เรียนรู้ HTML ใน 30 นาที"</h2>
        
        <video controls width="640" height="360" poster="html-tutorial-poster.jpg">
            <source src="html-tutorial.mp4" type="video/mp4">
            <source src="html-tutorial.webm" type="video/webm">
            <source src="html-tutorial.ogv" type="video/ogg">
            <track src="html-tutorial-th.vtt" kind="subtitles" srclang="th" label="ภาษาไทย" default>
            <track src="html-tutorial-en.vtt" kind="subtitles" srclang="en" label="English">
            <p>เบราว์เซอร์ของคุณไม่รองรับการเล่นวิดีโอ <a href="html-tutorial.mp4" download>ดาวน์โหลดวิดีโอ</a></p>
        </video>
        
        <p>
            <strong>ผู้สอน:</strong> อ.สมชาย ใจดี<br>
            <strong>จำนวนผู้เข้าชม:</strong> 125,430 ครั้ง<br>
            <strong>ระยะเวลา:</strong> 28:35
        </p>
        
        <p>
            <details>
                <summary>รายละเอียดบทเรียน</summary>
                <ol>
                    <li>00:00 - แนะนำ HTML</li>
                    <li>05:30 - โครงสร้างเอกสาร HTML</li>
                    <li>12:15 - Elements และ Tags</li>
                    <li>20:00 - Attributes</li>
                    <li>25:45 - สรุปและแบบฝึกหัด</li>
                </ol>
            </details>
        </p>
    </section>
    
    <hr>
    
    <section>
        <h2>วิดีโอที่เกี่ยวข้อง</h2>
        
        <article>
            <h3>เรียนรู้ CSS พื้นฐาน</h3>
            <video controls width="320" height="180" poster="css-tutorial-poster.jpg" preload="metadata">
                <source src="css-tutorial.mp4" type="video/mp4">
                <source src="css-tutorial.webm" type="video/webm">
            </video>
            <p><small>ระยะเวลา: 35:20 | 89,320 ครั้ง</small></p>
        </article>
        
        <article>
            <h3>JavaScript สำหรับมือใหม่</h3>
            <video controls width="320" height="180" poster="js-tutorial-poster.jpg" preload="none">
                <source src="js-tutorial.mp4" type="video/mp4">
                <source src="js-tutorial.webm" type="video/webm">
            </video>
            <p><small>ระยะเวลา: 42:15 | 156,890 ครั้ง</small></p>
        </article>
    </section>
    
    <hr>
    
    <section>
        <h2>วิดีโอพื้นหลัง (Background Video)</h2>
        <p><small>วิดีโอแบบ autoplay และ loop สำหรับพื้นหลัง</small></p>
        
        <video autoplay muted loop width="640" height="360" poster="background-poster.jpg">
            <source src="background-video.mp4" type="video/mp4">
            <source src="background-video.webm" type="video/webm">
        </video>
    </section>
    
    <hr>
    
    <section>
        <h2>Live Stream</h2>
        
        <iframe width="640" height="360" src="https://www.youtube.com/embed/dQw4w9WgXcQ" 
                title="Live Stream" 
                frameborder="0" 
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
                allowfullscreen>
        </iframe>
    </section>
</body>
</html>
```

---

## 📸 **เฉลย Lab 3: เว็บไซต์แกลเลอรีรูปภาพ Responsive**

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PhotoGallery - แกลเลอรีรูปภาพ</title>
</head>
<body>
    <h1>PhotoGallery - คลังรูปภาพสวยๆ</h1>
    
    <section>
        <h2>รูปภาพเด่นวันนี้</h2>
        
        <figure>
            <picture>
                <source srcset="sunset-large.jpg" media="(min-width: 1200px)">
                <source srcset="sunset-medium.jpg" media="(min-width: 768px)">
                <source srcset="sunset-small.jpg" media="(min-width: 480px)">
                <img src="sunset-default.jpg" alt="พระอาทิตย์ตกดินที่ทะเลสวยงาม" loading="eager">
            </picture>
            <figcaption>
                <strong>พระอาทิตย์ตกที่หาดกะตะ ภูเก็ต</strong><br>
                ถ่ายโดย: นายภาพสวย | 25 ตุลาคม 2567
            </figcaption>
        </figure>
    </section>
    
    <hr>
    
    <section>
        <h2>แกลเลอรีธรรมชาติ</h2>
        
        <figure>
            <picture>
                <source srcset="mountain-1200.webp" type="image/webp" media="(min-width: 1200px)">
                <source srcset="mountain-1200.jpg" type="image/jpeg" media="(min-width: 1200px)">
                
                <source srcset="mountain-768.webp" type="image/webp" media="(min-width: 768px)">
                <source srcset="mountain-768.jpg" type="image/jpeg" media="(min-width: 768px)">
                
                <img src="mountain-480.jpg" alt="ภูเขาสูงตระหง่านท่ามกลางหมอกยามเช้า" loading="lazy" width="800" height="600">
            </picture>
            <figcaption>ดอยอินทนนท์ ยามเช้า</figcaption>
        </figure>
        
        <figure>
            <img 
                src="waterfall-480.jpg" 
                srcset="waterfall-480.jpg 480w,
                        waterfall-768.jpg 768w,
                        waterfall-1200.jpg 1200w,
                        waterfall-1920.jpg 1920w"
                sizes="(max-width: 480px) 100vw,
                       (max-width: 768px) 90vw,
                       (max-width: 1200px) 80vw,
                       1200px"
                alt="น้ำตกสวยงามไหลลงมาจากหน้าผา"
                loading="lazy"
                width="800"
                height="600">
            <figcaption>น้ำตกเอราวัณ กาญจนบุรี</figcaption>
        </figure>
        
        <figure>
            <picture>
                <source srcset="forest-large.webp" type="image/webp">
                <source srcset="forest-large.jpg" type="image/jpeg">
                <img src="forest.jpg" alt="ป่าไม้เขียวชอุ่มเต็มไปด้วยต้นไม้ใหญ่" loading="lazy">
            </picture>
            <figcaption>ป่าดงพญาเย็น เชียงใหม่</figcaption>
        </figure>
    </section>
    
    <hr>
    
    <section>
        <h2>รูปภาพพอร์ตเทรต</h2>
        
        <figure>
            <picture>
                <source srcset="portrait-vertical.jpg" media="(orientation: portrait)">
                <source srcset="portrait-horizontal.jpg" media="(orientation: landscape)">
                <img src="portrait-default.jpg" alt="ภาพบุคคลยิ้มแย้มแจ่มใส" loading="lazy">
            </picture>
            <figcaption>Portrait Photography</figcaption>
        </figure>
    </section>
    
    <hr>
    
    <section>
        <h2>รูปภาพ High DPI (Retina Display)</h2>
        
        <figure>
            <img 
                src="product.jpg"
                srcset="product.jpg 1x,
                        product-2x.jpg 2x,
                        product-3x.jpg 3x"
                alt="สินค้าคุณภาพสูงบนพื้นหลังสีขาว"
                loading="lazy"
                width="400"
                height="400">
            <figcaption>รองเท้าผ้าใบ Premium Quality</figcaption>
        </figure>
    </section>
    
    <hr>
    
    <section>
        <h2>รูปภาพ Art Direction</h2>
        <p><small>แสดงรูปภาพต่างกันตามขนาดหน้าจอ (Crop ต่างกัน)</small></p>
        
        <figure>
            <picture>
                <!-- Desktop: แนวนอนเต็ม -->
                <source srcset="team-wide.jpg" media="(min-width: 1024px)">
                
                <!-- Tablet: แนวนอนปานกลาง -->
                <source srcset="team-medium.jpg" media="(min-width: 768px)">
                
                <!-- Mobile: แนวตั้ง crop ใกล้ -->
                <img src="team-portrait.jpg" alt="ทีมงานมืออาชีพยืนยิ้มร่วมกัน" loading="lazy">
            </picture>
            <figcaption>ทีมงาน TechCorp 2024</figcaption>
        </figure>
    </section>
</body>
</html>
```

---

## 🎨 **เฉลย Lab 4: เว็บไซต์พอร์ตโฟลิโอศิลปิน**

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Creative Portfolio - พอร์ตโฟลิโอศิลปิน</title>
</head>
<body>
    <header>
        <h1>Creative Portfolio</h1>
        <p>พอร์ตโฟลิโอของศิลปินดิจิทัล</p>
    </header>
    
    <nav>
        <ul>
            <li><a href="#video">วิดีโอผลงาน</a></li>
            <li><a href="#gallery">แกลเลอรี</a></li>
            <li><a href="#music">ดนตรีประกอบ</a></li>
        </ul>
    </nav>
    
    <main>
        <!-- Hero Video Section -->
        <section id="hero">
            <h2>วิดีโอแนะนำ</h2>
            
            <video 
                controls 
                width="100%" 
                height="auto" 
                poster="hero-poster.jpg"
                preload="metadata">
                <source src="portfolio-intro.webm" type="video/webm">
                <source src="portfolio-intro.mp4" type="video/mp4">
                <track 
                    src="intro-captions.vtt" 
                    kind="captions" 
                    srclang="th" 
                    label="ภาษาไทย"
                    default>
                <p>
                    วิดีโอแนะนำพอร์ตโฟลิโอของเรา 
                    <a href="portfolio-intro.mp4" download>ดาวน์โหลดวิดีโอ</a>
                </p>
            </video>
            
            <details>
                <summary>คำบรรยายวิดีโอ (Transcript)</summary>
                <p>
                    สวัสดีครับ ผมชื่อสมชาย เป็นศิลปินดิจิทัล
                    ผมสร้างสรรค์ผลงานด้านกราฟิกดีไซน์ วิดีโอมอชั่นกราฟิก
                    และดนตรีประกอบ มาชมผลงานของผมกันเลยครับ
                </p>
            </details>
        </section>
        
        <hr>
        
        <!-- Gallery Section -->
        <section id="gallery">
            <h2>แกลเลอรีผลงาน</h2>
            
            <article>
                <h3>โปสเตอร์ดิจิทัล</h3>
                <figure>
                    <picture>
                        <source 
                            srcset="poster1-large.webp" 
                            type="image/webp" 
                            media="(min-width: 1024px)">
                        <source 
                            srcset="poster1-large.jpg" 
                            type="image/jpeg" 
                            media="(min-width: 1024px)">
                        
                        <source 
                            srcset="poster1-medium.webp" 
                            type="image/webp" 
                            media="(min-width: 768px)">
                        <source 
                            srcset="poster1-medium.jpg" 
                            type="image/jpeg" 
                            media="(min-width: 768px)">
                        
                        <img 
                            src="poster1-small.jpg" 
                            alt="โปสเตอร์ดิจิทัลสีสันสดใสในธีมเทศกาลดนตรี"
                            loading="lazy"
                            width="600"
                            height="800">
                    </picture>
                    <figcaption>
                        <strong>Music Festival Poster 2024</strong><br>
                        <small>Adobe Illustrator, Photoshop</small>
                    </figcaption>
                </figure>
            </article>
            
            <article>
                <h3>Logo Design</h3>
                <figure>
                    <img 
                        src="logo-design.png"
                        srcset="logo-design.png 1x,
                                logo-design-2x.png 2x,
                                logo-design-3x.png 3x"
                        alt="โลโก้สมัยใหม่รูปแบบมินิมอล"
                        loading="lazy"
                        width="400"
                        height="400">
                    <figcaption>
                        <strong>TechStart Logo</strong><br>
                        <small>Minimalist Design</small>
                    </figcaption>
                </figure>
            </article>
        </section>
        
        <hr>
        
        <!-- Video Works Section -->
        <section id="video">
            <h2>ผลงานวิดีโอ</h2>
            
            <article>
                <h3>Motion Graphics - Brand Animation</h3>
                <video 
                    controls 
                    width="640" 
                    height="360" 
                    poster="motion-graphics-poster.jpg"
                    preload="metadata">
                    <source src="brand-animation.webm" type="video/webm">
                    <source src="brand-animation.mp4" type="video/mp4">
                    <track 
                        src="brand-animation-captions.vtt" 
                        kind="captions" 
                        srclang="th" 
                        label="คำบรรยาย">
                    เบราว์เซอร์ไม่รองรับวิดีโอ
                </video>
                <p><small>ระยะเวลา: 0:45 | ซอฟต์แวร์: After Effects, Cinema 4D</small></p>
            </article>
            
            <article>
                <h3>Product Showcase Video</h3>
                <video 
                    controls 
                    width="640" 
                    height="360" 
                    poster="product-showcase-poster.jpg">
                    <source src="product-showcase.webm" type="video/webm">
                    <source src="product-showcase.mp4" type="video/mp4">
                </video>
                <p><small>ระยะเวลา: 1:20 | ซอฟต์แวร์: Blender, Premiere Pro</small></p>
            </article>
        </section>
        
        <hr>
        
        <!-- Music Section -->
        <section id="music">
            <h2>ดนตรีประกอบผลงาน</h2>
            
            <article>
                <h3>Ambient Background Music</h3>
                <audio controls preload="metadata">
                    <source src="ambient-music.mp3" type="audio/mpeg">
                    <source src="ambient-music.ogg" type="audio/ogg">
                    เบราว์เซอร์ไม่รองรับเสียง
                </audio>
                <p><small>ระยะเวลา: 3:25 | แนวเพลง: Ambient, Electronic</small></p>
            </article>
            
            <article>
                <h3>Upbeat Corporate Theme</h3>
                <audio controls>
                    <source src="corporate-theme.mp3" type="audio/mpeg">
                    <source src="corporate-theme.ogg" type="audio/ogg">
                </audio>
                <p><small>ระยะเวลา: 2:15 | แนวเพลง: Corporate, Pop</small></p>
            </article>
        </section>
        
        <hr>
        
        <!-- Client Testimonials Video -->
        <section id="testimonials">
            <h2>ความคิดเห็นจากลูกค้า</h2>
            
            <article>
                <video 
                    controls 
                    width="480" 
                    height="270" 
                    poster="testimonial-poster.jpg">
                    <source src="client-testimonial.mp4" type="video/mp4">
                    <source src="client-testimonial.webm" type="video/webm">
                    <track 
                        src="testimonial-th.vtt" 
                        kind="subtitles" 
                        srclang="th" 
                        label="ภาษาไทย"
                        default>
                    <track 
                        src="testimonial-en.vtt" 
                        kind="subtitles" 
                        srclang="en" 
                        label="English">
                </video>
                <p>
                    <strong>คุณสมหญิง - CEO, TechStart</strong><br>
                    <small>"ผลงานที่ได้มีคุณภาพเกินความคาดหมาย"</small>
                </p>
            </article>
        </section>
    </main>
    
    <footer>
        <p>&copy; 2024 Creative Portfolio. All rights reserved.</p>
        <p>
            <a href="mailto:contact@creative.com">ติดต่อเรา</a> | 
            <a href="tel:0812345678">โทร 081-234-5678</a>
        </p>
    </footer>
</body>
</html>
```

---

## 📊 **สรุปการใช้ Tags ในแต่ละ Lab**

### **Lab 1 - เว็บไซต์เพลงออนไลน์:**
- `<audio>` พร้อม controls
- หลาย `<source>` (MP3, OGG, WAV)
- `preload` attributes: metadata, none
- `loop` attribute สำหรับเพลงวนซ้ำ
- Fallback content สำหรับ browser ที่ไม่รองรับ
- `<details>` และ `<summary>` สำหรับข้อมูลเพิ่มเติม

### **Lab 2 - เว็บไซต์วิดีโอออนไลน์:**
- `<video>` พร้อม controls, width, height
- `poster` attribute สำหรับภาพก่อนเล่น
- หลาย `<source>` (MP4, WebM, OGV)
- `<track>` สำหรับ subtitles/captions
- `preload` values: metadata, none
- `autoplay muted loop` สำหรับ background video
- `<iframe>` สำหรับ embed YouTube

### **Lab 3 - แกลเลอรีรูปภาพ Responsive:**
- `<picture>` element
- `<source>` พร้อม media queries
- `srcset` และ `sizes` attributes
- Resolution switching (480w, 768w, 1200w)
- Pixel density (1x, 2x, 3x)
- Modern formats (WebP)
- `loading="lazy"` สำหรับ performance
- `loading="eager"` สำหรับ above the fold
- Art direction (ภาพต่างกันตามหน้าจอ)

### **Lab 4 - พอร์ตโฟลิโอศิลปิน:**
- ผสมผสาน audio, video, images
- `<track>` สำหรับ accessibility
- `<details>` สำหรับ transcript
- Responsive images ทุกรูป
- Modern formats (WebP, WebM)
- Semantic HTML5 (header, nav, main, section, article, footer)

---

## ✅ **หลักการตรวจให้คะแนน**

### **คะแนนเต็ม 100 แบ่งเป็น:**

**1. Audio Elements (20 คะแนน)**
- `<audio>` พร้อม controls (5)
- หลาย `<source>` elements (5)
- Fallback content (5)
- Attributes ถูกต้อง (preload, loop) (5)

**2. Video Elements (25 คะแนน)**
- `<video>` พร้อม controls, width, height (7)
- `poster` attribute (3)
- หลาย `<source>` elements (5)
- `<track>` สำหรับ captions (5)
- Attributes ถูกต้อง (5)

**3. Responsive Images (25 คะแนน)**
- `<picture>` element (7)
- `<source>` พร้อม media queries (7)
- `srcset` และ `sizes` (6)
- Modern formats (WebP) (5)

**4. Accessibility (15 คะแนน)**
- `alt` text ที่มีความหมาย (5)
- Captions/Subtitles (5)
- Transcripts (5)

**5. Performance (15 คะแนน)**
- `loading="lazy"` ใช้เหมาะสม (5)
- `preload` attributes (5)
- `width` และ `height` ป้องกัน layout shift (5)

### **ข้อผิดพลาดที่หักคะแนน:**

**Critical Errors (-10 คะแนนต่อข้อ)**
- ไม่มี `controls` ใน audio/video
- ไม่มี fallback content
- ไม่ใส่ `alt` ในรูปภาพ
- ใช้ `autoplay` โดยไม่มี `muted`

**Major Errors (-5 คะแนนต่อข้อ)**
- มี source เดียว
- ไม่ใส่ `poster` ใน video
- ไม่ใช้ responsive images
- ไม่ใส่ `width` และ `height`

**Minor Errors (-2 คะแนนต่อข้อ)**
- ไม่ใส่ `preload`
- ไม่ใช้ modern formats
- `loading="lazy"` ในรูป above the fold

---

## 🚀 **เทคนิคขั้นสูงสำหรับครู**

### **การขยายผล Lab:**

**1. เพิ่ม CSS Styling:**
```css
/* Audio Player */
audio {
    width: 100%;
    margin: 20px 0;
}

/* Video Responsive */
video {
    max-width: 100%;
    height: auto;
}

/* Picture Responsive */
picture img {
    width: 100%;
    height: auto;
    display: block;
}

/* Figure */
figure {
    margin: 0;
    padding: 0;
}

figcaption {
    text-align: center;
    font-style: italic;
    margin-top: 10px;
}
```

**2. เพิ่ม JavaScript Controls:**
```javascript
// Custom Audio Player
const audio = document.querySelector('audio');
const playBtn = document.getElementById('play');
const progressBar = document.getElementById('progress');

playBtn.addEventListener('click', () => {
    if (audio.paused) {
        audio.play();
        playBtn.textContent = 'Pause';
    } else {
        audio.pause();
        playBtn.textContent = 'Play';
    }
});

audio.addEventListener('timeupdate', () => {
    const percent = (audio.currentTime / audio.duration) * 100;
    progressBar.value = percent;
});
```

**3. Lazy Loading Script:**
```javascript
// Native Lazy Loading with fallback
if ('loading' in HTMLImageElement.prototype) {
    // Browser supports native lazy loading
    const images = document.querySelectorAll('img[loading="lazy"]');
    images.forEach(img => {
        img.src = img.dataset.src;
    });
} else {
    // Fallback to IntersectionObserver
    const script = document.createElement('script');
    script.src = 'https://cdnjs.cloudflare.com/ajax/libs/lozad.js/1.16.0/lozad.min.js';
    document.body.appendChild(script);
}
```

**4. WebVTT Captions Example:**
```
WEBVTT

00:00:00.000 --> 00:00:05.000
สวัสดีครับ ยินดีต้อนรับสู่วิดีโอของเรา

00:00:05.000 --> 00:00:10.000
วันนี้เราจะมาเรียนรู้เกี่ยวกับ HTML

00:00:10.000 --> 00:00:15.000
เริ่มต้นกันเลยครับ
```

### **กิจกรรมเสริม:**

**1. Performance Optimization Challenge:**
- วัดความเร็วโหลดหน้าเว็บ
- เปรียบเทียบก่อน-หลังใช้ lazy loading
- ทดสอบ different image formats

**2. Accessibility Testing:**
- ทดสอบด้วย screen reader
- ตรวจสอบ keyboard navigation
- ทดสอบ captions ทำงานหรือไม่

**3. Responsive Design Testing:**
- ทดสอบในหน้าจอขนาดต่างๆ
- ตรวจสอบ art direction
- วัด performance บน mobile

**4. Browser Compatibility:**
- ทดสอบใน browser ต่างๆ
- ตรวจสอบ fallback content
- ทดสอบ modern formats

---

## 🎓 **แนวทางการสอน**

### **ขั้นตอนการสอน:**

**1. แนะนำ Multimedia Elements (45 นาที)**
- อธิบาย audio และ video elements
- แสดงตัวอย่าง attributes ต่างๆ
- Demo responsive images
- อธิบาย accessibility

**2. ฝึกปฏิบัติ Basic (60 นาที)**
- Lab 1: Audio
- Lab 2: Video
- ตรวจสอบและให้คำแนะนำ

**3. ฝึกปฏิบัติ Advanced (60 นาที)**
- Lab 3: Responsive Images
- Lab 4: Portfolio
- ทดสอบในหน้าจอต่างๆ

**4. Performance & Accessibility (30 นาที)**
- อธิบาย lazy loading
- สอน captions/transcripts
- Best practices

### **จุดเน้นการสอน:**

**1. Accessibility:**
- Captions และ subtitles
- Transcripts
- Alt text ที่ดี
- Keyboard controls

**2. Performance:**
- Lazy loading
- Image optimization
- Preload strategies
- Modern formats

**3. Responsive Design:**
- Art direction
- Resolution switching
- Pixel density
- Media queries

**4. Browser Compatibility:**
- Multiple sources
- Fallback content
- Progressive enhancement

---

## 🔍 **แบบทดสอบความเข้าใจ**

### **คำถามทบทวน:**

1. **ทำไมต้องมีหลาย `<source>` elements?**
   - เพื่อรองรับหลาย browser
   - Browser จะเลือก format ที่รองรับ

2. **ความแตกต่างระหว่าง `srcset` และ `<picture>`?**
   - `srcset` - resolution switching
   - `<picture>` - art direction และ format switching

3. **เมื่อไหร่ควรใช้ `loading="lazy"`?**
   - รูปภาพที่ไม่ใช่ above the fold
   - รูปภาพที่อยู่ล่างหน้าจอแรก

4. **ทำไม `autoplay` ต้องมี `muted`?**
   - Browser block autoplay ที่มีเสียง
   - เพื่อ UX ที่ดี

5. **ความสำคัญของ `width` และ `height`?**
   - ป้องกัน layout shift
   - Improve CLS (Cumulative Layout Shift)

6. **WebVTT คืออะไร?**
   - Format สำหรับ captions/subtitles
   - รองรับ HTML5 video/audio

---

## 💡 **Tips สำหรับครู**

### **การประเมินผลงาน:**
- ตรวจสอบการทำงานจริง
- ทดสอบ responsive
- ตรวจสอบ accessibility
- วัด performance

### **Common Issues:**
- ไฟล์ multimedia ใหญ่เกินไป
- Browser compatibility
- Layout shift
- Autoplay ไม่ทำงาน

### **Solutions:**
- Compress multimedia files
- ใช้ multiple formats
- ใส่ width/height
- ใช้ autoplay + muted + loop

---

**การใช้ Lab นี้จะช่วยให้นักเรียนเข้าใจการใช้งาน multimedia ใน HTML อย่างมีประสิทธิภาพ พร้อมคำนึงถึง accessibility และ performance ครับ!** 🎉
