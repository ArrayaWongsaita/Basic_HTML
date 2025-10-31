# Lab Phase 6: HTML Forms
## 🎯 เติม HTML Form Tags ให้ถูกต้องตามโครงสร้าง

### 📚 **เนื้อหาที่ใช้ใน Lab นี้:**
- `<form>` - ฟอร์มหลักและ attributes (action, method)
- `<input>` - ช่องกรอกข้อมูลประเภทต่างๆ
- `<textarea>` - ช่องกรอกข้อความหลายบรรทัด
- `<select>`, `<option>` - dropdown list
- `<button>` - ปุ่มต่างๆ
- `<label>` - ป้ายชื่อของ input
- `<fieldset>`, `<legend>` - การจัดกลุ่มฟิลด์
- Input types: text, email, password, tel, number, date, checkbox, radio
- Attributes: required, placeholder, name, id, value
- Client-side validation

---

## 📝 **Lab 1: ฟอร์มสมัครสมาชิก**

### **คำใบ้:**
1. **ฟอร์ม** - container หลักพร้อม action และ method
2. **กลุ่มฟิลด์** ข้อมูลส่วนตัว
3. **ป้ายชื่อ** และ **ช่องกรอก** text
4. **ช่องกรอก email** พร้อม validation
5. **ช่องกรอก password** 
6. **ช่องกรอกเบอร์โทร** 
7. **ช่องเลือกวันเกิด** 
8. **ตัวเลือกเพศ** แบบ radio
9. **checkbox** ยอมรับเงื่อนไข
10. **ปุ่ม submit** และ **reset**

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>สมัครสมาชิก</title>
</head>
<body>
    <หัวข้อหลัก>สมัครสมาชิกเว็บไซต์</หัวข้อหลัก>
    
    <ฟอร์ม action="/register" method="post">
        <กลุ่มฟิลด์>
            <คำอธิบายกลุ่ม>ข้อมูลส่วนตัว</คำอธิบายกลุ่ม>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="firstname">ชื่อ:</ป้ายชื่อ>
                <ช่องกรอกข้อความ type="text" id="firstname" name="firstname" required>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="lastname">นามสกุล:</ป้ายชื่อ>
                <ช่องกรอกข้อความ type="text" id="lastname" name="lastname" required>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="email">อีเมล:</ป้ายชื่อ>
                <ช่องกรอกอีเมล type="email" id="email" name="email" placeholder="example@email.com" required>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="password">รหัสผ่าน:</ป้ายชื่อ>
                <ช่องกรอกรหัสผ่าน type="password" id="password" name="password" minlength="8" required>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="confirm-password">ยืนยันรหัสผ่าน:</ป้ายชื่อ>
                <ช่องกรอกรหัสผ่าน type="password" id="confirm-password" name="confirm-password" minlength="8" required>
            </ย่อหน้า>
        </กลุ่มฟิลด์>
        
        <กลุ่มฟิลด์>
            <คำอธิบายกลุ่ม>ข้อมูลเพิ่มเติม</คำอธิบายกลุ่ม>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="birthdate">วันเกิด:</ป้ายชื่อ>
                <ช่องเลือกวันที่ type="date" id="birthdate" name="birthdate" required>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="phone">เบอร์โทรศัพท์:</ป้ายชื่อ>
                <ช่องกรอกเบอร์โทร type="tel" id="phone" name="phone" placeholder="0812345678" pattern="[0-9]{10}">
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ>เพศ:</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                <ช่องเลือกแบบวงกลม type="radio" id="male" name="gender" value="male">
                <ป้ายชื่อ for="male">ชาย</ป้ายชื่อ>
                
                <ช่องเลือกแบบวงกลม type="radio" id="female" name="gender" value="female">
                <ป้ายชื่อ for="female">หญิง</ป้ายชื่อ>
                
                <ช่องเลือกแบบวงกลม type="radio" id="other" name="gender" value="other">
                <ป้ายชื่อ for="other">ไม่ระบุ</ป้ายชื่อ>
            </ย่อหน้า>
        </กลุ่มฟิลด์>
        
        <ย่อหน้า>
            <ช่องเลือกแบบกล่อง type="checkbox" id="terms" name="terms" required>
            <ป้ายชื่อ for="terms">ฉันยอมรับ <ลิงก์ href="terms.html">เงื่อนไขการใช้งาน</ลิงก์></ป้ายชื่อ>
        </ย่อหน้า>
        
        <ย่อหน้า>
            <ช่องเลือกแบบกล่อง type="checkbox" id="newsletter" name="newsletter">
            <ป้ายชื่อ for="newsletter">รับข่าวสารและโปรโมชั่น</ป้ายชื่อ>
        </ย่อหน้า>
        
        <ย่อหน้า>
            <ปุ่มส่งข้อมูล type="submit">สมัครสมาชิก</ปุ่มส่งข้อมูล>
            <ปุ่มรีเซ็ต type="reset">ล้างข้อมูล</ปุ่มรีเซ็ต>
        </ย่อหน้า>
    </ฟอร์ม>
</body>
</html>
```

---

## 💼 **Lab 2: ฟอร์มสมัครงาน**

### **คำใบ้:**
1. **ฟอร์ม** พร้อม attributes
2. **กลุ่มฟิลด์** ข้อมูลส่วนตัว
3. **ช่องกรอก** ข้อมูลต่างๆ
4. **dropdown** เลือกตำแหน่งงาน
5. **textarea** สำหรับรายละเอียด
6. **ช่องกรอกเงินเดือน** แบบ number
7. **ช่องอัปโหลดไฟล์** resume
8. **checkbox** ทักษะต่างๆ
9. **radio** ระดับการศึกษา

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>สมัครงาน - TechCorp</title>
</head>
<body>
    <หัวข้อหลัก>ใบสมัครงาน - TechCorp Co., Ltd.</หัวข้อหลัก>
    
    <ฟอร์ม action="/submit-application" method="post" enctype="multipart/form-data">
        <กลุ่มฟิลด์>
            <คำอธิบายกลุ่ม>ข้อมูลส่วนตัว</คำอธิบายกลุ่ม>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="fullname">ชื่อ-นามสกุล:</ป้ายชื่อ>
                <ช่องกรอกข้อความ type="text" id="fullname" name="fullname" required>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="email">อีเมล:</ป้ายชื่อ>
                <ช่องกรอกอีเมล type="email" id="email" name="email" required>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="phone">เบอร์โทรศัพท์:</ป้ายชื่อ>
                <ช่องกรอกเบอร์โทร type="tel" id="phone" name="phone" placeholder="0812345678" required>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="age">อายุ:</ป้ายชื่อ>
                <ช่องกรอกตัวเลข type="number" id="age" name="age" min="18" max="60" required>
            </ย่อหน้า>
        </กลุ่มฟิลด์>
        
        <กลุ่มฟิลด์>
            <คำอธิบายกลุ่ม>ข้อมูลการสมัคร</คำอธิบายกลุ่ม>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="position">ตำแหน่งที่สมัคร:</ป้ายชื่อ>
                <รายการแบบเลือก id="position" name="position" required>
                    <ตัวเลือก value="">-- เลือกตำแหน่ง --</ตัวเลือก>
                    <ตัวเลือก value="frontend">Frontend Developer</ตัวเลือก>
                    <ตัวเลือก value="backend">Backend Developer</ตัวเลือก>
                    <ตัวเลือก value="fullstack">Full Stack Developer</ตัวเลือก>
                    <ตัวเลือก value="ui-ux">UI/UX Designer</ตัวเลือก>
                    <ตัวเลือก value="devops">DevOps Engineer</ตัวเลือก>
                </รายการแบบเลือก>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="experience">ประสบการณ์ (ปี):</ป้ายชื่อ>
                <ช่องกรอกตัวเลข type="number" id="experience" name="experience" min="0" max="50" step="0.5">
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="salary">เงินเดือนที่ต้องการ (บาท):</ป้ายชื่อ>
                <ช่องกรอกตัวเลข type="number" id="salary" name="salary" min="15000" step="1000">
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="start-date">วันที่สามารถเริ่มงาน:</ป้ายชื่อ>
                <ช่องเลือกวันที่ type="date" id="start-date" name="start-date">
            </ย่อหน้า>
        </กลุ่มฟิลด์>
        
        <กลุ่มฟิลด์>
            <คำอธิบายกลุ่ม>การศึกษา</คำอธิบายกลุ่ม>
            
            <ย่อหน้า>
                <ป้ายชื่อ>ระดับการศึกษาสูงสุด:</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                
                <ช่องเลือกแบบวงกลม type="radio" id="edu-high" name="education" value="high-school">
                <ป้ายชื่อ for="edu-high">มัธยมปลาย/ปวช.</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                
                <ช่องเลือกแบบวงกลม type="radio" id="edu-diploma" name="education" value="diploma">
                <ป้ายชื่อ for="edu-diploma">ปวส./อนุปริญญา</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                
                <ช่องเลือกแบบวงกลม type="radio" id="edu-bachelor" name="education" value="bachelor">
                <ป้ายชื่อ for="edu-bachelor">ปริญญาตรี</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                
                <ช่องเลือกแบบวงกลม type="radio" id="edu-master" name="education" value="master">
                <ป้ายชื่อ for="edu-master">ปริญญาโท</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                
                <ช่องเลือกแบบวงกลม type="radio" id="edu-doctor" name="education" value="doctor">
                <ป้ายชื่อ for="edu-doctor">ปริญญาเอก</ป้ายชื่อ>
            </ย่อหน้า>
        </กลุ่มฟิลด์>
        
        <กลุ่มฟิลด์>
            <คำอธิบายกลุ่ม>ทักษะความสามารถ</คำอธิบายกลุ่ม>
            
            <ย่อหน้า>
                <ป้ายชื่อ>ภาษาโปรแกรมที่ถนัด:</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                
                <ช่องเลือกแบบกล่อง type="checkbox" id="skill-js" name="skills" value="javascript">
                <ป้ายชื่อ for="skill-js">JavaScript</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                
                <ช่องเลือกแบบกล่อง type="checkbox" id="skill-python" name="skills" value="python">
                <ป้ายชื่อ for="skill-python">Python</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                
                <ช่องเลือกแบบกล่อง type="checkbox" id="skill-java" name="skills" value="java">
                <ป้ายชื่อ for="skill-java">Java</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                
                <ช่องเลือกแบบกล่อง type="checkbox" id="skill-php" name="skills" value="php">
                <ป้ายชื่อ for="skill-php">PHP</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                
                <ช่องเลือกแบบกล่อง type="checkbox" id="skill-csharp" name="skills" value="csharp">
                <ป้ายชื่อ for="skill-csharp">C#</ป้ายชื่อ>
            </ย่อหน้า>
        </กลุ่มฟิลด์>
        
        <ย่อหน้า>
            <ป้ายชื่อ for="about">แนะนำตัวเอง:</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
            <ช่องกรอกข้อความยาว id="about" name="about" rows="5" cols="50" placeholder="บอกเล่าเกี่ยวกับตัวคุณ..."></ช่องกรอกข้อความยาว>
        </ย่อหน้า>
        
        <ย่อหน้า>
            <ป้ายชื่อ for="resume">อัปโหลดไฟล์เรซูเม่ (PDF):</ป้ายชื่อ>
            <ช่องอัปโหลดไฟล์ type="file" id="resume" name="resume" accept=".pdf">
        </ย่อหน้า>
        
        <ย่อหน้า>
            <ปุ่มส่งข้อมูล type="submit">ส่งใบสมัคร</ปุ่มส่งข้อมูล>
            <ปุ่มรีเซ็ต type="reset">ล้างข้อมูล</ปุ่มรีเซ็ต>
        </ย่อหน้า>
    </ฟอร์ม>
</body>
</html>
```

---

## 🏨 **Lab 3: ฟอร์มจองโรงแรม**

### **คำใบ้:**
1. **ฟอร์ม** จองห้องพัก
2. **ช่องกรอกวันที่** เช็คอิน-เช็คเอาท์
3. **dropdown** ประเภทห้อง
4. **ช่องกรอกจำนวน** ผู้เข้าพัก
5. **checkbox** บริการเพิ่มเติม
6. **textarea** คำขอพิเศษ
7. **radio** วิธีชำระเงิน

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>จองห้องพัก - Grand Hotel</title>
</head>
<body>
    <หัวข้อหลัก>จองห้องพัก Grand Hotel</หัวข้อหลัก>
    
    <ฟอร์ม action="/booking" method="post">
        <กลุ่มฟิลด์>
            <คำอธิบายกลุ่ม>ข้อมูลการจอง</คำอธิบายกลุ่ม>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="checkin">วันเช็คอิน:</ป้ายชื่อ>
                <ช่องเลือกวันที่ type="date" id="checkin" name="checkin" required>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="checkout">วันเช็คเอาท์:</ป้ายชื่อ>
                <ช่องเลือกวันที่ type="date" id="checkout" name="checkout" required>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="room-type">ประเภทห้อง:</ป้ายชื่อ>
                <รายการแบบเลือก id="room-type" name="room-type" required>
                    <ตัวเลือก value="">-- เลือกประเภทห้อง --</ตัวเลือก>
                    <ตัวเลือก value="standard">Standard Room (1,500 บาท/คืน)</ตัวเลือก>
                    <ตัวเลือก value="deluxe">Deluxe Room (2,500 บาท/คืน)</ตัวเลือก>
                    <ตัวเลือก value="suite">Suite Room (4,000 บาท/คืน)</ตัวเลือก>
                    <ตัวเลือก value="penthouse">Penthouse (8,000 บาท/คืน)</ตัวเลือก>
                </รายการแบบเลือก>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="adults">จำนวนผู้ใหญ่:</ป้ายชื่อ>
                <ช่องกรอกตัวเลข type="number" id="adults" name="adults" min="1" max="4" value="1" required>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="children">จำนวนเด็ก:</ป้ายชื่อ>
                <ช่องกรอกตัวเลข type="number" id="children" name="children" min="0" max="3" value="0">
            </ย่อหน้า>
        </กลุ่มฟิลด์>
        
        <กลุ่มฟิลด์>
            <คำอธิบายกลุ่ม>ข้อมูลผู้จอง</คำอธิบายกลุ่ม>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="guest-name">ชื่อ-นามสกุล:</ป้ายชื่อ>
                <ช่องกรอกข้อความ type="text" id="guest-name" name="guest-name" required>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="email">อีเมล:</ป้ายชื่อ>
                <ช่องกรอกอีเมล type="email" id="email" name="email" required>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="phone">เบอร์โทรศัพท์:</ป้ายชื่อ>
                <ช่องกรอกเบอร์โทร type="tel" id="phone" name="phone" required>
            </ย่อหน้า>
        </กลุ่มฟิลด์>
        
        <กลุ่มฟิลด์>
            <คำอธิบายกลุ่ม>บริการเพิ่มเติม</คำอธิบายกลุ่ม>
            
            <ย่อหน้า>
                <ช่องเลือกแบบกล่อง type="checkbox" id="breakfast" name="services" value="breakfast">
                <ป้ายชื่อ for="breakfast">อาหารเช้า (+300 บาท/คน/วัน)</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                
                <ช่องเลือกแบบกล่อง type="checkbox" id="airport" name="services" value="airport">
                <ป้ายชื่อ for="airport">รับ-ส่ง สนามบิน (+500 บาท)</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                
                <ช่องเลือกแบบกล่อง type="checkbox" id="spa" name="services" value="spa">
                <ป้ายชื่อ for="spa">สปาและนวด (+1,200 บาท)</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                
                <ช่องเลือกแบบกล่อง type="checkbox" id="parking" name="services" value="parking">
                <ป้ายชื่อ for="parking">ที่จอดรถ (ฟรี)</ป้ายชื่อ>
            </ย่อหน้า>
        </กลุ่มฟิลด์>
        
        <กลุ่มฟิลด์>
            <คำอธิบายกลุ่ม>การชำระเงิน</คำอธิบายกลุ่ม>
            
            <ย่อหน้า>
                <ป้ายชื่อ>วิธีชำระเงิน:</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                
                <ช่องเลือกแบบวงกลม type="radio" id="pay-now" name="payment" value="pay-now" checked>
                <ป้ายชื่อ for="pay-now">ชำระเต็มจำนวนตอนจอง</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                
                <ช่องเลือกแบบวงกลม type="radio" id="pay-deposit" name="payment" value="deposit">
                <ป้ายชื่อ for="pay-deposit">มัดจำ 30%</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                
                <ช่องเลือกแบบวงกลม type="radio" id="pay-hotel" name="payment" value="hotel">
                <ป้ายชื่อ for="pay-hotel">ชำระเงินที่โรงแรม</ป้ายชื่อ>
            </ย่อหน้า>
        </กลุ่มฟิลด์>
        
        <ย่อหน้า>
            <ป้ายชื่อ for="requests">คำขอพิเศษ:</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
            <ช่องกรอกข้อความยาว id="requests" name="requests" rows="4" cols="50" placeholder="เช่น ห้องชั้นสูง, วิวทะเล, เตียงเสริม..."></ช่องกรอกข้อความยาว>
        </ย่อหน้า>
        
        <ย่อหน้า>
            <ปุ่มส่งข้อมูล type="submit">ยืนยันการจอง</ปุ่มส่งข้อมูล>
            <ปุ่มรีเซ็ต type="reset">ล้างข้อมูล</ปุ่มรีเซ็ต>
        </ย่อหน้า>
    </ฟอร์ม>
</body>
</html>
```

---

## 📞 **Lab 4: ฟอร์มติดต่อสอบถาม**

### **คำใบ้:**
1. **ฟอร์ม** ติดต่อเรา
2. **ช่องกรอก** ข้อมูลติดต่อ
3. **dropdown** หัวข้อเรื่อง
4. **radio** ความเร่งด่วน
5. **textarea** รายละเอียด
6. **ช่องอัปโหลด** ไฟล์แนบ
7. **ช่อง url** สำหรับเว็บไซต์

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>ติดต่อเรา - CustomerSupport</title>
</head>
<body>
    <หัวข้อหลัก>ติดต่อฝ่ายบริการลูกค้า</หัวข้อหลัก>
    
    <ฟอร์ม action="/contact" method="post" enctype="multipart/form-data">
        <กลุ่มฟิลด์>
            <คำอธิบายกลุ่ม>ข้อมูลผู้ติดต่อ</คำอธิบายกลุ่ม>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="contact-name">ชื่อ-นามสกุล:</ป้ายชื่อ>
                <ช่องกรอกข้อความ type="text" id="contact-name" name="contact-name" required>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="email">อีเมล:</ป้ายชื่อ>
                <ช่องกรอกอีเมล type="email" id="email" name="email" required>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="phone">เบอร์โทรศัพท์:</ป้ายชื่อ>
                <ช่องกรอกเบอร์โทร type="tel" id="phone" name="phone">
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="company">บริษัท/องค์กร:</ป้ายชื่อ>
                <ช่องกรอกข้อความ type="text" id="company" name="company">
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="website">เว็บไซต์:</ป้ายชื่อ>
                <ช่องกรอก URL type="url" id="website" name="website" placeholder="https://example.com">
            </ย่อหน้า>
        </กลุ่มฟิลด์>
        
        <กลุ่มฟิลด์>
            <คำอธิบายกลุ่ม>รายละเอียดเรื่อง</คำอธิบายกลุ่ม>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="subject">หัวข้อเรื่อง:</ป้ายชื่อ>
                <รายการแบบเลือก id="subject" name="subject" required>
                    <ตัวเลือก value="">-- เลือกหัวข้อ --</ตัวเลือก>
                    <ตัวเลือก value="general">สอบถามทั่วไป</ตัวเลือก>
                    <ตัวเลือก value="sales">สอบถามข้อมูลสินค้า/บริการ</ตัวเลือก>
                    <ตัวเลือก value="support">ขอความช่วยเหลือทางเทคนิค</ตัวเลือก>
                    <ตัวเลือก value="complaint">ร้องเรียน</ตัวเลือก>
                    <ตัวเลือก value="suggestion">ข้อเสนอแนะ</ตัวเลือก>
                </รายการแบบเลือก>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ>ความเร่งด่วน:</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                
                <ช่องเลือกแบบวงกลม type="radio" id="urgent-low" name="urgency" value="low" checked>
                <ป้ายชื่อ for="urgent-low">ไม่เร่งด่วน</ป้ายชื่อ>
                
                <ช่องเลือกแบบวงกลม type="radio" id="urgent-normal" name="urgency" value="normal">
                <ป้ายชื่อ for="urgent-normal">ปานกลาง</ป้ายชื่อ>
                
                <ช่องเลือกแบบวงกลม type="radio" id="urgent-high" name="urgency" value="high">
                <ป้ายชื่อ for="urgent-high">เร่งด่วน</ป้ายชื่อ>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="message">รายละเอียด:</ป้ายชื่อ><ขึ้นบรรทัดใหม่>
                <ช่องกรอกข้อความยาว id="message" name="message" rows="6" cols="50" required placeholder="กรุณาระบุรายละเอียดให้ชัดเจน..."></ช่องกรอกข้อความยาว>
            </ย่อหน้า>
            
            <ย่อหน้า>
                <ป้ายชื่อ for="attachment">แนบไฟล์ (ถ้ามี):</ป้ายชื่อ>
                <ช่องอัปโหลดไฟล์ type="file" id="attachment" name="attachment" accept=".pdf,.doc,.docx,.jpg,.png">
            </ย่อหน้า>
        </กลุ่มฟิลด์>
        
        <ย่อหน้า>
            <ช่องเลือกแบบกล่อง type="checkbox" id="copy" name="copy">
            <ป้ายชื่อ for="copy">ส่งสำเนาข้อความไปยังอีเมลของฉัน</ป้ายชื่อ>
        </ย่อหน้า>
        
        <ย่อหน้า>
            <ปุ่มส่งข้อมูล type="submit">ส่งข้อความ</ปุ่มส่งข้อมูล>
            <ปุ่มรีเซ็ต type="reset">ล้างข้อมูล</ปุ่มรีเซ็ต>
        </ย่อหน้า>
    </ฟอร์ม>
    
    <เส้นแบ่ง>
    
    <ย่อหน้า><ข้อความเล็ก>หมายเหตุ: เราจะตอบกลับภายใน 24 ชั่วโมง</ข้อความเล็ก></ย่อหน้า>
</body>
</html>
```

---

## 🎯 **เฉลยและคำแนะนำ**

### **การตรวจสอบผลงาน:**
1. ✅ ใช้ `<form>` พร้อม action และ method
2. ✅ ใช้ `<label>` และ for attribute ครบถ้วน
3. ✅ ใช้ input types ถูกต้องตามประเภทข้อมูล
4. ✅ ใส่ required attribute ในฟิลด์ที่จำเป็น
5. ✅ ใช้ `<fieldset>` และ `<legend>` จัดกลุ่ม
6. ✅ Radio buttons ใช้ name เดียวกัน
7. ✅ Checkboxes สามารถเลือกได้หลายตัว

### **เกณฑ์การให้คะแนน:**
- ✅ โครงสร้างฟอร์มถูกต้อง (25%)
- ✅ ใช้ input types เหมาะสม (25%)
- ✅ Label และ accessibility (20%)
- ✅ Validation attributes (15%)
- ✅ Fieldset และการจัดกลุ่ม (15%)

### **ข้อผิดพลาดที่พบบ่อย:**
- ❌ ไม่ใส่ `for` ใน `<label>` หรือ `id` ใน input
- ❌ ใช้ `type="text"` แทน email, tel, date
- ❌ Radio buttons ใช้ name ต่างกัน
- ❌ ลืมใส่ `name` attribute
- ❌ ไม่ใส่ `required` ในฟิลด์สำคัญ
- ❌ ไม่ใช้ `<fieldset>` จัดกลุ่มฟิลด์

---

## 📋 **Input Types สำคัญ**

### **Text Inputs:**
```html
<input type="text">      <!-- ข้อความทั่วไป -->
<input type="email">     <!-- อีเมล (validation) -->
<input type="password">  <!-- รหัสผ่าน (ซ่อนตัวอักษร) -->
<input type="tel">       <!-- เบอร์โทร -->
<input type="url">       <!-- URL -->
<input type="search">    <!-- ช่องค้นหา -->
```

### **Number & Date:**
```html
<input type="number" min="1" max="100" step="1">
<input type="date">
<input type="time">
<input type="datetime-local">
<input type="month">
<input type="week">
```

### **Choice Inputs:**
```html
<input type="checkbox">  <!-- เลือกได้หลายตัว -->
<input type="radio">     <!-- เลือกได้ตัวเดียว -->
```

### **Other Types:**
```html
<input type="file">      <!-- อัปโหลดไฟล์ -->
<input type="color">     <!-- เลือกสี -->
<input type="range">     <!-- slider -->
<input type="hidden">    <!-- ซ่อนค่า -->
```

---

## 🏆 **Best Practices**

### **1. ใช้ Label เสมอ:**
```html
<!-- ✅ ถูกต้อง -->
<label for="email">อีเมล:</label>
<input type="email" id="email" name="email">

<!-- ✅ หรือ -->
<label>
    อีเมล:
    <input type="email" name="email">
</label>
```

### **2. ใช้ Input Type ที่เหมาะสม:**
```html
<!-- ✅ ถูกต้อง -->
<input type="email">
<input type="tel">
<input type="date">

<!-- ❌ ผิด -->
<input type="text"> <!-- สำหรับทุกอย่าง -->
```

### **3. ใส่ Required Validation:**
```html
<input type="text" required>
<input type="email" required>
<select required>
    <option value="">-- เลือก --</option>
</select>
```

### **4. ใช้ Placeholder อย่างเหมาะสม:**
```html
<input type="email" placeholder="example@email.com">
<input type="tel" placeholder="0812345678">
<textarea placeholder="พิมพ์ข้อความที่นี่..."></textarea>
```

### **5. จัดกลุ่มด้วย Fieldset:**
```html
<fieldset>
    <legend>ข้อมูลส่วนตัว</legend>
    <!-- inputs -->
</fieldset>
```

---

## 🔍 **Validation Attributes**

### **Required:**
```html
<input type="text" required>
```

### **Pattern:**
```html
<input type="tel" pattern="[0-9]{10}">
<input type="text" pattern="[A-Za-z]+">
```

### **Min/Max:**
```html
<input type="number" min="1" max="100">
<input type="date" min="2025-01-01" max="2025-12-31">
```

### **Minlength/Maxlength:**
```html
<input type="password" minlength="8" maxlength="20">
<textarea maxlength="500"></textarea>
```

### **Step:**
```html
<input type="number" step="0.5">
<input type="number" step="1000">
```

---

## 💡 **ความรู้เพิ่มเติม**

### **Form Attributes:**
```html
<form action="/submit" method="post" enctype="multipart/form-data">
    <!-- method: get, post -->
    <!-- enctype: สำหรับอัปโหลดไฟล์ -->
</form>
```

### **Button Types:**
```html
<button type="submit">ส่งข้อมูล</button>
<button type="reset">ล้างข้อมูล</button>
<button type="button">ปุ่มทั่วไป</button>
```

### **Accessibility Tips:**
- ใช้ `<label>` เสมอ
- ใส่ `for` attribute
- ใช้ `<fieldset>` และ `<legend>`
- ใส่ `aria-*` attributes เมื่อจำเป็น

### **Security Tips:**
- ใช้ `method="post"` สำหรับข้อมูลสำคัญ
- Validate ทั้ง client และ server side
- ใช้ HTTPS สำหรับฟอร์มที่มีข้อมูลส่วนตัว

---

**สำเร็จแล้ว!** 🎉 ตอนนี้คุณเข้าใจการสร้างฟอร์มใน HTML แล้ว อย่าลืมว่า form accessibility และ validation เป็นสิ่งสำคัญมากครับ!
