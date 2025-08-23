# ประสิทธิภาพภาพและข้อผิดพลาดที่พบบ่อยใน Multimedia

## 1. ประสิทธิภาพภาพ (Image Performance)

### 1.1 Responsive Images - การส่งรูปที่เหมาะสม

#### การเลือกขนาดรูปตามอุปกรณ์

```html
<!-- ✅ ถูกต้อง: ส่งรูปขนาดเหมาะสมตามอุปกรณ์ -->
<picture>
  <!-- Desktop: รูปความละเอียดสูง -->
  <source
    media="(min-width: 1200px)"
    srcset="hero-desktop-1920w.webp 1920w, hero-desktop-1600w.webp 1600w"
    sizes="100vw"
    type="image/webp"
  />

  <!-- Tablet: รูปขนาดกลาง -->
  <source
    media="(min-width: 768px)"
    srcset="hero-tablet-1024w.webp 1024w, hero-tablet-800w.webp 800w"
    sizes="100vw"
    type="image/webp"
  />

  <!-- Mobile: รูปขนาดเล็ก -->
  <source
    media="(max-width: 767px)"
    srcset="hero-mobile-600w.webp 600w, hero-mobile-400w.webp 400w"
    sizes="100vw"
    type="image/webp"
  />

  <!-- Fallback JPEG -->
  <img src="hero-default-800w.jpg" alt="ภาพหลักของหน้าเว็บ" loading="eager" />
</picture>

<!-- ❌ ผิด: ใช้รูปขนาดเดียวสำหรับทุกอุปกรณ์ -->
<img src="huge-image-3000x2000.jpg" alt="รูปภาพ" />
```

#### การใช้ `srcset` และ `sizes` อย่างมีประสิทธิภาพ

```html
<!-- Product Gallery - รูปสินค้าที่ปรับขนาดได้ -->
<div class="product-gallery">
  <img
    src="product-400w.jpg"
    srcset="
      product-400w.jpg   400w,
      product-600w.jpg   600w,
      product-800w.jpg   800w,
      product-1200w.jpg 1200w,
      product-1600w.jpg 1600w
    "
    sizes="(max-width: 480px) 100vw,
              (max-width: 768px) 80vw,
              (max-width: 1024px) 60vw,
              40vw"
    alt="สินค้า iPhone 15 Pro"
    loading="lazy"
  />
</div>

<!-- Blog Article Images -->
<article class="blog-post">
  <img
    src="article-image-600w.jpg"
    srcset="
      article-image-600w.jpg   600w,
      article-image-900w.jpg   900w,
      article-image-1200w.jpg 1200w
    "
    sizes="(max-width: 768px) 100vw,
              (max-width: 1200px) 75vw,
              800px"
    alt="ภาพประกอบบทความ"
    loading="lazy"
  />
</article>

<style>
  .product-gallery img {
    width: 100%;
    height: auto;
    max-width: 600px;
    border-radius: 8px;
  }

  .blog-post img {
    width: 100%;
    height: auto;
    max-width: 800px;
    margin: 1rem 0;
  }

  /* Responsive breakpoints */
  @media (max-width: 768px) {
    .product-gallery img {
      max-width: 100%;
    }
  }
</style>
```

### 1.2 Lazy Loading - โหลดรูปเมื่อจำเป็น

#### การใช้ `loading="lazy"` อย่างถูกต้อง

```html
<!-- Hero image: โหลดทันที -->
<img src="hero-image.jpg" alt="ภาพหลัก" loading="eager" />

<!-- Images ที่อยู่ด้านล่าง: ใช้ lazy loading -->
<section class="content">
  <img src="content-image-1.jpg" alt="รูปที่ 1" loading="lazy" />

  <img src="content-image-2.jpg" alt="รูปที่ 2" loading="lazy" />
</section>

<!-- Gallery: ทุกรูปใช้ lazy loading -->
<div class="image-gallery">
  <img src="gallery-1.jpg" alt="รูปที่ 1" loading="lazy" />
  <img src="gallery-2.jpg" alt="รูปที่ 2" loading="lazy" />
  <img src="gallery-3.jpg" alt="รูปที่ 3" loading="lazy" />
  <!-- ... รูปอื่นๆ -->
</div>
```

#### Custom Lazy Loading ด้วย Intersection Observer

```html
<div class="advanced-gallery">
  <div class="image-container" data-src="large-image-1.jpg">
    <img src="placeholder-blur.jpg" alt="ภาพกำลังโหลด" class="lazy-image" />
    <div class="loading-spinner">⏳ กำลังโหลด...</div>
  </div>

  <div class="image-container" data-src="large-image-2.jpg">
    <img src="placeholder-blur.jpg" alt="ภาพกำลังโหลด" class="lazy-image" />
    <div class="loading-spinner">⏳ กำลังโหลด...</div>
  </div>

  <div class="image-container" data-src="large-image-3.jpg">
    <img src="placeholder-blur.jpg" alt="ภาพกำลังโหลด" class="lazy-image" />
    <div class="loading-spinner">⏳ กำลังโหลด...</div>
  </div>
</div>

<script>
  // Advanced Lazy Loading
  class LazyImageLoader {
    constructor() {
      this.imageObserver = null;
      this.init();
    }

    init() {
      // ตรวจสอบว่า browser รองรับ Intersection Observer
      if ('IntersectionObserver' in window) {
        this.imageObserver = new IntersectionObserver(
          (entries, observer) => {
            entries.forEach((entry) => {
              if (entry.isIntersecting) {
                this.loadImage(entry.target);
                observer.unobserve(entry.target);
              }
            });
          },
          {
            // เริ่มโหลดเมื่อรูปเข้ามาใน viewport 100px
            rootMargin: '100px 0px',
            threshold: 0.01,
          }
        );

        this.observeImages();
      } else {
        // Fallback สำหรับ browser เก่า
        this.loadAllImages();
      }
    }

    observeImages() {
      const imageContainers = document.querySelectorAll(
        '.image-container[data-src]'
      );
      imageContainers.forEach((container) => {
        this.imageObserver.observe(container);
      });
    }

    loadImage(container) {
      const img = container.querySelector('img');
      const spinner = container.querySelector('.loading-spinner');
      const src = container.dataset.src;

      // แสดง loading spinner
      spinner.style.display = 'block';

      // สร้าง image object ใหม่เพื่อโหลด
      const imageLoader = new Image();

      imageLoader.onload = () => {
        // โหลดสำเร็จ
        img.src = src;
        img.classList.add('loaded');
        spinner.style.display = 'none';
        container.removeAttribute('data-src');
      };

      imageLoader.onerror = () => {
        // โหลดไม่สำเร็จ
        spinner.innerHTML = '❌ โหลดไม่สำเร็จ';
        spinner.style.color = 'red';
      };

      // เริ่มโหลดรูป
      imageLoader.src = src;
    }

    loadAllImages() {
      // Fallback: โหลดทุกรูปทันที
      const containers = document.querySelectorAll(
        '.image-container[data-src]'
      );
      containers.forEach((container) => {
        this.loadImage(container);
      });
    }
  }

  // เริ่มใช้งาน
  document.addEventListener('DOMContentLoaded', () => {
    new LazyImageLoader();
  });
</script>

<style>
  .advanced-gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 1rem;
    padding: 1rem;
  }

  .image-container {
    position: relative;
    background-color: #f0f0f0;
    border-radius: 8px;
    overflow: hidden;
    aspect-ratio: 16/9;
  }

  .lazy-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    filter: blur(5px);
    transition: filter 0.3s ease;
  }

  .lazy-image.loaded {
    filter: blur(0);
  }

  .loading-spinner {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: rgba(0, 0, 0, 0.7);
    color: white;
    padding: 0.5rem 1rem;
    border-radius: 4px;
    font-size: 0.9rem;
  }
</style>
```

### 1.3 การเลือกรูปแบบไฟล์ที่เหมาะสม

#### การใช้รูปแบบไฟล์สมัยใหม่

```html
<!-- ✅ ใช้รูปแบบไฟล์ที่มีประสิทธิภาพสูง -->
<picture>
  <!-- AVIF: รูปแบบใหม่ที่ขนาดเล็กที่สุด -->
  <source srcset="product.avif" type="image/avif" />

  <!-- WebP: รองรับในเบราว์เซอร์ส่วนใหญ่ -->
  <source srcset="product.webp" type="image/webp" />

  <!-- JPEG: Fallback -->
  <img src="product.jpg" alt="สินค้า" />
</picture>

<!-- สำหรับโลโก้และไอคอน -->
<picture>
  <!-- SVG: เหมาะสำหรับกราฟิก -->
  <source srcset="logo.svg" type="image/svg+xml" />

  <!-- PNG: Fallback สำหรับความโปร่งใส -->
  <img src="logo.png" alt="โลโก้บริษัท" />
</picture>
```

#### การทดสอบและเปรียบเทียบขนาดไฟล์

```html
<!-- ตัวอย่างการเปรียบเทียบขนาดไฟล์ -->
<div class="file-size-comparison">
  <h3>การเปรียบเทียบขนาดไฟล์</h3>
  <table border="1">
    <thead>
      <tr>
        <th>รูปแบบไฟล์</th>
        <th>ขนาด (KB)</th>
        <th>คุณภาพ</th>
        <th>การรองรับ</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>JPEG</td>
        <td>245 KB</td>
        <td>ดี</td>
        <td>100%</td>
      </tr>
      <tr>
        <td>WebP</td>
        <td>156 KB (-36%)</td>
        <td>ดีมาก</td>
        <td>94%</td>
      </tr>
      <tr>
        <td>AVIF</td>
        <td>98 KB (-60%)</td>
        <td>ยอดเยี่ยม</td>
        <td>72%</td>
      </tr>
    </tbody>
  </table>
</div>

<!-- ตัวอย่างภาพเปรียบเทียบ -->
<div class="image-comparison">
  <div class="comparison-item">
    <h4>JPEG (245 KB)</h4>
    <img src="sample-image.jpg" alt="ตัวอย่าง JPEG" />
  </div>

  <div class="comparison-item">
    <h4>WebP (156 KB)</h4>
    <picture>
      <source srcset="sample-image.webp" type="image/webp" />
      <img src="sample-image.jpg" alt="ตัวอย่าง WebP" />
    </picture>
  </div>

  <div class="comparison-item">
    <h4>AVIF (98 KB)</h4>
    <picture>
      <source srcset="sample-image.avif" type="image/avif" />
      <img src="sample-image.jpg" alt="ตัวอย่าง AVIF" />
    </picture>
  </div>
</div>
```

## 2. ข้อผิดพลาดที่พบบ่อยใน Multimedia

### 2.1 เล่นเสียงอัตโนมัติรบกวนผู้ใช้

#### ❌ ปัญหา: Autoplay ที่รบกวน

```html
<!-- ❌ อย่าทำ: เล่นเสียงอัตโนมัติโดยไม่มี muted -->
<video autoplay controls>
  <source src="promotional-video.mp4" type="video/mp4" />
</video>

<audio autoplay controls>
  <source src="background-music.mp3" type="audio/mpeg" />
</audio>

<!-- ❌ อย่าทำ: เสียงที่เล่นทันทีเมื่อโหลดหน้า -->
<audio autoplay loop>
  <source src="ambient-sound.mp3" type="audio/mpeg" />
</audio>
```

#### ✅ แก้ไข: การใช้ Autoplay อย่างถูกต้อง

```html
<!-- ✅ ถูกต้อง: ใช้ muted กับ autoplay -->
<video autoplay muted loop playsinline poster="video-poster.jpg">
  <source src="hero-background.mp4" type="video/mp4" />
  <source src="hero-background.webm" type="video/webm" />
</video>

<!-- ✅ ถูกต้อง: ให้ผู้ใช้เลือกเปิดเสียง -->
<div class="video-with-audio-control">
  <video id="hero-video" autoplay muted loop playsinline>
    <source src="promotional-video.mp4" type="video/mp4" />
  </video>

  <div class="audio-control">
    <button id="unmute-btn" onclick="enableAudio()">
      🔊 คลิกเพื่อเปิดเสียง
    </button>
  </div>
</div>

<script>
  function enableAudio() {
    const video = document.getElementById('hero-video');
    const button = document.getElementById('unmute-btn');

    video.muted = false;
    button.style.display = 'none';

    // แสดงการแจ้งเตือน
    showNotification('เปิดเสียงแล้ว');
  }

  function showNotification(message) {
    const notification = document.createElement('div');
    notification.className = 'notification';
    notification.textContent = message;
    document.body.appendChild(notification);

    setTimeout(() => {
      notification.remove();
    }, 3000);
  }
</script>

<style>
  .video-with-audio-control {
    position: relative;
  }

  .audio-control {
    position: absolute;
    bottom: 20px;
    right: 20px;
  }

  #unmute-btn {
    background-color: rgba(0, 0, 0, 0.7);
    color: white;
    border: none;
    padding: 0.75rem 1rem;
    border-radius: 25px;
    cursor: pointer;
    font-size: 0.9rem;
    transition: background-color 0.3s;
  }

  #unmute-btn:hover {
    background-color: rgba(0, 0, 0, 0.9);
  }

  .notification {
    position: fixed;
    top: 20px;
    right: 20px;
    background-color: #4caf50;
    color: white;
    padding: 1rem;
    border-radius: 4px;
    z-index: 1000;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
  }
</style>
```

#### การสร้าง Audio Player ที่เป็นมิตรกับผู้ใช้

```html
<div class="user-friendly-audio-player">
  <h3>🎵 เพลงประกอบ</h3>
  <p>คลิกเพื่อเล่นเพลงประกอบขณะอ่าน</p>

  <audio id="background-audio" loop>
    <source src="reading-background-music.mp3" type="audio/mpeg" />
    <source src="reading-background-music.ogg" type="audio/ogg" />
  </audio>

  <div class="audio-controls">
    <button onclick="toggleAudio()" id="audio-toggle">▶️ เริ่มเล่น</button>
    <input
      type="range"
      id="volume-slider"
      min="0"
      max="100"
      value="30"
      onchange="changeVolume(this.value)"
    />
    <span id="volume-display">30%</span>
  </div>

  <div class="audio-settings">
    <label>
      <input type="checkbox" id="auto-stop" checked />
      หยุดเล่นเมื่อเปลี่ยนหน้า
    </label>
  </div>
</div>

<script>
  const audio = document.getElementById('background-audio');
  const toggleBtn = document.getElementById('audio-toggle');
  const volumeSlider = document.getElementById('volume-slider');
  const volumeDisplay = document.getElementById('volume-display');
  let isPlaying = false;

  // ตั้งค่าเสียงเริ่มต้นต่ำ
  audio.volume = 0.3;

  function toggleAudio() {
    if (isPlaying) {
      audio.pause();
      toggleBtn.textContent = '▶️ เริ่มเล่น';
      isPlaying = false;
    } else {
      audio
        .play()
        .then(() => {
          toggleBtn.textContent = '⏸️ หยุด';
          isPlaying = true;
        })
        .catch((error) => {
          console.error('ไม่สามารถเล่นเสียงได้:', error);
          alert(
            'เบราว์เซอร์ไม่อนุญาตให้เล่นเสียงอัตโนมัติ กรุณาคลิกที่ปุ่มเล่นอีกครั้ง'
          );
        });
    }
  }

  function changeVolume(value) {
    audio.volume = value / 100;
    volumeDisplay.textContent = value + '%';
  }

  // หยุดเล่นเมื่อผู้ใช้ออกจากหน้า
  window.addEventListener('beforeunload', () => {
    if (document.getElementById('auto-stop').checked && isPlaying) {
      audio.pause();
    }
  });

  // บันทึกการตั้งค่าใน localStorage
  volumeSlider.addEventListener('change', () => {
    localStorage.setItem('audioVolume', volumeSlider.value);
  });

  // โหลดการตั้งค่าที่บันทึกไว้
  window.addEventListener('load', () => {
    const savedVolume = localStorage.getItem('audioVolume');
    if (savedVolume) {
      volumeSlider.value = savedVolume;
      changeVolume(savedVolume);
    }
  });
</script>

<style>
  .user-friendly-audio-player {
    background-color: #f8f9fa;
    border: 1px solid #dee2e6;
    border-radius: 8px;
    padding: 1.5rem;
    margin: 1rem 0;
    max-width: 400px;
  }

  .audio-controls {
    display: flex;
    align-items: center;
    gap: 1rem;
    margin: 1rem 0;
  }

  .audio-controls button {
    padding: 0.5rem 1rem;
    border: 1px solid #007bff;
    border-radius: 4px;
    background-color: #007bff;
    color: white;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  .audio-controls button:hover {
    background-color: #0056b3;
  }

  #volume-slider {
    flex: 1;
  }

  .audio-settings {
    font-size: 0.9rem;
    color: #666;
  }

  .audio-settings label {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    cursor: pointer;
  }
</style>
```

### 2.2 ขาดคำบรรยายสื่อ (Missing Media Descriptions)

#### ❌ ปัญหา: ไม่มีคำบรรยายสื่อ

```html
<!-- ❌ อย่าทำ: ไม่มีคำบรรยายหรือ alt text -->
<video controls>
  <source src="tutorial-video.mp4" type="video/mp4" />
</video>

<audio controls>
  <source src="podcast.mp3" type="audio/mpeg" />
</audio>

<img src="chart-data.png" />
```

#### ✅ แก้ไข: การใส่คำบรรยายสื่ออย่างครบถ้วน

```html
<!-- ✅ ถูกต้อง: Video พร้อมคำบรรยายและ accessibility -->
<section class="video-section">
  <h2>บทเรียน: การใช้งาน HTML5 Forms</h2>

  <video
    controls
    poster="html-forms-poster.jpg"
    aria-label="วิดีโอสอนการใช้งาน HTML5 Forms"
  >
    <source src="html-forms-tutorial.mp4" type="video/mp4" />
    <source src="html-forms-tutorial.webm" type="video/webm" />

    <!-- Subtitles หลายภาษา -->
    <track
      kind="subtitles"
      src="subtitles-th.vtt"
      srclang="th"
      label="ไทย"
      default
    />
    <track
      kind="subtitles"
      src="subtitles-en.vtt"
      srclang="en"
      label="English"
    />

    <!-- Captions สำหรับผู้พิการทางการได้ยิน -->
    <track
      kind="captions"
      src="captions-th.vtt"
      srclang="th"
      label="คำบรรยายเสียง"
    />

    <!-- Descriptions สำหรับผู้พิการทางสายตา -->
    <track
      kind="descriptions"
      src="descriptions-th.vtt"
      srclang="th"
      label="คำอธิบายภาพ"
    />

    <!-- Chapters -->
    <track kind="chapters" src="chapters.vtt" srclang="th" label="บทเรียน" />
  </video>

  <!-- ข้อมูลเพิ่มเติมของวิดีโอ -->
  <div class="video-info">
    <p>
      <strong>เนื้อหา:</strong> เรียนรู้การสร้างฟอร์มด้วย HTML5
      ตั้งแต่พื้นฐานจนถึงขั้นสูง
    </p>
    <p><strong>ระยะเวลา:</strong> 25 นาที</p>
    <p><strong>ผู้สอน:</strong> อาจารย์สมชาย</p>
    <p>
      <strong>หัวข้อที่ครอบคลุม:</strong> Form elements, Validation,
      Accessibility
    </p>
  </div>
</section>

<!-- ✅ ถูกต้อง: Audio พร้อมคำอธิบาย -->
<section class="audio-section">
  <h3>🎙️ Podcast: Future of Web Development</h3>

  <audio controls aria-label="Podcast เรื่อง Future of Web Development">
    <source src="web-dev-future-podcast.mp3" type="audio/mpeg" />
    <source src="web-dev-future-podcast.ogg" type="audio/ogg" />
  </audio>

  <div class="podcast-info">
    <p>
      <strong>รายละเอียด:</strong> บทสนทนากับผู้เชี่ยวชาญด้าน Web Development
      เกี่ยวกับแนวโน้มและเทคโนโลยีใหม่ๆ
    </p>
    <p><strong>ระยะเวลา:</strong> 45 นาที</p>
    <p><strong>ผู้ดำเนินรายการ:</strong> คุณสมหญิง</p>
    <p><strong>แขก:</strong> Senior Developer จาก Google และ Facebook</p>

    <details>
      <summary>📝 Transcript ของ Podcast</summary>
      <div class="transcript">
        <h4>เนื้อหาการสนทนา:</h4>
        <p><strong>[00:00 - 05:00] บทนำ</strong></p>
        <p>
          สวัสดีครับ ยินดีต้อนรับเข้าสู่ podcast Future of Web Development
          ฉันชื่อสมหญิง และวันนี้เรามีแขกพิเศษ...
        </p>

        <p><strong>[05:00 - 15:00] แนวโน้ม JavaScript Frameworks</strong></p>
        <p>
          เราจะมาคุยกันเกี่ยวกับ React, Vue, Angular และ framework ใหม่ๆ
          ที่น่าสนใจ...
        </p>

        <p><strong>[15:00 - 25:00] AI และ Web Development</strong></p>
        <p>
          การใช้ AI ในการช่วยเขียน code และ testing
          จะเปลี่ยนแปลงอุตสาหกรรมอย่างไร...
        </p>

        <p><strong>[25:00 - 35:00] WebAssembly และ Performance</strong></p>
        <p>
          เทคโนโลยีที่จะทำให้ web applications เร็วเท่า native applications...
        </p>

        <p><strong>[35:00 - 45:00] Q&A และสรุป</strong></p>
        <p>ตอบคำถามจากผู้ฟังและสรุปประเด็นสำคัญ...</p>
      </div>
    </details>
  </div>
</section>

<!-- ✅ ถูกต้อง: รูปภาพพร้อม alt text ที่มีความหมาย -->
<figure>
  <img
    src="web-performance-chart.png"
    alt="กราฟแสดงการปรับปรุงประสิทธิภาพเว็บไซต์ จากการใช้ lazy loading ทำให้ loading time ลดลง 40%"
  />
  <figcaption>
    กราฟแสดงผลการทดสอบประสิทธิภาพก่อนและหลังใช้ lazy loading
  </figcaption>
</figure>
```

#### ตัวอย่างไฟล์ WebVTT สำหรับคำบรรยาย

##### descriptions-th.vtt (สำหรับผู้พิการทางสายตา):

```
WEBVTT

NOTE
คำอธิบายภาพสำหรับผู้พิการทางสายตา

00:00:00.000 --> 00:00:05.000
ผู้สอนชายวัยกลางคนนั่งหน้าคอมพิวเตอร์ในห้องสำนักงาน มีหน้าจอแสดงโค้ด HTML

00:00:05.000 --> 00:00:10.000
เมาส์ชี้ไปที่แท็ก form ในโปรแกรม text editor สีพื้นหลังเป็นสีเข้ม

00:00:10.000 --> 00:00:15.000
เปิดเบราว์เซอร์ขึ้นมา แสดงหน้าเว็บที่มีฟอร์มสมัครสมาชิก ประกอบด้วยช่องกรอกชื่อ อีเมล และรหัสผ่าน

00:00:15.000 --> 00:00:20.000
ผู้สอนพิมพ์ข้อมูลในฟอร์ม โดยเริ่มจากช่องชื่อ แล้วกดปุ่ม Tab เพื่อไปช่องถัดไป
```

##### captions-th.vtt (รวมเสียงสิ่งแวดล้อม):

```
WEBVTT

00:00:00.000 --> 00:00:05.000
สวัสดีครับ วันนี้เราจะมาเรียนรู้เรื่อง HTML Forms กัน

00:00:05.000 --> 00:00:07.000
[เสียงคลิกเมาส์]

00:00:07.000 --> 00:00:10.000
เริ่มต้นด้วยการสร้างแท็ก form

00:00:10.000 --> 00:00:12.000
[เสียงพิมพ์คีย์บอร์ด]

00:00:12.000 --> 00:00:15.000
แล้วก็ใส่ input elements ต่างๆ ลงไป

00:00:15.000 --> 00:00:18.000
[เสียงเปิดเบราว์เซอร์]

00:00:18.000 --> 00:00:20.000
มาดูผลลัพธ์ในเบราว์เซอร์กัน
```

### 2.3 การแก้ไขปัญหาที่พบบ่อย

#### เครื่องมือตรวจสอบ Accessibility

```html
<div class="accessibility-checker">
  <h3>🔍 เครื่องมือตรวจสอบ Accessibility</h3>

  <button onclick="checkMultimediaAccessibility()">
    ตรวจสอบ Multimedia Accessibility
  </button>

  <div id="accessibility-results"></div>
</div>

<script>
  function checkMultimediaAccessibility() {
    const results = [];

    // ตรวจสอบ video elements
    const videos = document.querySelectorAll('video');
    videos.forEach((video, index) => {
      const issues = [];

      if (!video.hasAttribute('aria-label') && !video.textContent.trim()) {
        issues.push('ไม่มี aria-label หรือคำอธิบาย');
      }

      const tracks = video.querySelectorAll('track');
      const hasSubtitles = Array.from(tracks).some(
        (track) => track.kind === 'subtitles'
      );
      const hasCaptions = Array.from(tracks).some(
        (track) => track.kind === 'captions'
      );

      if (!hasSubtitles) issues.push('ไม่มี subtitles');
      if (!hasCaptions)
        issues.push('ไม่มี captions สำหรับผู้พิการทางการได้ยิน');

      if (video.hasAttribute('autoplay') && !video.hasAttribute('muted')) {
        issues.push('ใช้ autoplay โดยไม่มี muted (รบกวนผู้ใช้)');
      }

      results.push({
        type: 'Video',
        index: index + 1,
        issues: issues.length > 0 ? issues : ['✅ ไม่มีปัญหา'],
      });
    });

    // ตรวจสอบ audio elements
    const audios = document.querySelectorAll('audio');
    audios.forEach((audio, index) => {
      const issues = [];

      if (!audio.hasAttribute('aria-label') && !audio.textContent.trim()) {
        issues.push('ไม่มี aria-label หรือคำอธิบาย');
      }

      if (audio.hasAttribute('autoplay')) {
        issues.push('ใช้ autoplay (อาจรบกวนผู้ใช้)');
      }

      results.push({
        type: 'Audio',
        index: index + 1,
        issues: issues.length > 0 ? issues : ['✅ ไม่มีปัญหา'],
      });
    });

    // ตรวจสอบ images
    const images = document.querySelectorAll('img');
    let imagesWithoutAlt = 0;
    images.forEach((img) => {
      if (!img.hasAttribute('alt') || img.alt.trim() === '') {
        imagesWithoutAlt++;
      }
    });

    if (imagesWithoutAlt > 0) {
      results.push({
        type: 'Images',
        index: '',
        issues: [`${imagesWithoutAlt} รูปภาพไม่มี alt text`],
      });
    }

    // แสดงผลลัพธ์
    displayResults(results);
  }

  function displayResults(results) {
    const resultsDiv = document.getElementById('accessibility-results');

    if (results.length === 0) {
      resultsDiv.innerHTML =
        '<div class="success">🎉 ไม่พบปัญหา Accessibility</div>';
      return;
    }

    let html = '<h4>📋 ผลการตรวจสอบ:</h4><ul>';

    results.forEach((result) => {
      html += `<li><strong>${result.type} ${result.index}</strong><ul>`;
      result.issues.forEach((issue) => {
        const className = issue.startsWith('✅') ? 'success' : 'warning';
        html += `<li class="${className}">${issue}</li>`;
      });
      html += '</ul></li>';
    });

    html += '</ul>';
    resultsDiv.innerHTML = html;
  }
</script>

<style>
  .accessibility-checker {
    background-color: #f8f9fa;
    border: 1px solid #dee2e6;
    border-radius: 8px;
    padding: 1.5rem;
    margin: 2rem 0;
  }

  .accessibility-checker button {
    background-color: #007bff;
    color: white;
    border: none;
    padding: 0.75rem 1.5rem;
    border-radius: 4px;
    cursor: pointer;
    font-size: 1rem;
  }

  .accessibility-checker button:hover {
    background-color: #0056b3;
  }

  #accessibility-results {
    margin-top: 1rem;
  }

  .success {
    color: #28a745;
  }

  .warning {
    color: #dc3545;
  }

  #accessibility-results ul {
    list-style-type: none;
    padding-left: 1rem;
  }

  #accessibility-results li {
    margin: 0.5rem 0;
  }
</style>
```

## 3. Best Practices สำหรับ Performance และ Accessibility

### 3.1 Checklist การตรวจสอบ

```html
<div class="best-practices-checklist">
  <h3>📋 Best Practices Checklist</h3>

  <div class="checklist-section">
    <h4>🖼️ Images</h4>
    <label
      ><input type="checkbox" /> ใช้รูปแบบไฟล์ที่เหมาะสม (WebP, AVIF)</label
    >
    <label
      ><input type="checkbox" /> ใช้ responsive images (srcset, sizes)</label
    >
    <label
      ><input type="checkbox" /> ใช้ lazy loading สำหรับรูปที่อยู่ล่างๆ</label
    >
    <label><input type="checkbox" /> มี alt text ที่มีความหมาย</label>
    <label
      ><input type="checkbox" /> กำหนดขนาด width/height เพื่อป้องกัน layout
      shift</label
    >
  </div>

  <div class="checklist-section">
    <h4>🎬 Video</h4>
    <label><input type="checkbox" /> ใช้ muted กับ autoplay</label>
    <label><input type="checkbox" /> มี poster image</label>
    <label><input type="checkbox" /> มี subtitles อย่างน้อย 1 ภาษา</label>
    <label
      ><input type="checkbox" /> มี captions สำหรับผู้พิการทางการได้ยิน</label
    >
    <label
      ><input type="checkbox" /> มี descriptions สำหรับผู้พิการทางสายตา</label
    >
    <label><input type="checkbox" /> มี transcript ในหน้าเว็บ</label>
  </div>

  <div class="checklist-section">
    <h4>🎵 Audio</h4>
    <label
      ><input type="checkbox" /> ไม่ใช้ autoplay (หรือให้ผู้ใช้เลือก)</label
    >
    <label><input type="checkbox" /> มีคำอธิบายเนื้อหา</label>
    <label><input type="checkbox" /> มี transcript ถ้าเป็นพูด</label>
    <label><input type="checkbox" /> มีการควบคุมระดับเสียง</label>
  </div>

  <div class="checklist-section">
    <h4>🚀 Performance</h4>
    <label><input type="checkbox" /> ใช้ preload="metadata" สำหรับ video</label>
    <label><input type="checkbox" /> บีบอัดไฟล์ให้เหมาะสม</label>
    <label><input type="checkbox" /> มี fallback สำหรับเบราว์เซอร์เก่า</label>
    <label><input type="checkbox" /> ทดสอบบนอุปกรณ์ต่างๆ</label>
  </div>
</div>

<style>
  .best-practices-checklist {
    background-color: #f8f9fa;
    border-left: 4px solid #007bff;
    padding: 1.5rem;
    margin: 2rem 0;
  }

  .checklist-section {
    margin: 1.5rem 0;
  }

  .checklist-section h4 {
    color: #333;
    margin-bottom: 0.75rem;
  }

  .checklist-section label {
    display: block;
    margin: 0.5rem 0;
    cursor: pointer;
    user-select: none;
  }

  .checklist-section input[type='checkbox'] {
    margin-right: 0.5rem;
    transform: scale(1.1);
  }

  .checklist-section label:hover {
    background-color: rgba(0, 123, 255, 0.1);
    padding: 0.25rem;
    border-radius: 4px;
  }
</style>
```

---

**สรุป**: การใช้ multimedia อย่างมีประสิทธิภาพต้องคำนึงถึงทั้ง performance และ accessibility โดยหลีกเลี่ยง autoplay ที่รบกวนและใส่คำบรรยายสื่ออย่างครบถ้วน เพื่อให้เว็บไซต์เข้าถึงได้สำหรับผู้ใช้ทุกกลุ่ม
