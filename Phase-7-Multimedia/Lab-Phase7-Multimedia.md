# Lab Phase 7: HTML Multimedia
## 🎯 เติม HTML Multimedia Tags ให้ถูกต้องตามโครงสร้าง

### 📚 **เนื้อหาที่ใช้ใน Lab นี้:**
- `<audio>` - เสียงและ attributes (controls, autoplay, loop)
- `<video>` - วิดีโอและ attributes (controls, width, height, poster)
- `<source>` - แหล่งที่มาของไฟล์ multimedia
- `<picture>` - รูปภาพแบบ responsive
- `<img>` - attributes ขั้นสูง (srcset, sizes, loading)
- Accessibility: captions, transcripts
- Performance: lazy loading, image optimization
- Responsive multimedia

---

## 🎵 **Lab 1: เว็บไซต์เพลงออนไลน์**

### **คำใบ้:**
1. **เสียง** พร้อม controls
2. **หลายแหล่งไฟล์** สำหรับ compatibility
3. **ข้อความสำรอง** สำหรับ browser ที่ไม่รองรับ
4. **รูปภาพปกอัลบั้ม** พร้อม alt text
5. **รายการเพลง** ใช้ list
6. **attributes** autoplay, loop, preload

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>MusicStream - เพลงออนไลน์</title>
</head>
<body>
    <หัวข้อหลัก>MusicStream - ฟังเพลงออนไลน์</หัวข้อหลัก>
    
    <ส่วนเนื้อหา>
        <หัวข้อรอง>กำลังเล่น: เพลง "ฤดูฝน"</หัวข้อรอง>
        
        <รูปภาพ src="album-cover.jpg" alt="ปกอัลบั้ม ฤดูฝน - ศิลปิน ABC" width="300" height="300">
        
        <เสียง controls>
            <แหล่งเสียง src="rainy-season.mp3" type="audio/mpeg">
            <แหล่งเสียง src="rainy-season.ogg" type="audio/ogg">
            <แหล่งเสียง src="rainy-season.wav" type="audio/wav">
            <ย่อหน้า>เบราว์เซอร์ของคุณไม่รองรับการเล่นเสียง <ลิงก์ href="rainy-season.mp3" download>ดาวน์โหลดเพลง</ลิงก์></ย่อหน้า>
        </เสียง>
        
        <ย่อหน้า>
            <ข้อความสำคัญ>ศิลปิน:</ข้อความสำคัญ> ABC Band<ขึ้นบรรทัดใหม่>
            <ข้อความสำคัญ>อัลบั้ม:</ข้อความสำคัญ> ฤดูของเรา<ขึ้นบรรทัดใหม่>
            <ข้อความสำคัญ>ระยะเวลา:</ข้อความสำคัญ> 3:45
        </ย่อหน้า>
    </ส่วนเนื้อหา>
    
    <เส้นแบ่ง>
    
    <ส่วนเนื้อหา>
        <หัวข้อรอง>เพลงยอดนิยม</หัวข้อรอง>
        
        <บทความ>
            <หัวข้อย่อย>1. เพลง "แสงแรก"</หัวข้อย่อย>
            <เสียง controls preload="metadata">
                <แหล่งเสียง src="first-light.mp3" type="audio/mpeg">
                <แหล่งเสียง src="first-light.ogg" type="audio/ogg">
                เบราว์เซอร์ไม่รองรับ
            </เสียง>
        </บทความ>
        
        <บทความ>
            <หัวข้อย่อย>2. เพลง "ดาวเหนือ"</หัวข้อย่อย>
            <เสียง controls preload="none">
                <แหล่งเสียง src="north-star.mp3" type="audio/mpeg">
                <แหล่งเสียง src="north-star.ogg" type="audio/ogg">
                เบราว์เซอร์ไม่รองรับ
            </เสียง>
        </บทความ>
        
        <บทความ>
            <หัวข้อย่อย>3. เพลง "ทะเลใจ"</หัวข้อย่อย>
            <เสียง controls loop>
                <แหล่งเสียง src="ocean-heart.mp3" type="audio/mpeg">
                <แหล่งเสียง src="ocean-heart.ogg" type="audio/ogg">
                เบราว์เซอร์ไม่รองรับ
            </เสียง>
        </บทความ>
    </ส่วนเนื้อหา>
    
    <เส้นแบ่ง>
    
    <ส่วนเนื้อหา>
        <หัวข้อรอง>Podcast ยอดนิยม</หัวข้อรอง>
        
        <บทความ>
            <หัวข้อย่อย>EP.15 - เทคโนโลยีในอนาคต</หัวข้อย่อย>
            <ย่อหน้า><ข้อความเล็ก>ระยะเวลา: 45 นาที | วันที่: 25 ตุลาคม 2567</ข้อความเล็ก></ย่อหน้า>
            <เสียง controls preload="metadata">
                <แหล่งเสียง src="podcast-ep15.mp3" type="audio/mpeg">
                <แหล่งเสียง src="podcast-ep15.ogg" type="audio/ogg">
            </เสียง>
            <ย่อหน้า>
                <รายละเอียด>
                    <สรุป>รายละเอียด Podcast</สรุป>
                    <ย่อหน้า>ในตอนนี้เราจะพูดถึงเทคโนโลยี AI, Machine Learning และอนาคตของการทำงานในยุคดิจิทัล</ย่อหน้า>
                </รายละเอียด>
            </ย่อหน้า>
        </บทความ>
    </ส่วนเนื้อหา>
</body>
</html>
```

---

## 🎬 **Lab 2: เว็บไซต์วิดีโอออนไลน์**

### **คำใบ้:**
1. **วิดีโอ** พร้อม controls
2. **poster** สำหรับภาพก่อนเล่น
3. **width และ height** กำหนดขนาด
4. **หลาย source** สำหรับ compatibility
5. **track** สำหรับ subtitle
6. **attributes** autoplay, muted, loop

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>VideoHub - วิดีโอออนไลน์</title>
</head>
<body>
    <หัวข้อหลัก>VideoHub - คลังวิดีโอออนไลน์</หัวข้อหลัก>
    
    <ส่วนเนื้อหา>
        <หัวข้อรอง>วิดีโอแนะนำ: "เรียนรู้ HTML ใน 30 นาที"</หัวข้อรอง>
        
        <วิดีโอ controls width="640" height="360" poster="html-tutorial-poster.jpg">
            <แหล่งวิดีโอ src="html-tutorial.mp4" type="video/mp4">
            <แหล่งวิดีโอ src="html-tutorial.webm" type="video/webm">
            <แหล่งวิดีโอ src="html-tutorial.ogv" type="video/ogg">
            <แทร็กคำบรรยาย src="html-tutorial-th.vtt" kind="subtitles" srclang="th" label="ภาษาไทย" default>
            <แทร็กคำบรรยาย src="html-tutorial-en.vtt" kind="subtitles" srclang="en" label="English">
            <ย่อหน้า>เบราว์เซอร์ของคุณไม่รองรับการเล่นวิดีโอ <ลิงก์ href="html-tutorial.mp4" download>ดาวน์โหลดวิดีโอ</ลิงก์></ย่อหน้า>
        </วิดีโอ>
        
        <ย่อหน้า>
            <ข้อความสำคัญ>ผู้สอน:</ข้อความสำคัญ> อ.สมชาย ใจดี<ขึ้นบรรทัดใหม่>
            <ข้อความสำคัญ>จำนวนผู้เข้าชม:</ข้อความสำคัญ> 125,430 ครั้ง<ขึ้นบรรทัดใหม่>
            <ข้อความสำคัญ>ระยะเวลา:</ข้อความสำคัญ> 28:35
        </ย่อหน้า>
        
        <ย่อหน้า>
            <รายละเอียด>
                <สรุป>รายละเอียดบทเรียน</สรุป>
                <รายการเรียงลำดับ>
                    <รายการ>00:00 - แนะนำ HTML</รายการ>
                    <รายการ>05:30 - โครงสร้างเอกสาร HTML</รายการ>
                    <รายการ>12:15 - Elements และ Tags</รายการ>
                    <รายการ>20:00 - Attributes</รายการ>
                    <รายการ>25:45 - สรุปและแบบฝึกหัด</รายการ>
                </รายการเรียงลำดับ>
            </รายละเอียด>
        </ย่อหน้า>
    </ส่วนเนื้อหา>
    
    <เส้นแบ่ง>
    
    <ส่วนเนื้อหา>
        <หัวข้อรอง>วิดีโอที่เกี่ยวข้อง</หัวข้อรอง>
        
        <บทความ>
            <หัวข้อย่อย>เรียนรู้ CSS พื้นฐาน</หัวข้อย่อย>
            <วิดีโอ controls width="320" height="180" poster="css-tutorial-poster.jpg" preload="metadata">
                <แหล่งวิดีโอ src="css-tutorial.mp4" type="video/mp4">
                <แหล่งวิดีโอ src="css-tutorial.webm" type="video/webm">
            </วิดีโอ>
            <ย่อหน้า><ข้อความเล็ก>ระยะเวลา: 35:20 | 89,320 ครั้ง</ข้อความเล็ก></ย่อหน้า>
        </บทความ>
        
        <บทความ>
            <หัวข้อย่อย>JavaScript สำหรับมือใหม่</หัวข้อย่อย>
            <วิดีโอ controls width="320" height="180" poster="js-tutorial-poster.jpg" preload="none">
                <แหล่งวิดีโอ src="js-tutorial.mp4" type="video/mp4">
                <แหล่งวิดีโอ src="js-tutorial.webm" type="video/webm">
            </วิดีโอ>
            <ย่อหน้า><ข้อความเล็ก>ระยะเวลา: 42:15 | 156,890 ครั้ง</ข้อความเล็ก></ย่อหน้า>
        </บทความ>
    </ส่วนเนื้อหา>
    
    <เส้นแบ่ง>
    
    <ส่วนเนื้อหา>
        <หัวข้อรอง>วิดีโอพื้นหลัง (Background Video)</หัวข้อรอง>
        <ย่อหน้า><ข้อความเล็ก>วิดีโอแบบ autoplay และ loop สำหรับพื้นหลัง</ข้อความเล็ก></ย่อหน้า>
        
        <วิดีโอ autoplay muted loop width="640" height="360" poster="background-poster.jpg">
            <แหล่งวิดีโอ src="background-video.mp4" type="video/mp4">
            <แหล่งวิดีโอ src="background-video.webm" type="video/webm">
        </วิดีโอ>
    </ส่วนเนื้อหา>
    
    <เส้นแบ่ง>
    
    <ส่วนเนื้อหา>
        <หัวข้อรอง>Live Stream</หัวข้อรอง>
        
        <iframe width="640" height="360" src="https://www.youtube.com/embed/dQw4w9WgXcQ" 
                title="Live Stream" 
                frameborder="0" 
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
                allowfullscreen>
        </iframe>
    </ส่วนเนื้อหา>
</body>
</html>
```

---

## 📸 **Lab 3: เว็บไซต์แกลเลอรีรูปภาพ Responsive**

### **คำใบ้:**
1. **picture** element สำหรับ responsive images
2. **source** พร้อม media queries
3. **srcset** สำหรับ resolution switching
4. **sizes** attribute
5. **loading="lazy"** สำหรับ performance
6. **figure และ figcaption**

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PhotoGallery - แกลเลอรีรูปภาพ</title>
</head>
<body>
    <หัวข้อหลัก>PhotoGallery - คลังรูปภาพสวยๆ</หัวข้อหลัก>
    
    <ส่วนเนื้อหา>
        <หัวข้อรอง>รูปภาพเด่นวันนี้</หัวข้อรอง>
        
        <กล่องรูปภาพพร้อมคำบรรยาย>
            <รูปภาพแบบ Responsive>
                <แหล่งรูปภาพตามหน้าจอ srcset="sunset-large.jpg" media="(min-width: 1200px)">
                <แหล่งรูปภาพตามหน้าจอ srcset="sunset-medium.jpg" media="(min-width: 768px)">
                <แหล่งรูปภาพตามหน้าจอ srcset="sunset-small.jpg" media="(min-width: 480px)">
                <รูปภาพ src="sunset-default.jpg" alt="พระอาทิตย์ตกดินที่ทะเลสวยงาม" loading="eager">
            </รูปภาพแบบ Responsive>
            <คำบรรยายรูปภาพ>
                <ข้อความสำคัญ>พระอาทิตย์ตกที่หาดกะตะ ภูเก็ต</ข้อความสำคัญ><ขึ้นบรรทัดใหม่>
                ถ่ายโดย: นายภาพสวย | 25 ตุลาคม 2567
            </คำบรรยายรูปภาพ>
        </กล่องรูปภาพพร้อมคำบรรยาย>
    </ส่วนเนื้อหา>
    
    <เส้นแบ่ง>
    
    <ส่วนเนื้อหา>
        <หัวข้อรอง>แกลเลอรีธรรมชาติ</หัวข้อรอง>
        
        <กล่องรูปภาพพร้อมคำบรรยาย>
            <รูปภาพแบบ Responsive>
                <แหล่งรูปภาพตามหน้าจอ srcset="mountain-1200.webp" type="image/webp" media="(min-width: 1200px)">
                <แหล่งรูปภาพตามหน้าจอ srcset="mountain-1200.jpg" type="image/jpeg" media="(min-width: 1200px)">
                
                <แหล่งรูปภาพตามหน้าจอ srcset="mountain-768.webp" type="image/webp" media="(min-width: 768px)">
                <แหล่งรูปภาพตามหน้าจอ srcset="mountain-768.jpg" type="image/jpeg" media="(min-width: 768px)">
                
                <รูปภาพ src="mountain-480.jpg" alt="ภูเขาสูงตระหง่านท่ามกลางหมอกยามเช้า" loading="lazy" width="800" height="600">
            </รูปภาพแบบ Responsive>
            <คำบรรยายรูปภาพ>ดอยอินทนนท์ ยามเช้า</คำบรรยายรูปภาพ>
        </กล่องรูปภาพพร้อมคำบรรยาย>
        
        <กล่องรูปภาพพร้อมคำบรรยาย>
            <รูปภาพ 
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
            <คำบรรยายรูปภาพ>น้ำตกเอราวัณ กาญจนบุรี</คำบรรยายรูปภาพ>
        </กล่องรูปภาพพร้อมคำบรรยาย>
        
        <กล่องรูปภาพพร้อมคำบรรยาย>
            <รูปภาพแบบ Responsive>
                <แหล่งรูปภาพตามหน้าจอ srcset="forest-large.webp" type="image/webp">
                <แหล่งรูปภาพตามหน้าจอ srcset="forest-large.jpg" type="image/jpeg">
                <รูปภาพ src="forest.jpg" alt="ป่าไม้เขียวชอุ่มเต็มไปด้วยต้นไม้ใหญ่" loading="lazy">
            </รูปภาพแบบ Responsive>
            <คำบรรยายรูปภาพ>ป่าดงพญาเย็น เชียงใหม่</คำบรรยายรูปภาพ>
        </กล่องรูปภาพพร้อมคำบรรยาย>
    </ส่วนเนื้อหา>
    
    <เส้นแบ่ง>
    
    <ส่วนเนื้อหา>
        <หัวข้อรอง>รูปภาพพอร์ตเทรต</หัวข้อรอง>
        
        <กล่องรูปภาพพร้อมคำบรรยาย>
            <รูปภาพแบบ Responsive>
                <แหล่งรูปภาพตามหน้าจอ 
                    srcset="portrait-vertical.jpg" 
                    media="(orientation: portrait)">
                <แหล่งรูปภาพตามหน้าจอ 
                    srcset="portrait-horizontal.jpg" 
                    media="(orientation: landscape)">
                <รูปภาพ src="portrait-default.jpg" alt="ภาพบุคคลยิ้มแย้มแจ่มใส" loading="lazy">
            </รูปภาพแบบ Responsive>
            <คำบรรยายรูปภาพ>Portrait Photography</คำบรรยายรูปภาพ>
        </กล่องรูปภาพพร้อมคำบรรยาย>
    </ส่วนเนื้อหา>
    
    <เส้นแบ่ง>
    
    <ส่วนเนื้อหา>
        <หัวข้อรอง>รูปภาพ High DPI (Retina Display)</หัวข้อรอง>
        
        <กล่องรูปภาพพร้อมคำบรรยาย>
            <รูปภาพ 
                src="product.jpg"
                srcset="product.jpg 1x,
                        product-2x.jpg 2x,
                        product-3x.jpg 3x"
                alt="สินค้าคุณภาพสูงบนพื้นหลังสีขาว"
                loading="lazy"
                width="400"
                height="400">
            <คำบรรยายรูปภาพ>รองเท้าผ้าใบ Premium Quality</คำบรรยายรูปภาพ>
        </กล่องรูปภาพพร้อมคำบรรยาย>
    </ส่วนเนื้อหา>
    
    <เส้นแบ่ง>
    
    <ส่วนเนื้อหา>
        <หัวข้อรอง>รูปภาพ Art Direction</หัวข้อรอง>
        <ย่อหน้า><ข้อความเล็ก>แสดงรูปภาพต่างกันตามขนาดหน้าจอ (Crop ต่างกัน)</ข้อความเล็ก></ย่อหน้า>
        
        <กล่องรูปภาพพร้อมคำบรรยาย>
            <รูปภาพแบบ Responsive>
                <!-- Desktop: แนวนอนเต็ม -->
                <แหล่งรูปภาพตามหน้าจอ 
                    srcset="team-wide.jpg" 
                    media="(min-width: 1024px)">
                
                <!-- Tablet: แนวนอนปานกลาง -->
                <แหล่งรูปภาพตามหน้าจอ 
                    srcset="team-medium.jpg" 
                    media="(min-width: 768px)">
                
                <!-- Mobile: แนวตั้ง crop ใกล้ -->
                <รูปภาพ 
                    src="team-portrait.jpg" 
                    alt="ทีมงานมืออาชีพยืนยิ้มร่วมกัน"
                    loading="lazy">
            </รูปภาพแบบ Responsive>
            <คำบรรยายรูปภาพ>ทีมงาน TechCorp 2024</คำบรรยายรูปภาพ>
        </กล่องรูปภาพพร้อมคำบรรยาย>
    </ส่วนเนื้อหา>
</body>
</html>
```

---

## 🎨 **Lab 4: เว็บไซต์พอร์ตโฟลิโอศิลปิน**

### **คำใบ้:**
1. **ผสมผสาน** audio, video, images
2. **accessibility** สำหรับ multimedia
3. **performance optimization**
4. **responsive design**
5. **modern formats** (WebP, WebM)

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Creative Portfolio - พอร์ตโฟลิโอศิลปิน</title>
</head>
<body>
    <ส่วนหัว>
        <หัวข้อหลัก>Creative Portfolio</หัวข้อหลัก>
        <ย่อหน้า>พอร์ตโฟลิโอของศิลปินดิจิทัล</ย่อหน้า>
    </ส่วนหัว>
    
    <ส่วนนำทาง>
        <รายการไม่เรียงลำดับ>
            <รายการ><ลิงก์ href="#video">วิดีโอผลงาน</ลิงก์></รายการ>
            <รายการ><ลิงก์ href="#gallery">แกลเลอรี</ลิงก์></รายการ>
            <รายการ><ลิงก์ href="#music">ดนตรีประกอบ</ลิงก์></รายการ>
        </รายการไม่เรียงลำดับ>
    </ส่วนนำทาง>
    
    <ส่วนเนื้อหาหลัก>
        <!-- Hero Video Section -->
        <ส่วนเนื้อหา id="hero">
            <หัวข้อรอง>วิดีโอแนะนำ</หัวข้อรอง>
            
            <วิดีโอ 
                controls 
                width="100%" 
                height="auto" 
                poster="hero-poster.jpg"
                preload="metadata">
                <แหล่งวิดีโอ src="portfolio-intro.webm" type="video/webm">
                <แหล่งวิดีโอ src="portfolio-intro.mp4" type="video/mp4">
                <แทร็กคำบรรยาย 
                    src="intro-captions.vtt" 
                    kind="captions" 
                    srclang="th" 
                    label="ภาษาไทย"
                    default>
                <ย่อหน้า>
                    วิดีโอแนะนำพอร์ตโฟลิโอของเรา 
                    <ลิงก์ href="portfolio-intro.mp4" download>ดาวน์โหลดวิดีโอ</ลิงก์>
                </ย่อหน้า>
            </วิดีโอ>
            
            <รายละเอียด>
                <สรุป>คำบรรยายวิดีโอ (Transcript)</สรุป>
                <ย่อหน้า>
                    สวัสดีครับ ผมชื่อสมชาย เป็นศิลปินดิจิทัล
                    ผมสร้างสรรค์ผลงานด้านกราฟิกดีไซน์ วิดีโอมอชั่นกราฟิก
                    และดนตรีประกอบ มาชมผลงานของผมกันเลยครับ
                </ย่อหน้า>
            </รายละเอียด>
        </ส่วนเนื้อหา>
        
        <เส้นแบ่ง>
        
        <!-- Gallery Section -->
        <ส่วนเนื้อหา id="gallery">
            <หัวข้อรอง>แกลเลอรีผลงาน</หัวข้อรอง>
            
            <บทความ>
                <หัวข้อย่อย>โปสเตอร์ดิจิทัล</หัวข้อย่อย>
                <กล่องรูปภาพพร้อมคำบรรยาย>
                    <รูปภาพแบบ Responsive>
                        <แหล่งรูปภาพตามหน้าจอ 
                            srcset="poster1-large.webp" 
                            type="image/webp" 
                            media="(min-width: 1024px)">
                        <แหล่งรูปภาพตามหน้าจอ 
                            srcset="poster1-large.jpg" 
                            type="image/jpeg" 
                            media="(min-width: 1024px)">
                        
                        <แหล่งรูปภาพตามหน้าจอ 
                            srcset="poster1-medium.webp" 
                            type="image/webp" 
                            media="(min-width: 768px)">
                        <แหล่งรูปภาพตามหน้าจอ 
                            srcset="poster1-medium.jpg" 
                            type="image/jpeg" 
                            media="(min-width: 768px)">
                        
                        <รูปภาพ 
                            src="poster1-small.jpg" 
                            alt="โปสเตอร์ดิจิทัลสีสันสดใสในธีมเทศกาลดนตรี"
                            loading="lazy"
                            width="600"
                            height="800">
                    </รูปภาพแบบ Responsive>
                    <คำบรรยายรูปภาพ>
                        <ข้อความสำคัญ>Music Festival Poster 2024</ข้อความสำคัญ><ขึ้นบรรทัดใหม่>
                        <ข้อความเล็ก>Adobe Illustrator, Photoshop</ข้อความเล็ก>
                    </คำบรรยายรูปภาพ>
                </กล่องรูปภาพพร้อมคำบรรยาย>
            </บทความ>
            
            <บทความ>
                <หัวข้อย่อย>Logo Design</หัวข้อย่อย>
                <กล่องรูปภาพพร้อมคำบรรยาย>
                    <รูปภาพ 
                        src="logo-design.png"
                        srcset="logo-design.png 1x,
                                logo-design-2x.png 2x,
                                logo-design-3x.png 3x"
                        alt="โลโก้สมัยใหม่รูปแบบมินิมอล"
                        loading="lazy"
                        width="400"
                        height="400">
                    <คำบรรยายรูปภาพ>
                        <ข้อความสำคัญ>TechStart Logo</ข้อความสำคัญ><ขึ้นบรรทัดใหม่>
                        <ข้อความเล็ก>Minimalist Design</ข้อความเล็ก>
                    </คำบรรยายรูปภาพ>
                </กล่องรูปภาพพร้อมคำบรรยาย>
            </บทความ>
        </ส่วนเนื้อหา>
        
        <เส้นแบ่ง>
        
        <!-- Video Works Section -->
        <ส่วนเนื้อหา id="video">
            <หัวข้อรอง>ผลงานวิดีโอ</หัวข้อรอง>
            
            <บทความ>
                <หัวข้อย่อย>Motion Graphics - Brand Animation</หัวข้อย่อย>
                <วิดีโอ 
                    controls 
                    width="640" 
                    height="360" 
                    poster="motion-graphics-poster.jpg"
                    preload="metadata">
                    <แหล่งวิดีโอ src="brand-animation.webm" type="video/webm">
                    <แหล่งวิดีโอ src="brand-animation.mp4" type="video/mp4">
                    <แทร็กคำบรรยาย 
                        src="brand-animation-captions.vtt" 
                        kind="captions" 
                        srclang="th" 
                        label="คำบรรยาย">
                    เบราว์เซอร์ไม่รองรับวิดีโอ
                </วิดีโอ>
                <ย่อหน้า><ข้อความเล็ก>ระยะเวลา: 0:45 | ซอฟต์แวร์: After Effects, Cinema 4D</ข้อความเล็ก></ย่อหน้า>
            </บทความ>
            
            <บทความ>
                <หัวข้อย่อย>Product Showcase Video</หัวข้อย่อย>
                <วิดีโอ 
                    controls 
                    width="640" 
                    height="360" 
                    poster="product-showcase-poster.jpg">
                    <แหล่งวิดีโอ src="product-showcase.webm" type="video/webm">
                    <แหล่งวิดีโอ src="product-showcase.mp4" type="video/mp4">
                </วิดีโอ>
                <ย่อหน้า><ข้อความเล็ก>ระยะเวลา: 1:20 | ซอฟต์แวร์: Blender, Premiere Pro</ข้อความเล็ก></ย่อหน้า>
            </บทความ>
        </ส่วนเนื้อหา>
        
        <เส้นแบ่ง>
        
        <!-- Music Section -->
        <ส่วนเนื้อหา id="music">
            <หัวข้อรอง>ดนตรีประกอบผลงาน</หัวข้อรอง>
            
            <บทความ>
                <หัวข้อย่อย>Ambient Background Music</หัวข้อย่อย>
                <เสียง controls preload="metadata">
                    <แหล่งเสียง src="ambient-music.mp3" type="audio/mpeg">
                    <แหล่งเสียง src="ambient-music.ogg" type="audio/ogg">
                    เบราว์เซอร์ไม่รองรับเสียง
                </เสียง>
                <ย่อหน้า><ข้อความเล็ก>ระยะเวลา: 3:25 | แนวเพลง: Ambient, Electronic</ข้อความเล็ก></ย่อหน้า>
            </บทความ>
            
            <บทความ>
                <หัวข้อย่อย>Upbeat Corporate Theme</หัวข้อย่อย>
                <เสียง controls>
                    <แหล่งเสียง src="corporate-theme.mp3" type="audio/mpeg">
                    <แหล่งเสียง src="corporate-theme.ogg" type="audio/ogg">
                </เสียง>
                <ย่อหน้า><ข้อความเล็ก>ระยะเวลา: 2:15 | แนวเพลง: Corporate, Pop</ข้อความเล็ก></ย่อหน้า>
            </บทความ>
        </ส่วนเนื้อหา>
        
        <เส้นแบ่ง>
        
        <!-- Client Testimonials Video -->
        <ส่วนเนื้อหา id="testimonials">
            <หัวข้อรอง>ความคิดเห็นจากลูกค้า</หัวข้อรอง>
            
            <บทความ>
                <วิดีโอ 
                    controls 
                    width="480" 
                    height="270" 
                    poster="testimonial-poster.jpg">
                    <แหล่งวิดีโอ src="client-testimonial.mp4" type="video/mp4">
                    <แหล่งวิดีโอ src="client-testimonial.webm" type="video/webm">
                    <แทร็กคำบรรยาย 
                        src="testimonial-th.vtt" 
                        kind="subtitles" 
                        srclang="th" 
                        label="ภาษาไทย"
                        default>
                    <แทร็กคำบรรยาย 
                        src="testimonial-en.vtt" 
                        kind="subtitles" 
                        srclang="en" 
                        label="English">
                </วิดีโอ>
                <ย่อหน้า>
                    <ข้อความสำคัญ>คุณสมหญิง - CEO, TechStart</ข้อความสำคัญ><ขึ้นบรรทัดใหม่>
                    <ข้อความเล็ก>"ผลงานที่ได้มีคุณภาพเกินความคาดหมาย"</ข้อความเล็ก>
                </ย่อหน้า>
            </บทความ>
        </ส่วนเนื้อหา>
    </ส่วนเนื้อหาหลัก>
    
    <ส่วนท้าย>
        <ย่อหน้า>&copy; 2024 Creative Portfolio. All rights reserved.</ย่อหน้า>
        <ย่อหน้า>
            <ลิงก์ href="mailto:contact@creative.com">ติดต่อเรา</ลิงก์> | 
            <ลิงก์ href="tel:0812345678">โทร 081-234-5678</ลิงก์>
        </ย่อหน้า>
    </ส่วนท้าย>
</body>
</html>
```

---

## 🎯 **เฉลยและคำแนะนำ**

### **การตรวจสอบผลงาน:**
1. ✅ ใช้ `<audio>` และ `<video>` พร้อม controls
2. ✅ มีหลาย `<source>` สำหรับ compatibility
3. ✅ ใส่ fallback content สำหรับ browser ที่ไม่รองรับ
4. ✅ ใช้ `<picture>` สำหรับ responsive images
5. ✅ ใส่ `alt` text ที่มีความหมาย
6. ✅ ใช้ `loading="lazy"` สำหรับรูปที่ไม่ใช่ above the fold
7. ✅ ใส่ `width` และ `height` เพื่อป้องกัน layout shift

### **เกณฑ์การให้คะแนน:**
- ✅ Audio/Video elements ถูกต้อง (25%)
- ✅ Responsive images (picture, srcset) (25%)
- ✅ Accessibility (alt, captions, transcripts) (20%)
- ✅ Performance (lazy loading, preload) (15%)
- ✅ Multiple sources และ fallback (15%)

### **ข้อผิดพลาดที่พบบ่อย:**
- ❌ ไม่ใส่ `controls` attribute
- ❌ มี source เดียว (ไม่รองรับหลาย browser)
- ❌ ไม่ใส่ fallback content
- ❌ ไม่ใส่ `alt` ในรูปภาพ
- ❌ ใส่ `loading="lazy"` ในรูป above the fold
- ❌ ไม่ใส่ `width` และ `height`
- ❌ ใช้ `autoplay` โดยไม่มี `muted`

---

## 📋 **Multimedia Elements สำคัญ**

### **Audio Element:**
```html
<audio controls preload="metadata">
    <source src="audio.mp3" type="audio/mpeg">
    <source src="audio.ogg" type="audio/ogg">
    <source src="audio.wav" type="audio/wav">
    เบราว์เซอร์ไม่รองรับ
</audio>
```

**Attributes:**
- `controls` - แสดงปุ่มควบคุม
- `autoplay` - เล่นอัตโนมัติ (ควรใช้กับ `muted`)
- `loop` - เล่นวนซ้ำ
- `muted` - ปิดเสียง
- `preload` - "none", "metadata", "auto"

### **Video Element:**
```html
<video controls width="640" height="360" poster="poster.jpg">
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
    <source src="video.ogv" type="video/ogg">
    <track src="captions.vtt" kind="subtitles" srclang="th" label="ไทย">
    เบราว์เซอร์ไม่รองรับ
</video>
```

**Attributes:**
- `controls`, `autoplay`, `loop`, `muted`, `preload` - เหมือน audio
- `poster` - รูปภาพก่อนเล่น
- `width`, `height` - ขนาด

### **Picture Element:**
```html
<picture>
    <source srcset="large.jpg" media="(min-width: 1200px)">
    <source srcset="medium.jpg" media="(min-width: 768px)">
    <img src="small.jpg" alt="อธิบายรูป">
</picture>
```

### **Responsive Images:**
```html
<!-- Resolution Switching -->
<img src="small.jpg"
     srcset="small.jpg 480w,
             medium.jpg 768w,
             large.jpg 1200w"
     sizes="(max-width: 480px) 100vw,
            (max-width: 768px) 90vw,
            800px"
     alt="อธิบาย">

<!-- Pixel Density -->
<img src="image.jpg"
     srcset="image.jpg 1x,
             image-2x.jpg 2x,
             image-3x.jpg 3x"
     alt="อธิบาย">
```

---

## 🏆 **Best Practices**

### **1. ใช้ Multiple Sources:**
```html
<!-- ✅ ถูกต้อง -->
<video controls>
    <source src="video.webm" type="video/webm">
    <source src="video.mp4" type="video/mp4">
    fallback content
</video>

<!-- ❌ ผิด - source เดียว -->
<video src="video.mp4" controls></video>
```

### **2. Accessibility:**
```html
<!-- Subtitles/Captions -->
<video controls>
    <source src="video.mp4" type="video/mp4">
    <track src="captions-th.vtt" kind="captions" srclang="th" label="ไทย" default>
    <track src="captions-en.vtt" kind="captions" srclang="en" label="English">
</video>

<!-- Transcript -->
<details>
    <summary>คำบรรยาย (Transcript)</summary>
    <p>เนื้อหาทั้งหมดของวิดีโอ...</p>
</details>
```

### **3. Performance:**
```html
<!-- Lazy Loading -->
<img src="image.jpg" alt="..." loading="lazy">

<!-- Preload -->
<video controls preload="metadata">
    <!-- preload: none, metadata, auto -->
</video>

<!-- Width & Height -->
<img src="image.jpg" alt="..." width="800" height="600">
```

### **4. Modern Formats:**
```html
<picture>
    <!-- WebP สำหรับ browser ที่รองรับ -->
    <source srcset="image.webp" type="image/webp">
    <!-- JPEG สำหรับ fallback -->
    <source srcset="image.jpg" type="image/jpeg">
    <img src="image.jpg" alt="...">
</picture>
```

### **5. Autoplay Best Practices:**
```html
<!-- ✅ ถูกต้อง - มี muted -->
<video autoplay muted loop>
    <source src="background.mp4" type="video/mp4">
</video>

<!-- ❌ ผิด - autoplay ไม่มี muted -->
<video autoplay controls>
    <source src="video.mp4" type="video/mp4">
</video>
```

---

## 💡 **ความรู้เพิ่มเติม**

### **File Formats:**

**Audio:**
- MP3 - รองรับกว้างที่สุด
- OGG - คุณภาพดี, open source
- WAV - ไม่บีบอัด, ไฟล์ใหญ่

**Video:**
- MP4 (H.264) - รองรับกว้างที่สุด
- WebM - คุณภาพดี, ไฟล์เล็ก
- OGV - open source

**Images:**
- JPEG - photos
- PNG - graphics, transparency
- WebP - modern, ไฟล์เล็ก
- AVIF - ล่าสุด, ไฟล์เล็กมาก

### **Preload Values:**
- `none` - ไม่โหลดล่วงหน้า
- `metadata` - โหลดแค่ metadata (duration, dimensions)
- `auto` - โหลดทั้งไฟล์

### **Track Element:**
```html
<track src="captions.vtt" 
       kind="subtitles|captions|descriptions|chapters|metadata"
       srclang="th"
       label="ภาษาไทย"
       default>
```

### **Responsive Breakpoints:**
- Mobile: < 768px
- Tablet: 768px - 1024px
- Desktop: > 1024px
- Large Desktop: > 1200px

---

**สำเร็จแล้ว!** 🎉 ตอนนี้คุณเข้าใจการใช้งาน multimedia elements ใน HTML แล้ว อย่าลืมคำนึงถึง accessibility และ performance เสมอนะครับ!
