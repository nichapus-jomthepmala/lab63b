## การทดลองที่2 เรื่อง การเขียนโปรแกรมการค้นหา wifi

## วัตถุประสงค์
1. เพื่อศึกษาการเขียนโปรแกรมค้นหา wifi
2. เพื่อศึกษาการรันโปรแกรมบน microcontroller ในการค้นหา wifi 
 
## อุปกรณ์ที่ใช้
1. microcontroller ESP-01 ที่มี wifi ในตัวเอง , CPU , เสาอากาศสำหรับ wifi
2. อุปกรณ์เชื่อมต่อ USB เข้าไปยัง serial
3. microcontroller ESP-01 ที่มี wifi ในตัวเอง

## ศึกษาข้อมูลเบื้องต้น
https://youtu.be/yBjab0UNuB8

## วิธีการทำการทดลอง
1. เขียนโปรแกรมบน microcontroller โดยทำการเสียบ microcontroller เข้าทาง serial port ขอบ USB
2. ดูตัวอย่างโปรแกรมที่folder pattani 
  
  • พิมพ์ cd pattani เพื่อไปยังโฟลเดอร์
 
  • แสดงโฟลเดอร์ ซึ่งจะมีโปรแกรมตัวอย่าง 9 โปรแกรม
  
  • ไปที่ตัวอย่างที่ 2
  
    • พิมพ์ cd 02_Scan-Wifi
3. ดู source code progam
  
  • พิมพ์ vi src/main.cpp
4. อัพโหลดโปรแกรม 02_Scan-Wifi เข้าไปยัง microcontroller โดยใช้คำสั่ง upload
  
  • พิมพ์ pio run -t upload
  ![image](https://user-images.githubusercontent.com/80880074/112323357-4bf96600-8ce4-11eb-93c9-95160f5ee132.jpeg)
  
  • ในขณะที่ program กำลังรันข้อมูล เพื่อให้ microcontroller รันโปรแกรมใหม่เข้าไป กดปุ่มสีดำเพื่อให้เกิดการโหลด และกดปุ่มสีแดงเพื่อให้เกิดการรีเซ็ท
  ![image](https://user-images.githubusercontent.com/80880074/112323497-6af7f800-8ce4-11eb-9f96-75fe3e6b4b47.jpeg)

  • อัพโหลดเข้าตัว microcontroller เสร็จสิ้น
  
  • สังเกตผลลัพธ์ที่แสดงผ่านคอมพิวเตอร์ พิมพ์ pio device monitor 
  ![image](https://user-images.githubusercontent.com/80880074/112323660-94b11f00-8ce4-11eb-8258-5673bf28299a.jpeg)

## การบันทึกผลการทดลอง
  • หลังการที่หน้าจอแสดงผลลัพธ์ การวนลูปจะเริ่มต้นขึ้น และเริ่มทำการค้นหา wifi ภายในบริเวณและแสดงผลจากการค้นหาดังภาพ
  ![image](https://user-images.githubusercontent.com/80880074/112323742-a5619500-8ce4-11eb-979b-8191da58c2f6.jpeg)
  
## อภิปรายผลการทดลอง
  • pio run -t upload ใช้อัพโหลดโปรแกรม 02_Scan-Wifi เข้าไปยัง microcontroller โดยคำสั่ง pio device monitor ใช้สังเกตผลลัพธ์ที่แสดงผ่านคอมพิวเตอร์ ทำให้สามารถสังเกตชื่อและจำนวนของ wifi ที่เราพบ

## คำถามหลังการทดลอง
  คำถาม : คำสั่ง pio device monitor มีหน้าที่อะไร ?
  
  คำตอบ : สังเกตผลลัพธ์ที่แสดงผ่านคอมพิวเตอร์

