# รูปตอบสนองและ Multimedia Attributes ขั้นสูง

## 1. Responsive Images ด้วย `<picture>` และ `<source>`

### 1.1 ภาพรวม Responsive Images

Responsive Images ช่วยให้เราส่งรูปภาพที่เหมาะสมกับอุปกรณ์และขนาดหน้าจอที่แตกต่างกัน เพื่อ:

- **ประหยัด bandwidth** - ส่งรูปขนาดเล็กให้อุปกรณ์มือถือ
- **ปรับปรุง performance** - โหลดเร็วขึ้นตามความเหมาะสม
- **รองรับ high-density displays** - Retina, 4K displays
- **Art Direction** - ใช้รูปที่ต่างกันตามขนาดหน้าจอ

## 2. `<picture>` Element

### 2.1 Syntax พื้นฐาน

```html
<picture>
  <source media="(min-width: 1200px)" srcset="image-large.jpg" />
  <source media="(min-width: 768px)" srcset="image-medium.jpg" />
  <source media="(max-width: 767px)" srcset="image-small.jpg" />
  <img src="image-default.jpg" alt="คำอธิบายรูปภาพ" />
</picture>
```

### 2.2 Art Direction - รูปภาพต่างกันตามอุปกรณ์

```html
<!-- ตัวอย่าง: รูปภาพแบนเนอร์ที่เปลี่ยนตามขนาดหน้าจอ -->
<picture>
  <!-- Desktop: รูปแนวนอนขนาดใหญ่ -->
  <source media="(min-width: 1024px)" srcset="banner-desktop.jpg" />

  <!-- Tablet: รูปแนวนอนขนาดกลาง -->
  <source media="(min-width: 768px)" srcset="banner-tablet.jpg" />

  <!-- Mobile: รูปแนวตั้งที่เหมาะกับมือถือ -->
  <source media="(max-width: 767px)" srcset="banner-mobile.jpg" />

  <!-- Fallback สำหรับเบราว์เซอร์เก่า -->
  <img src="banner-default.jpg" alt="แบนเนอร์โปรโมชั่นลดราคา 50%" />
</picture>
```

### 2.3 รองรับรูปแบบไฟล์ใหม่

```html
<!-- รองรับ WebP และ AVIF -->
<picture>
  <!-- รูปแบบใหม่ที่มีขนาดเล็กกว่า -->
  <source srcset="image.avif" type="image/avif" />
  <source srcset="image.webp" type="image/webp" />

  <!-- Fallback เป็น JPEG -->
  <img src="image.jpg" alt="รูปภาพสินค้า" />
</picture>

<!-- ตัวอย่างครบครัน: รูปแบบไฟล์ + ขนาดหน้าจอ -->
<picture>
  <!-- Desktop: AVIF -->
  <source
    media="(min-width: 1024px)"
    srcset="hero-desktop.avif"
    type="image/avif"
  />
  <source
    media="(min-width: 1024px)"
    srcset="hero-desktop.webp"
    type="image/webp"
  />
  <source media="(min-width: 1024px)" srcset="hero-desktop.jpg" />

  <!-- Tablet: WebP -->
  <source
    media="(min-width: 768px)"
    srcset="hero-tablet.webp"
    type="image/webp"
  />
  <source media="(min-width: 768px)" srcset="hero-tablet.jpg" />

  <!-- Mobile: เล็กสุด -->
  <source
    media="(max-width: 767px)"
    srcset="hero-mobile.webp"
    type="image/webp"
  />
  <source media="(max-width: 767px)" srcset="hero-mobile.jpg" />

  <img src="hero-default.jpg" alt="ภาพหลักของหน้าเว็บ" />
</picture>
```

## 3. `<img>` กับ `srcset` และ `sizes`

### 3.1 `srcset` - หลายความละเอียด

```html
<!-- Pixel density descriptors (1x, 2x, 3x) -->
<img
  src="logo.png"
  srcset="logo.png 1x, logo@2x.png 2x, logo@3x.png 3x"
  alt="โลโก้บริษัท"
/>

<!-- Width descriptors (w) -->
<img
  src="product-400.jpg"
  srcset="
    product-400.jpg   400w,
    product-800.jpg   800w,
    product-1200.jpg 1200w,
    product-1600.jpg 1600w
  "
  alt="รูปสินค้า"
/>
```

### 3.2 `sizes` - ขนาดการแสดงผล

```html
<!-- กำหนดขนาดการแสดงผลตามขนาดหน้าจอ -->
<img
  src="article-image-400.jpg"
  srcset="
    article-image-400.jpg   400w,
    article-image-800.jpg   800w,
    article-image-1200.jpg 1200w
  "
  sizes="(max-width: 768px) 100vw,
            (max-width: 1024px) 50vw,
            33vw"
  alt="รูปประกอบบทความ"
/>

<!-- ตัวอย่างเฉพาะเจาะจง -->
<img
  src="hero-image-600.jpg"
  srcset="
    hero-image-600.jpg   600w,
    hero-image-900.jpg   900w,
    hero-image-1200.jpg 1200w,
    hero-image-1800.jpg 1800w
  "
  sizes="(max-width: 480px) 100vw,
            (max-width: 768px) 90vw,
            (max-width: 1024px) 80vw,
            70vw"
  alt="ภาพหลักของหน้าแรก"
/>
```

### 3.3 ตัวอย่างการใช้งานจริง

```html
<!-- Gallery รูปภาพ -->
<div class="image-gallery">
  <div class="gallery-item">
    <picture>
      <source
        media="(min-width: 1024px)"
        srcset="gallery1-large.webp"
        type="image/webp"
      />
      <source media="(min-width: 1024px)" srcset="gallery1-large.jpg" />

      <source
        media="(min-width: 768px)"
        srcset="gallery1-medium.webp"
        type="image/webp"
      />
      <source media="(min-width: 768px)" srcset="gallery1-medium.jpg" />

      <img src="gallery1-small.jpg" alt="ภาพงานศิลปะชิ้นที่ 1" loading="lazy" />
    </picture>
  </div>

  <div class="gallery-item">
    <!-- รูปที่มีหลายขนาดพร้อม lazy loading -->
    <img
      src="gallery2-400.jpg"
      srcset="
        gallery2-400.jpg   400w,
        gallery2-600.jpg   600w,
        gallery2-800.jpg   800w,
        gallery2-1200.jpg 1200w
      "
      sizes="(max-width: 768px) 50vw,
                (max-width: 1024px) 33vw,
                25vw"
      alt="ภาพงานศิลปะชิ้นที่ 2"
      loading="lazy"
    />
  </div>
</div>

<style>
  .image-gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1rem;
    padding: 1rem;
  }

  .gallery-item img {
    width: 100%;
    height: auto;
    border-radius: 8px;
    transition: transform 0.3s ease;
  }

  .gallery-item img:hover {
    transform: scale(1.05);
  }
</style>
```

## 4. Multimedia Attributes ขั้นสูง

### 4.1 `controls` - การควบคุมที่กำหนดเอง

```html
<!-- Controls พื้นฐาน -->
<video controls width="800" height="450">
  <source src="video.mp4" type="video/mp4" />
</video>

<!-- Controls แบบกำหนดเอง -->
<div class="custom-video-player">
  <video id="custom-video" width="800" height="450">
    <source src="lesson.mp4" type="video/mp4" />
  </video>

  <div class="custom-controls">
    <button onclick="playPause()" id="play-pause">▶️</button>
    <input
      type="range"
      id="seek-bar"
      value="0"
      min="0"
      max="100"
      oninput="seek(this.value)"
    />
    <span id="time-display">0:00 / 0:00</span>
    <input
      type="range"
      id="volume-control"
      value="100"
      min="0"
      max="100"
      oninput="setVolume(this.value)"
    />
    <button onclick="toggleFullscreen()">⛶</button>
  </div>
</div>

<script>
  const video = document.getElementById('custom-video');
  const playPauseBtn = document.getElementById('play-pause');
  const seekBar = document.getElementById('seek-bar');
  const timeDisplay = document.getElementById('time-display');
  const volumeControl = document.getElementById('volume-control');

  function playPause() {
    if (video.paused) {
      video.play();
      playPauseBtn.textContent = '⏸️';
    } else {
      video.pause();
      playPauseBtn.textContent = '▶️';
    }
  }

  function seek(value) {
    const time = (value / 100) * video.duration;
    video.currentTime = time;
  }

  function setVolume(value) {
    video.volume = value / 100;
  }

  function toggleFullscreen() {
    if (video.requestFullscreen) {
      video.requestFullscreen();
    }
  }

  // อัปเดตเวลาและ progress bar
  video.addEventListener('timeupdate', function () {
    const progress = (video.currentTime / video.duration) * 100;
    seekBar.value = progress;

    const current = formatTime(video.currentTime);
    const duration = formatTime(video.duration);
    timeDisplay.textContent = `${current} / ${duration}`;
  });

  function formatTime(seconds) {
    const mins = Math.floor(seconds / 60);
    const secs = Math.floor(seconds % 60);
    return `${mins}:${secs.toString().padStart(2, '0')}`;
  }
</script>

<style>
  .custom-video-player {
    max-width: 800px;
    margin: 1rem 0;
  }

  .custom-controls {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.5rem;
    background-color: #333;
    color: white;
    border-radius: 0 0 4px 4px;
  }

  .custom-controls button {
    background: none;
    border: none;
    color: white;
    font-size: 1.2rem;
    cursor: pointer;
    padding: 0.25rem;
  }

  .custom-controls input[type='range'] {
    flex: 1;
  }

  #volume-control {
    max-width: 100px;
  }
</style>
```

### 4.2 `autoplay` - การใช้งานที่ถูกต้อง

```html
<!-- ❌ หลีกเลี่ยง: autoplay โดยไม่มี muted -->
<video autoplay controls>
  <source src="video.mp4" type="video/mp4" />
</video>

<!-- ✅ ถูกต้อง: autoplay พร้อม muted -->
<video autoplay muted controls playsinline>
  <source src="background-video.mp4" type="video/mp4" />
</video>

<!-- ✅ ตัวอย่างการใช้ autoplay อย่างระมัดระวัง -->
<div class="hero-video">
  <video autoplay muted loop playsinline poster="hero-poster.jpg">
    <source src="hero-background.mp4" type="video/mp4" />
    <source src="hero-background.webm" type="video/webm" />
  </video>

  <div class="hero-content">
    <h1>ยินดีต้อนรับสู่เว็บไซต์ของเรา</h1>
    <button onclick="enableAudio()" id="audio-btn">🔊 เปิดเสียง</button>
  </div>
</div>

<script>
  function enableAudio() {
    const video = document.querySelector('.hero-video video');
    const audioBtn = document.getElementById('audio-btn');

    video.muted = false;
    audioBtn.style.display = 'none';

    // แสดงข้อความแจ้งเตือน
    const notification = document.createElement('div');
    notification.textContent = 'เปิดเสียงแล้ว';
    notification.className = 'audio-notification';
    document.body.appendChild(notification);

    setTimeout(() => {
      notification.remove();
    }, 3000);
  }
</script>

<style>
  .hero-video {
    position: relative;
    width: 100%;
    height: 60vh;
    overflow: hidden;
  }

  .hero-video video {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .hero-content {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
    color: white;
    z-index: 1;
  }

  .hero-content h1 {
    font-size: 3rem;
    margin-bottom: 1rem;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
  }

  #audio-btn {
    padding: 0.75rem 1.5rem;
    font-size: 1.1rem;
    background-color: rgba(255, 255, 255, 0.9);
    border: none;
    border-radius: 25px;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  #audio-btn:hover {
    background-color: white;
  }

  .audio-notification {
    position: fixed;
    top: 20px;
    right: 20px;
    background-color: #4caf50;
    color: white;
    padding: 1rem;
    border-radius: 4px;
    z-index: 1000;
  }
</style>
```

### 4.3 `loop` - การเล่นซ้ำ

```html
<!-- Background video ที่เล่นซ้ำ -->
<video autoplay muted loop playsinline class="bg-video">
  <source src="background-loop.mp4" type="video/mp4" />
  <source src="background-loop.webm" type="video/webm" />
</video>

<!-- Audio background music -->
<audio id="bg-music" loop>
  <source src="background-music.mp3" type="audio/mpeg" />
  <source src="background-music.ogg" type="audio/ogg" />
</audio>

<div class="content-overlay">
  <h1>เนื้อหาหลักของเว็บไซต์</h1>
  <button onclick="toggleBackgroundMusic()">🎵 เปิด/ปิดเพลงพื้นหลัง</button>
</div>

<script>
  let musicPlaying = false;

  function toggleBackgroundMusic() {
    const bgMusic = document.getElementById('bg-music');

    if (musicPlaying) {
      bgMusic.pause();
      musicPlaying = false;
    } else {
      bgMusic.play();
      musicPlaying = true;
    }
  }
</script>

<style>
  .bg-video {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: -1;
  }

  .content-overlay {
    position: relative;
    z-index: 1;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: rgba(0, 0, 0, 0.3);
    color: white;
  }
</style>
```

### 4.4 `poster` - รูปตัวอย่าง

```html
<!-- Video พร้อม poster ที่ responsive -->
<video controls poster="video-poster.jpg" preload="metadata">
  <source src="educational-video.mp4" type="video/mp4" />
  <source src="educational-video.webm" type="video/webm" />
</video>

<!-- Poster ที่เปลี่ยนตามขนาดหน้าจอ -->
<video controls preload="none" id="responsive-poster-video">
  <source src="product-demo.mp4" type="video/mp4" />
</video>

<script>
  // เปลี่ยน poster ตามขนาดหน้าจอ
  function updatePoster() {
    const video = document.getElementById('responsive-poster-video');
    const width = window.innerWidth;

    if (width > 1024) {
      video.poster = 'poster-desktop.jpg';
    } else if (width > 768) {
      video.poster = 'poster-tablet.jpg';
    } else {
      video.poster = 'poster-mobile.jpg';
    }
  }

  // เรียกใช้เมื่อโหลดหน้าและเมื่อเปลี่ยนขนาดหน้าจอ
  updatePoster();
  window.addEventListener('resize', updatePoster);
</script>
```

## 5. Subtitles และ Captions ด้วย `<track>`

### 5.1 การใช้งาน `track kind="subtitles"`

```html
<video controls width="800" height="450" poster="lesson-poster.jpg">
  <source src="web-development-course.mp4" type="video/mp4" />
  <source src="web-development-course.webm" type="video/webm" />

  <!-- Subtitles หลายภาษา -->
  <track
    kind="subtitles"
    src="subtitles-th.vtt"
    srclang="th"
    label="ไทย"
    default
  />
  <track kind="subtitles" src="subtitles-en.vtt" srclang="en" label="English" />
  <track kind="subtitles" src="subtitles-zh.vtt" srclang="zh" label="中文" />

  <!-- Captions สำหรับผู้พิการทางการได้ยิน -->
  <track
    kind="captions"
    src="captions-th.vtt"
    srclang="th"
    label="คำบรรยายเสียง (ไทย)"
  />

  <!-- Chapters -->
  <track kind="chapters" src="chapters.vtt" srclang="th" label="บทเรียน" />

  <!-- Descriptions สำหรับผู้พิการทางสายตา -->
  <track
    kind="descriptions"
    src="descriptions-th.vtt"
    srclang="th"
    label="คำอธิบายภาพ"
  />
</video>
```

### 5.2 ไฟล์ WebVTT สำหรับ Subtitles

#### subtitles-th.vtt:

```
WEBVTT

NOTE
ไฟล์ซับไตเติลภาษาไทยสำหรับบทเรียน Web Development

00:00:00.000 --> 00:00:05.000
สวัสดีครับ ยินดีต้อนรับสู่บทเรียน HTML5 Multimedia

00:00:05.000 --> 00:00:10.000
วันนี้เราจะมาเรียนรู้เกี่ยวกับการใช้งาน audio และ video elements

00:00:10.000 --> 00:00:15.000
รวมถึงการทำ responsive images ด้วย picture element

00:00:15.000 --> 00:00:20.000
<v ผู้สอน>ครั้งแรกเราจะเริ่มจากการใช้งาน video element</v>

00:00:20.000 --> 00:00:25.000
<v ผู้สอน>การใส่ attributes ต่างๆ เช่น controls, autoplay</v>

00:00:25.000 --> 00:00:30.000
<i>แต่ต้องระวังเรื่อง autoplay ที่อาจรบกวนผู้ใช้</i>

00:00:30.000 --> 00:00:35.000
<b>ข้อสำคัญ:</b> ควรใช้ muted ร่วมกับ autoplay เสมอ
```

#### captions-th.vtt (รวมเสียงสิ่งแวดล้อม):

```
WEBVTT

00:00:00.000 --> 00:00:05.000
สวัสดีครับ ยินดีต้อนรับสู่บทเรียน HTML5 Multimedia

00:00:05.000 --> 00:00:08.000
[เสียงคลิกเมาส์]

00:00:08.000 --> 00:00:10.000
วันนี้เราจะมาเรียนรู้เกี่ยวกับการใช้งาน audio และ video elements

00:00:10.000 --> 00:00:12.000
[เสียงพิมพ์คีย์บอร์ด]

00:00:12.000 --> 00:00:15.000
รวมถึงการทำ responsive images ด้วย picture element

00:00:15.000 --> 00:00:18.000
[เสียงเปิดไฟล์]

00:00:18.000 --> 00:00:20.000
ครั้งแรกเราจะเริ่มจากการใช้งาน video element
```

#### chapters.vtt:

```
WEBVTT

Chapter 1
00:00:00.000 --> 00:02:30.000
บทนำ - ความสำคัญของ Multimedia

Chapter 2
00:02:30.000 --> 00:05:45.000
Video Element และ Attributes

Chapter 3
00:05:45.000 --> 00:08:30.000
Audio Element และการควบคุม

Chapter 4
00:08:30.000 --> 00:12:15.000
Responsive Images ด้วย Picture

Chapter 5
00:12:15.000 --> 00:15:00.000
Best Practices และ Accessibility

Chapter 6
00:15:00.000 --> 00:18:00.000
สรุปและแนวทางต่อไป
```

### 5.3 Video Player พร้อม Subtitle Controls

```html
<div class="advanced-video-player">
  <video id="lesson-video" width="800" height="450" poster="lesson-poster.jpg">
    <source src="html5-lesson.mp4" type="video/mp4" />
    <source src="html5-lesson.webm" type="video/webm" />

    <track
      kind="subtitles"
      src="subs-th.vtt"
      srclang="th"
      label="ไทย"
      default
    />
    <track kind="subtitles" src="subs-en.vtt" srclang="en" label="English" />
    <track
      kind="captions"
      src="captions-th.vtt"
      srclang="th"
      label="คำบรรยาย"
    />
    <track kind="chapters" src="chapters.vtt" srclang="th" label="บท" />
  </video>

  <div class="video-controls">
    <button onclick="togglePlay()">▶️ Play</button>

    <div class="subtitle-controls">
      <label for="subtitle-track">ซับไตเติล:</label>
      <select id="subtitle-track" onchange="changeSubtitleTrack(this.value)">
        <option value="-1">ปิด</option>
        <option value="0" selected>ไทย</option>
        <option value="1">English</option>
      </select>

      <label for="caption-track">คำบรรยาย:</label>
      <select id="caption-track" onchange="changeCaptionTrack(this.value)">
        <option value="-1" selected>ปิด</option>
        <option value="2">ไทย (รวมเสียง)</option>
      </select>
    </div>

    <div class="playback-controls">
      <label for="playback-rate">ความเร็ว:</label>
      <select id="playback-rate" onchange="changePlaybackRate(this.value)">
        <option value="0.25">0.25x</option>
        <option value="0.5">0.5x</option>
        <option value="0.75">0.75x</option>
        <option value="1" selected>1x</option>
        <option value="1.25">1.25x</option>
        <option value="1.5">1.5x</option>
        <option value="2">2x</option>
      </select>
    </div>
  </div>

  <div class="chapters-navigation">
    <h4>บทเรียน:</h4>
    <div id="chapters-list"></div>
  </div>

  <div class="transcript-section">
    <details>
      <summary>📝 Transcript ของบทเรียน</summary>
      <div class="transcript-content">
        <p><strong>00:00 - 02:30 บทนำ</strong></p>
        <p>
          สวัสดีครับ ยินดีต้อนรับสู่บทเรียน HTML5 Multimedia
          วันนี้เราจะมาเรียนรู้เกี่ยวกับการใช้งาน audio และ video elements
          รวมถึงการทำ responsive images ด้วย picture element
        </p>

        <p><strong>02:30 - 05:45 Video Element</strong></p>
        <p>
          ครั้งแรกเราจะเริ่มจากการใช้งาน video element การใส่ attributes ต่างๆ
          เช่น controls, autoplay แต่ต้องระวังเรื่อง autoplay ที่อาจรบกวนผู้ใช้
        </p>

        <p><strong>05:45 - 08:30 Audio Element</strong></p>
        <p>
          ต่อมาเราจะเรียนรู้เกี่ยวกับ audio element และการสร้าง music player
          ที่สามารถควบคุมได้
        </p>
      </div>
    </details>
  </div>
</div>

<script>
  const video = document.getElementById('lesson-video');
  const subtitleSelect = document.getElementById('subtitle-track');
  const captionSelect = document.getElementById('caption-track');
  const chaptersList = document.getElementById('chapters-list');

  function togglePlay() {
    if (video.paused) {
      video.play();
    } else {
      video.pause();
    }
  }

  function changeSubtitleTrack(trackIndex) {
    const tracks = video.textTracks;

    // ปิดทุก subtitle track
    for (let i = 0; i < tracks.length; i++) {
      if (tracks[i].kind === 'subtitles') {
        tracks[i].mode = 'hidden';
      }
    }

    // เปิด track ที่เลือก
    if (trackIndex >= 0) {
      tracks[trackIndex].mode = 'showing';
    }
  }

  function changeCaptionTrack(trackIndex) {
    const tracks = video.textTracks;

    // ปิดทุก caption track
    for (let i = 0; i < tracks.length; i++) {
      if (tracks[i].kind === 'captions') {
        tracks[i].mode = 'hidden';
      }
    }

    // เปิด track ที่เลือก
    if (trackIndex >= 0) {
      tracks[trackIndex].mode = 'showing';
    }
  }

  function changePlaybackRate(rate) {
    video.playbackRate = parseFloat(rate);
  }

  // โหลด chapters
  video.addEventListener('loadedmetadata', function () {
    const tracks = video.textTracks;

    for (let i = 0; i < tracks.length; i++) {
      if (tracks[i].kind === 'chapters') {
        tracks[i].mode = 'hidden';

        tracks[i].addEventListener('load', function () {
          loadChapters(tracks[i]);
        });

        break;
      }
    }
  });

  function loadChapters(chapterTrack) {
    const cues = chapterTrack.cues;

    for (let i = 0; i < cues.length; i++) {
      const cue = cues[i];
      const button = document.createElement('button');
      button.textContent = `${formatTime(cue.startTime)} - ${cue.text}`;
      button.className = 'chapter-btn';
      button.onclick = function () {
        video.currentTime = cue.startTime;
        video.play();
      };
      chaptersList.appendChild(button);
    }
  }

  function formatTime(seconds) {
    const mins = Math.floor(seconds / 60);
    const secs = Math.floor(seconds % 60);
    return `${mins}:${secs.toString().padStart(2, '0')}`;
  }
</script>

<style>
  .advanced-video-player {
    max-width: 850px;
    margin: 2rem auto;
    border: 1px solid #ddd;
    border-radius: 8px;
    overflow: hidden;
  }

  #lesson-video {
    width: 100%;
    height: auto;
    display: block;
  }

  .video-controls {
    padding: 1rem;
    background-color: #f8f9fa;
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    align-items: center;
  }

  .subtitle-controls,
  .playback-controls {
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }

  .subtitle-controls select,
  .playback-controls select {
    padding: 0.25rem;
    border: 1px solid #ddd;
    border-radius: 4px;
  }

  .chapters-navigation {
    padding: 1rem;
    background-color: #fff;
    border-top: 1px solid #eee;
  }

  .chapters-navigation h4 {
    margin: 0 0 0.5rem 0;
    color: #333;
  }

  .chapter-btn {
    display: block;
    width: 100%;
    margin: 0.25rem 0;
    padding: 0.5rem;
    text-align: left;
    border: 1px solid #ddd;
    border-radius: 4px;
    background: white;
    cursor: pointer;
    transition: background-color 0.2s;
  }

  .chapter-btn:hover {
    background-color: #f0f0f0;
  }

  .transcript-section {
    padding: 1rem;
    background-color: #f8f9fa;
    border-top: 1px solid #eee;
  }

  .transcript-content {
    margin-top: 1rem;
    line-height: 1.6;
    color: #555;
  }

  .transcript-content p {
    margin: 1rem 0;
  }

  /* Responsive adjustments */
  @media (max-width: 768px) {
    .video-controls {
      flex-direction: column;
      align-items: stretch;
    }

    .subtitle-controls,
    .playback-controls {
      justify-content: space-between;
    }
  }
</style>
```

## 6. Best Practices และ Performance

### 6.1 การเลือกรูปแบบไฟล์

```html
<!-- ✅ ลำดับความสำคัญของรูปแบบไฟล์ -->
<picture>
  <!-- รูปแบบใหม่ที่มีประสิทธิภาพสูง -->
  <source srcset="image.avif" type="image/avif" />
  <source srcset="image.webp" type="image/webp" />

  <!-- Fallback -->
  <img src="image.jpg" alt="รูปภาพ" />
</picture>

<!-- สำหรับ video -->
<video controls>
  <source src="video.webm" type="video/webm" />
  <!-- ขนาดเล็ก -->
  <source src="video.mp4" type="video/mp4" />
  <!-- รองรับทุก browser -->
</video>
```

### 6.2 การใช้ `loading="lazy"`

```html
<!-- ✅ Lazy loading สำหรับรูปที่อยู่ล่างๆ -->
<img src="image1.jpg" alt="รูปแรก" />
<!-- โหลดทันที -->

<img src="image2.jpg" alt="รูปที่สอง" loading="lazy" />
<!-- โหลดเมื่อเลื่อนมาใกล้ -->

<picture>
  <source srcset="gallery.webp" type="image/webp" />
  <img src="gallery.jpg" alt="รูปในแกลเลอรี่" loading="lazy" />
</picture>
```

### 6.3 การจัดการ Accessibility

```html
<!-- ✅ Accessibility ที่ครบถ้วน -->
<video controls aria-label="วิดีโอสอน HTML5 Multimedia">
  <source src="lesson.mp4" type="video/mp4" />

  <!-- Subtitles สำหรับผู้ที่ต้องการ -->
  <track kind="subtitles" src="subs-th.vtt" srclang="th" label="ไทย" default />

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
</video>

<!-- Transcript ไว้ใต้วิดีโอ -->
<section aria-labelledby="transcript-heading">
  <h3 id="transcript-heading">เนื้อหาของวิดีโอ</h3>
  <div class="transcript">
    <!-- เนื้อหาทั้งหมดของวิดีโอ -->
  </div>
</section>
```

---

**สรุป**: การใช้ responsive images และ multimedia attributes อย่างถูกต้องจะช่วยให้เว็บไซต์มีประสิทธิภาพดี โหลดเร็ว และเข้าถึงได้สำหรับผู้ใช้ทุกกลุ่ม โดยเฉพาะการใส่ subtitles และ captions ที่จำเป็นสำหรับ accessibility
