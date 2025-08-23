# Phase 7: สื่อ (Multimedia) - Audio, Video และ Elements เสริม

## 1. ภาพรวม Multimedia ใน HTML5

HTML5 นำเสนอ native multimedia support ที่ช่วยให้เราสามารถฝังเสียงและวิดีโอได้โดยไม่ต้องพึ่งพา plugins เช่น Flash

**Elements หลัก:**

- `<audio>`: สำหรับไฟล์เสียง
- `<video>`: สำหรับไฟล์วิดีโอ
- `<source>`: กำหนดแหล่งที่มาของสื่อหลายรูปแบบ
- `<track>`: สำหรับ subtitles, captions, chapters

**ประโยชน์:**

- ไม่ต้องใช้ plugins
- รองรับ accessibility
- ควบคุมได้ด้วย JavaScript
- Responsive และ mobile-friendly

## 2. `<audio>` Element - เสียง

### 2.1 Syntax พื้นฐาน

```html
<audio controls>
  <source src="audio-file.mp3" type="audio/mpeg" />
  <source src="audio-file.ogg" type="audio/ogg" />
  เบราว์เซอร์ของคุณไม่รองรับ audio element
</audio>
```

### 2.2 Attributes สำคัญของ `<audio>`

#### `controls` - แสดงปุ่มควบคุม

```html
<!-- แสดงปุ่มควบคุม -->
<audio controls>
  <source src="music.mp3" type="audio/mpeg" />
</audio>

<!-- ไม่แสดงปุ่มควบคุม (ควบคุมด้วย JavaScript) -->
<audio id="background-music">
  <source src="background.mp3" type="audio/mpeg" />
</audio>
```

#### `autoplay` - เล่นอัตโนมัติ

```html
<!-- เล่นทันทีเมื่อโหลดหน้า (ใช้ด้วยความระมัดระวัง) -->
<audio controls autoplay>
  <source src="intro.mp3" type="audio/mpeg" />
</audio>

<!-- เล่นอัตโนมัติแต่ปิดเสียง -->
<audio controls autoplay muted>
  <source src="ambient.mp3" type="audio/mpeg" />
</audio>
```

#### `loop` - เล่นซ้ำ

```html
<audio controls loop>
  <source src="background-music.mp3" type="audio/mpeg" />
</audio>
```

#### `muted` - ปิดเสียง

```html
<audio controls muted>
  <source src="audio.mp3" type="audio/mpeg" />
</audio>
```

#### `preload` - การโหลดล่วงหน้า

```html
<!-- โหลดทั้งไฟล์ -->
<audio controls preload="auto">
  <source src="song.mp3" type="audio/mpeg" />
</audio>

<!-- โหลดเฉพาะ metadata -->
<audio controls preload="metadata">
  <source src="podcast.mp3" type="audio/mpeg" />
</audio>

<!-- ไม่โหลดล่วงหน้า -->
<audio controls preload="none">
  <source src="large-file.mp3" type="audio/mpeg" />
</audio>
```

### 2.3 ตัวอย่างการใช้งาน Audio

#### Music Player พื้นฐาน

```html
<div class="music-player">
  <h3>🎵 Music Player</h3>

  <audio id="music-player" controls>
    <source src="assets/music/song1.mp3" type="audio/mpeg" />
    <source src="assets/music/song1.ogg" type="audio/ogg" />
    เบราว์เซอร์ของคุณไม่รองรับการเล่นเสียง
  </audio>

  <div class="playlist">
    <h4>Playlist:</h4>
    <ul>
      <li><button onclick="playMusic('song1')">🎵 เพลงที่ 1</button></li>
      <li><button onclick="playMusic('song2')">🎵 เพลงที่ 2</button></li>
      <li><button onclick="playMusic('song3')">🎵 เพลงที่ 3</button></li>
    </ul>
  </div>

  <div class="player-info">
    <div>กำลังเล่น: <span id="current-song">เพลงที่ 1</span></div>
    <div>
      เวลา: <span id="current-time">0:00</span> /
      <span id="duration">0:00</span>
    </div>
  </div>
</div>

<script>
  const audioPlayer = document.getElementById('music-player');
  const currentSongSpan = document.getElementById('current-song');
  const currentTimeSpan = document.getElementById('current-time');
  const durationSpan = document.getElementById('duration');

  const songs = {
    song1: { src: 'assets/music/song1.mp3', title: 'เพลงที่ 1' },
    song2: { src: 'assets/music/song2.mp3', title: 'เพลงที่ 2' },
    song3: { src: 'assets/music/song3.mp3', title: 'เพลงที่ 3' },
  };

  function playMusic(songKey) {
    const song = songs[songKey];
    audioPlayer.src = song.src;
    currentSongSpan.textContent = song.title;
    audioPlayer.play();
  }

  // อัปเดตเวลา
  audioPlayer.addEventListener('timeupdate', function () {
    const current = Math.floor(audioPlayer.currentTime);
    const duration = Math.floor(audioPlayer.duration);

    currentTimeSpan.textContent = formatTime(current);
    if (!isNaN(duration)) {
      durationSpan.textContent = formatTime(duration);
    }
  });

  function formatTime(seconds) {
    const mins = Math.floor(seconds / 60);
    const secs = seconds % 60;
    return `${mins}:${secs.toString().padStart(2, '0')}`;
  }

  // โหลด duration เมื่อไฟล์พร้อม
  audioPlayer.addEventListener('loadedmetadata', function () {
    durationSpan.textContent = formatTime(Math.floor(audioPlayer.duration));
  });
</script>

<style>
  .music-player {
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 1rem;
    max-width: 400px;
    margin: 1rem 0;
  }

  .playlist ul {
    list-style: none;
    padding: 0;
  }

  .playlist button {
    width: 100%;
    padding: 0.5rem;
    margin: 0.25rem 0;
    border: 1px solid #ddd;
    border-radius: 4px;
    background: white;
    cursor: pointer;
    text-align: left;
  }

  .playlist button:hover {
    background-color: #f0f0f0;
  }

  .player-info {
    margin-top: 1rem;
    font-size: 0.9rem;
    color: #666;
  }
</style>
```

#### Podcast Player

```html
<div class="podcast-player">
  <h3>🎙️ Podcast Player</h3>

  <div class="episode-info">
    <h4>Episode 1: Introduction to Web Development</h4>
    <p>เรียนรู้พื้นฐานการพัฒนาเว็บไซต์</p>
    <div class="episode-meta">
      <span>⏱️ 45:30</span>
      <span>📅 March 15, 2024</span>
    </div>
  </div>

  <audio id="podcast" controls preload="metadata">
    <source src="assets/podcasts/episode1.mp3" type="audio/mpeg" />
    <source src="assets/podcasts/episode1.ogg" type="audio/ogg" />
    เบราว์เซอร์ของคุณไม่รองรับการเล่นเสียง
  </audio>

  <div class="podcast-controls">
    <button onclick="skipTime(-10)">⏪ -10s</button>
    <button onclick="togglePlayPause()" id="play-pause-btn">
      ⏯️ Play/Pause
    </button>
    <button onclick="skipTime(30)">⏩ +30s</button>
  </div>

  <div class="speed-control">
    <label for="playback-speed">ความเร็ว:</label>
    <select id="playback-speed" onchange="changeSpeed(this.value)">
      <option value="0.5">0.5x</option>
      <option value="0.75">0.75x</option>
      <option value="1" selected>1x</option>
      <option value="1.25">1.25x</option>
      <option value="1.5">1.5x</option>
      <option value="2">2x</option>
    </select>
  </div>
</div>

<script>
  const podcast = document.getElementById('podcast');
  const playPauseBtn = document.getElementById('play-pause-btn');

  function togglePlayPause() {
    if (podcast.paused) {
      podcast.play();
    } else {
      podcast.pause();
    }
  }

  function skipTime(seconds) {
    podcast.currentTime += seconds;
  }

  function changeSpeed(rate) {
    podcast.playbackRate = parseFloat(rate);
  }

  // อัปเดตปุ่ม play/pause
  podcast.addEventListener('play', () => {
    playPauseBtn.textContent = '⏸️ Pause';
  });

  podcast.addEventListener('pause', () => {
    playPauseBtn.textContent = '▶️ Play';
  });
</script>

<style>
  .podcast-player {
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 1.5rem;
    max-width: 500px;
    margin: 1rem 0;
    background-color: #f9f9f9;
  }

  .episode-info h4 {
    margin: 0 0 0.5rem 0;
    color: #333;
  }

  .episode-meta {
    font-size: 0.9rem;
    color: #666;
    margin: 0.5rem 0;
  }

  .episode-meta span {
    margin-right: 1rem;
  }

  .podcast-controls {
    margin: 1rem 0;
    text-align: center;
  }

  .podcast-controls button {
    margin: 0 0.5rem;
    padding: 0.5rem 1rem;
    border: 1px solid #ddd;
    border-radius: 4px;
    background: white;
    cursor: pointer;
  }

  .speed-control {
    margin-top: 1rem;
  }

  .speed-control select {
    margin-left: 0.5rem;
    padding: 0.25rem;
  }
</style>
```

## 3. `<video>` Element - วิดีโอ

### 3.1 Syntax พื้นฐาน

```html
<video controls width="640" height="360">
  <source src="video.mp4" type="video/mp4" />
  <source src="video.webm" type="video/webm" />
  <source src="video.ogg" type="video/ogg" />
  เบราว์เซอร์ของคุณไม่รองรับ video element
</video>
```

### 3.2 Attributes สำคัญของ `<video>`

#### ขนาดและการแสดงผล

```html
<!-- กำหนดขนาด -->
<video controls width="800" height="450">
  <source src="movie.mp4" type="video/mp4" />
</video>

<!-- รูปภาพตัวอย่าง -->
<video controls poster="thumbnail.jpg" width="640" height="360">
  <source src="video.mp4" type="video/mp4" />
</video>

<!-- Responsive video -->
<video controls style="width: 100%; height: auto; max-width: 800px;">
  <source src="responsive-video.mp4" type="video/mp4" />
</video>
```

#### การควบคุมการเล่น

```html
<!-- เล่นอัตโนมัติ (ใช้ด้วยความระมัดระวัง) -->
<video controls autoplay muted>
  <source src="intro-video.mp4" type="video/mp4" />
</video>

<!-- เล่นซ้ำ -->
<video controls loop>
  <source src="background-video.mp4" type="video/mp4" />
</video>

<!-- ไม่มีเสียง -->
<video controls muted>
  <source src="silent-video.mp4" type="video/mp4" />
</video>
```

### 3.3 ตัวอย่างการใช้งาน Video

#### Video Player ขั้นสูง

```html
<div class="video-player">
  <h3>🎬 Video Player</h3>

  <video
    id="main-video"
    width="800"
    height="450"
    poster="assets/videos/poster.jpg"
  >
    <source src="assets/videos/sample.mp4" type="video/mp4" />
    <source src="assets/videos/sample.webm" type="video/webm" />
    เบราว์เซอร์ของคุณไม่รองรับการเล่นวิดีโอ
  </video>

  <div class="video-controls">
    <button onclick="togglePlay()" id="play-btn">▶️ Play</button>
    <button onclick="stopVideo()">⏹️ Stop</button>
    <button onclick="toggleMute()" id="mute-btn">🔊 Mute</button>
    <button onclick="toggleFullscreen()">🔲 Fullscreen</button>
  </div>

  <div class="video-progress">
    <label for="seek-bar">ความคืบหน้า:</label>
    <input
      type="range"
      id="seek-bar"
      value="0"
      min="0"
      max="100"
      oninput="seekVideo(this.value)"
    />
    <span id="video-time">0:00 / 0:00</span>
  </div>

  <div class="volume-control">
    <label for="volume-bar">เสียง:</label>
    <input
      type="range"
      id="volume-bar"
      value="100"
      min="0"
      max="100"
      oninput="changeVolume(this.value)"
    />
    <span id="volume-display">100%</span>
  </div>

  <div class="video-info">
    <h4>ข้อมูลวิดีโอ</h4>
    <div>ความละเอียด: <span id="resolution">-</span></div>
    <div>ระยะเวลา: <span id="total-duration">-</span></div>
    <div>สถานะ: <span id="video-status">พร้อม</span></div>
  </div>
</div>

<script>
  const video = document.getElementById('main-video');
  const playBtn = document.getElementById('play-btn');
  const muteBtn = document.getElementById('mute-btn');
  const seekBar = document.getElementById('seek-bar');
  const volumeBar = document.getElementById('volume-bar');
  const videoTime = document.getElementById('video-time');
  const volumeDisplay = document.getElementById('volume-display');
  const videoStatus = document.getElementById('video-status');
  const resolution = document.getElementById('resolution');
  const totalDuration = document.getElementById('total-duration');

  function togglePlay() {
    if (video.paused) {
      video.play();
      playBtn.textContent = '⏸️ Pause';
      videoStatus.textContent = 'กำลังเล่น';
    } else {
      video.pause();
      playBtn.textContent = '▶️ Play';
      videoStatus.textContent = 'หยุดชั่วคราว';
    }
  }

  function stopVideo() {
    video.pause();
    video.currentTime = 0;
    playBtn.textContent = '▶️ Play';
    videoStatus.textContent = 'หยุด';
  }

  function toggleMute() {
    video.muted = !video.muted;
    muteBtn.textContent = video.muted ? '🔇 Unmute' : '🔊 Mute';
  }

  function seekVideo(value) {
    const time = (value / 100) * video.duration;
    video.currentTime = time;
  }

  function changeVolume(value) {
    video.volume = value / 100;
    volumeDisplay.textContent = value + '%';
  }

  function toggleFullscreen() {
    if (video.requestFullscreen) {
      video.requestFullscreen();
    } else if (video.webkitRequestFullscreen) {
      video.webkitRequestFullscreen();
    } else if (video.msRequestFullscreen) {
      video.msRequestFullscreen();
    }
  }

  // Event listeners
  video.addEventListener('timeupdate', function () {
    const progress = (video.currentTime / video.duration) * 100;
    seekBar.value = progress;

    const current = formatTime(video.currentTime);
    const duration = formatTime(video.duration);
    videoTime.textContent = `${current} / ${duration}`;
  });

  video.addEventListener('loadedmetadata', function () {
    totalDuration.textContent = formatTime(video.duration);
    resolution.textContent = `${video.videoWidth} x ${video.videoHeight}`;
    seekBar.max = 100;
  });

  video.addEventListener('ended', function () {
    playBtn.textContent = '▶️ Play';
    videoStatus.textContent = 'จบแล้ว';
  });

  function formatTime(seconds) {
    if (isNaN(seconds)) return '0:00';
    const mins = Math.floor(seconds / 60);
    const secs = Math.floor(seconds % 60);
    return `${mins}:${secs.toString().padStart(2, '0')}`;
  }
</script>

<style>
  .video-player {
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 1rem;
    max-width: 850px;
    margin: 1rem 0;
  }

  #main-video {
    width: 100%;
    height: auto;
    border-radius: 4px;
  }

  .video-controls {
    margin: 1rem 0;
  }

  .video-controls button {
    margin-right: 0.5rem;
    padding: 0.5rem 1rem;
    border: 1px solid #ddd;
    border-radius: 4px;
    background: white;
    cursor: pointer;
  }

  .video-controls button:hover {
    background-color: #f0f0f0;
  }

  .video-progress,
  .volume-control {
    margin: 0.5rem 0;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }

  .video-progress input[type='range'],
  .volume-control input[type='range'] {
    flex: 1;
  }

  .video-info {
    margin-top: 1rem;
    padding: 1rem;
    background-color: #f9f9f9;
    border-radius: 4px;
  }

  .video-info h4 {
    margin: 0 0 0.5rem 0;
  }

  .video-info div {
    margin: 0.25rem 0;
    font-size: 0.9rem;
  }
</style>
```

## 4. `<source>` Element - แหล่งที่มาหลายรูปแบบ

### 4.1 การใช้งาน Source

```html
<!-- Audio กับหลายรูปแบบ -->
<audio controls>
  <source src="audio.mp3" type="audio/mpeg" />
  <source src="audio.ogg" type="audio/ogg" />
  <source src="audio.wav" type="audio/wav" />
  เบราว์เซอร์ของคุณไม่รองรับการเล่นเสียง
</audio>

<!-- Video กับหลายรูปแบบ -->
<video controls>
  <source src="video.mp4" type="video/mp4" />
  <source src="video.webm" type="video/webm" />
  <source src="video.ogg" type="video/ogg" />
  เบราว์เซอร์ของคุณไม่รองรับการเล่นวิดีโอ
</video>
```

### 4.2 Media Queries กับ Source

```html
<!-- Responsive video sources -->
<video controls>
  <source src="video-4k.mp4" type="video/mp4" media="(min-width: 1920px)" />
  <source src="video-hd.mp4" type="video/mp4" media="(min-width: 1280px)" />
  <source src="video-mobile.mp4" type="video/mp4" media="(max-width: 768px)" />
  <source src="video-default.mp4" type="video/mp4" />
</video>

<!-- Audio แยกตามคุณภาพ -->
<audio controls>
  <source src="audio-hq.mp3" type="audio/mpeg" media="(min-width: 1024px)" />
  <source src="audio-mobile.mp3" type="audio/mpeg" />
</audio>
```

### 4.3 ตัวอย่างการจัดการ Fallback

```html
<div class="media-container">
  <video controls poster="video-poster.jpg">
    <source src="assets/video.mp4" type="video/mp4" />
    <source src="assets/video.webm" type="video/webm" />

    <!-- Fallback สำหรับเบราว์เซอร์ที่ไม่รองรับ -->
    <div class="video-fallback">
      <h3>เบราว์เซอร์ของคุณไม่รองรับการเล่นวิดีโอ</h3>
      <p>
        กรุณา
        <a href="assets/video.mp4" download>ดาวน์โหลดวิดีโอ</a>
        เพื่อดูในโปรแกรมอื่น
      </p>

      <!-- หรือใช้ YouTube embed เป็น fallback -->
      <iframe
        width="560"
        height="315"
        src="https://www.youtube.com/embed/VIDEO_ID"
        frameborder="0"
        allowfullscreen
      >
      </iframe>
    </div>
  </video>
</div>

<style>
  .video-fallback {
    text-align: center;
    padding: 2rem;
    background-color: #f8f9fa;
    border: 1px solid #dee2e6;
    border-radius: 4px;
  }

  .video-fallback a {
    color: #007bff;
    text-decoration: none;
    font-weight: bold;
  }

  .video-fallback a:hover {
    text-decoration: underline;
  }
</style>
```

## 5. `<track>` Element - Subtitles และ Captions

### 5.1 การใช้งาน Track

```html
<video controls>
  <source src="movie.mp4" type="video/mp4" />

  <!-- Subtitles ภาษาไทย -->
  <track
    kind="subtitles"
    src="subtitles-th.vtt"
    srclang="th"
    label="ไทย"
    default
  />

  <!-- Subtitles ภาษาอังกฤษ -->
  <track kind="subtitles" src="subtitles-en.vtt" srclang="en" label="English" />

  <!-- Captions สำหรับผู้พิการทางการได้ยิน -->
  <track
    kind="captions"
    src="captions.vtt"
    srclang="th"
    label="คำบรรยายเสียง"
  />

  <!-- Chapters -->
  <track kind="chapters" src="chapters.vtt" srclang="th" label="บท" />

  <!-- Descriptions -->
  <track
    kind="descriptions"
    src="descriptions.vtt"
    srclang="th"
    label="คำอธิบาย"
  />
</video>
```

### 5.2 ไฟล์ WebVTT (.vtt)

#### ตัวอย่างไฟล์ subtitles-th.vtt:

```
WEBVTT

00:00:00.000 --> 00:00:05.000
สวัสดีครับ ยินดีต้อนรับสู่วิดีโอของเรา

00:00:05.000 --> 00:00:10.000
วันนี้เราจะมาเรียนรู้เกี่ยวกับ HTML5

00:00:10.000 --> 00:00:15.000
โดยเฉพาะเรื่องของ multimedia elements

NOTE
นี่คือ comment ที่จะไม่แสดงผล

00:00:15.000 --> 00:00:20.000
<v Speaker1>ผู้พูดคนแรก: ข้อความของผู้พูดคนแรก</v>

00:00:20.000 --> 00:00:25.000
<v Speaker2>ผู้พูดคนที่สอง: ข้อความของผู้พูดคนที่สอง</v>
```

#### ตัวอย่างไฟล์ chapters.vtt:

```
WEBVTT

Chapter 1
00:00:00.000 --> 00:02:30.000
บทนำ

Chapter 2
00:02:30.000 --> 00:05:45.000
HTML5 Multimedia

Chapter 3
00:05:45.000 --> 00:08:15.000
Audio Element

Chapter 4
00:08:15.000 --> 00:11:30.000
Video Element

Chapter 5
00:11:30.000 --> 00:15:00.000
สรุป
```

### 5.3 Custom Video Player พร้อม Subtitles

```html
<div class="custom-video-player">
  <video id="video-with-subs" width="800" height="450">
    <source src="assets/lesson.mp4" type="video/mp4" />
    <track
      kind="subtitles"
      src="assets/subs-th.vtt"
      srclang="th"
      label="ไทย"
      default
    />
    <track
      kind="subtitles"
      src="assets/subs-en.vtt"
      srclang="en"
      label="English"
    />
    <track kind="chapters" src="assets/chapters.vtt" srclang="th" label="บท" />
  </video>

  <div class="player-controls">
    <button onclick="togglePlaySubs()" id="play-subs-btn">▶️ Play</button>
    <button onclick="toggleSubtitles()" id="subs-btn">💬 Subtitles: ON</button>

    <select id="subtitle-select" onchange="changeSubtitleTrack(this.value)">
      <option value="-1">ไม่มีซับไตเติล</option>
      <option value="0" selected>ไทย</option>
      <option value="1">English</option>
    </select>
  </div>

  <div class="chapters-menu">
    <h4>บทต่างๆ:</h4>
    <div id="chapters-list"></div>
  </div>
</div>

<script>
  const videoSubs = document.getElementById('video-with-subs');
  const playSubsBtn = document.getElementById('play-subs-btn');
  const subsBtn = document.getElementById('subs-btn');
  const subtitleSelect = document.getElementById('subtitle-select');
  const chaptersList = document.getElementById('chapters-list');

  let subtitlesEnabled = true;

  function togglePlaySubs() {
    if (videoSubs.paused) {
      videoSubs.play();
      playSubsBtn.textContent = '⏸️ Pause';
    } else {
      videoSubs.pause();
      playSubsBtn.textContent = '▶️ Play';
    }
  }

  function toggleSubtitles() {
    subtitlesEnabled = !subtitlesEnabled;

    const tracks = videoSubs.textTracks;
    for (let i = 0; i < tracks.length; i++) {
      if (tracks[i].kind === 'subtitles') {
        tracks[i].mode = subtitlesEnabled ? 'showing' : 'hidden';
      }
    }

    subsBtn.textContent = subtitlesEnabled
      ? '💬 Subtitles: ON'
      : '💬 Subtitles: OFF';
  }

  function changeSubtitleTrack(trackIndex) {
    const tracks = videoSubs.textTracks;

    // ปิดทุก track ก่อน
    for (let i = 0; i < tracks.length; i++) {
      if (tracks[i].kind === 'subtitles') {
        tracks[i].mode = 'hidden';
      }
    }

    // เปิด track ที่เลือก
    if (trackIndex >= 0 && subtitlesEnabled) {
      tracks[trackIndex].mode = 'showing';
    }
  }

  // โหลด chapters
  videoSubs.addEventListener('loadedmetadata', function () {
    const tracks = videoSubs.textTracks;

    for (let i = 0; i < tracks.length; i++) {
      if (tracks[i].kind === 'chapters') {
        tracks[i].mode = 'hidden'; // โหลดแต่ไม่แสดง

        tracks[i].addEventListener('load', function () {
          displayChapters(tracks[i]);
        });

        break;
      }
    }
  });

  function displayChapters(chaptersTrack) {
    const cues = chaptersTrack.cues;

    for (let i = 0; i < cues.length; i++) {
      const cue = cues[i];
      const button = document.createElement('button');
      button.textContent = cue.text;
      button.onclick = function () {
        videoSubs.currentTime = cue.startTime;
      };
      button.className = 'chapter-button';
      chaptersList.appendChild(button);
    }
  }

  // อัปเดตปุ่ม play/pause
  videoSubs.addEventListener('play', () => {
    playSubsBtn.textContent = '⏸️ Pause';
  });

  videoSubs.addEventListener('pause', () => {
    playSubsBtn.textContent = '▶️ Play';
  });
</script>

<style>
  .custom-video-player {
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 1rem;
    max-width: 850px;
    margin: 1rem 0;
  }

  #video-with-subs {
    width: 100%;
    height: auto;
    border-radius: 4px;
  }

  .player-controls {
    margin: 1rem 0;
    display: flex;
    align-items: center;
    gap: 1rem;
  }

  .player-controls button,
  .player-controls select {
    padding: 0.5rem 1rem;
    border: 1px solid #ddd;
    border-radius: 4px;
    background: white;
    cursor: pointer;
  }

  .chapters-menu {
    margin-top: 1rem;
    padding: 1rem;
    background-color: #f9f9f9;
    border-radius: 4px;
  }

  .chapters-menu h4 {
    margin: 0 0 0.5rem 0;
  }

  .chapter-button {
    display: block;
    width: 100%;
    margin: 0.25rem 0;
    padding: 0.5rem;
    border: 1px solid #ddd;
    border-radius: 4px;
    background: white;
    cursor: pointer;
    text-align: left;
  }

  .chapter-button:hover {
    background-color: #f0f0f0;
  }
</style>
```

## 6. Best Practices และ Accessibility

### 6.1 การเลือกรูปแบบไฟล์

```html
<!-- ✅ รองรับหลาย browser -->
<video controls>
  <source src="video.mp4" type="video/mp4" />
  <!-- Safari, IE -->
  <source src="video.webm" type="video/webm" />
  <!-- Chrome, Firefox -->
  <source src="video.ogg" type="video/ogg" />
  <!-- Firefox -->
</video>

<audio controls>
  <source src="audio.mp3" type="audio/mpeg" />
  <!-- ทุก browser -->
  <source src="audio.ogg" type="audio/ogg" />
  <!-- Firefox, Chrome -->
  <source src="audio.wav" type="audio/wav" />
  <!-- backup -->
</audio>
```

### 6.2 Accessibility

```html
<!-- ✅ การใช้งานที่เป็นมิตรกับผู้พิการ -->
<video
  controls
  aria-label="วิดีโอสอน HTML5 Multimedia"
  poster="video-thumbnail.jpg"
>
  <source src="lesson.mp4" type="video/mp4" />

  <!-- Captions สำหรับผู้พิการทางการได้ยิน -->
  <track
    kind="captions"
    src="captions.vtt"
    srclang="th"
    label="คำบรรยาย"
    default
  />

  <!-- Descriptions สำหรับผู้พิการทางสายตา -->
  <track
    kind="descriptions"
    src="descriptions.vtt"
    srclang="th"
    label="คำอธิบายภาพ"
  />

  <!-- Transcript ให้ในหน้าเว็บ -->
</video>

<details>
  <summary>Transcript ของวิดีโอ</summary>
  <div class="transcript">
    <p>สวัสดีครับ ยินดีต้อนรับสู่บทเรียน HTML5 Multimedia...</p>
    <p>วันนี้เราจะมาเรียนรู้เกี่ยวกับการใช้งาน audio และ video elements...</p>
  </div>
</details>
```

### 6.3 Performance และ Loading

```html
<!-- ✅ การจัดการ loading ที่ดี -->
<video controls preload="metadata" <!-- โหลดเฉพาะข้อมูล -->
  poster="thumbnail.jpg">
  <!-- แสดงภาพก่อนโหลด -->
  <source src="large-video.mp4" type="video/mp4" />
</video>

<!-- สำหรับ autoplay (ใช้ด้วยความระมัดระวัง) -->
<video autoplay muted loop playsinline>
  <!-- muted สำหรับ mobile -->
  <source src="background-video.mp4" type="video/mp4" />
</video>
```

### 6.4 Responsive Design

```html
<!-- ✅ Video ที่ responsive -->
<div class="video-container">
  <video controls poster="poster.jpg">
    <source src="video.mp4" type="video/mp4" />
  </video>
</div>

<style>
  .video-container {
    position: relative;
    width: 100%;
    max-width: 800px;
    margin: 0 auto;
  }

  .video-container video {
    width: 100%;
    height: auto;
    display: block;
  }

  /* Aspect ratio container */
  .video-16-9 {
    position: relative;
    width: 100%;
    padding-bottom: 56.25%; /* 16:9 aspect ratio */
  }

  .video-16-9 video {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
</style>
```

---

**สรุป**: HTML5 multimedia elements ช่วยให้เราสามารถฝังสื่อต่างๆ ได้อย่างมีประสิทธิภาพ โดยต้องคำนึงถึง browser compatibility, accessibility, และ performance เสมอ
