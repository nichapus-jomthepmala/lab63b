## การทดลองที่6 เรื่อง การเขียนโปรแกรมสร้างไวไฟแอคเซสพอยต์ (Wifi AP)

## วัตถุประสงค์
1.  เพื่อเข้าใจการเขียนโปรแกรมที่จะสร้าง Wifi Access Point ขึ้นมาเอง
2.  เพื่อสามารถนำโปรแกรมไปใช้ในการเชื่อม wifi ของตัวเองกับอุปกรณ์อื่น
 
## อุปกรณ์ที่ใช้
1. microcontroller ESP-01 ประกอบด้วย CPU
2. อุปกรณ์เชื่อมต่อ USB เข้าไปยัง serial

## ศึกษาข้อมูลเบื้องต้น
https://www.youtube.com/watch?v=T26DVHePlTs

## วิธีการทำการทดลอง
1. เขียนโปรแกรมบน microcontroller โดยทำการเสียบ microcontroller เข้าทาง serial port ขอบ USB
2. ดูตัวอย่างโปรแกรมที่folder pattani 
  
  • พิมพ์ cd pattani เพื่อไปยังโฟลเดอร์
  
  • แสดงโฟลเดอร์ ซึ่งจะมีโปรแกรมตัวอย่าง 9 โปรแกรม
  
  • ไปที่ตัวอย่างที่ 6
  
    • พิมพ์ cd 06_Wifi-AP-Web-Server
3. ดู source code program พิมพ์ vi src/main.cpp
  
  • โดยโค้ดดังกล่าว ประกอบด้วยข้อมูลดังนี้
  
      กำหนด ชื่อ และ ตั้งpassword 
      ![image](https://user-images.githubusercontent.com/80880074/112326409-13a75700-8ce7-11eb-83a9-9a729ad495c7.jpeg)
      กำหนด IPAdress, gateway, subnet
      ![image](https://user-images.githubusercontent.com/80880074/112326487-26219080-8ce7-11eb-9f5f-e1d06de13d74.jpeg)
      เตรียม web server
      ![image](https://user-images.githubusercontent.com/80880074/112326606-3cc7e780-8ce7-11eb-9598-581dfd744091.jpeg)
      รันคำสั่ง softAP แล้วกำหนด ssiad กับ password
      ![image](https://user-images.githubusercontent.com/80880074/112326686-4cdfc700-8ce7-11eb-9c41-5544a5b7a3dc.jpeg)
    
4. อัพโหลดโปรแกรม 06_Wifi-AP-Web-Server เข้าไปยัง microcontroller โดยใช้คำสั่ง upload
  
  • พิมพ์ pio run -t upload
  
  • ทำการเสียบ microcontroller เข้าทาง serial port ของ USB
  
  • ในขณะที่ program กำลังรันข้อมูล เพื่อให้ microcontroller รันโปรแกรมใหม่เข้าไป กดปุ่มสีดำเพื่อให้เกิดการโหลด และกดปุ่มสีแดงเพื่อให้เกิดการรีเซ็ท
    
  • ตรวจสอบว่า wifi ที่สร้างขึ้นนั้นแสดงผลหรือยัง โดยพิมพ์ pio device monitor 
  ![image](https://user-images.githubusercontent.com/80880074/112326787-697bff00-8ce7-11eb-8551-e0c159910449.jpeg)
  
  • ใช้โทรศัพท์โทรศัพท์มือถือค้นหา wifi

## การบันทึกผลการทดลอง
• การใช้คำสั่ง pio device monitor เพื่อดูผลลัพธ์ของการรันโปรแกรมในไมโครคอนโทรเลอร์ ได้แสดงที่อยู่ไอพีขึ้นมา และเมื่อทำการคัดลอกไปที่บราวเซอร์ ผลลัพธ์ที่แสดงจะขึ้นว่า Hello 1 โดย cnt เปลี่ยนตัวแปรไปเรื่อยๆ

## อภิปรายผลการทดลอง
  • จากการทดลองดังกล่าว โปรแกรม 06_Wifi-AP-Web-Server ทำให้เราสามารถสร้าง Wifi Access Point ขึ้นมาเองได้ และตรวจสอบพบว่ามีอยู่จริง ดังภาพ
![image](https://user-images.githubusercontent.com/80880074/112326864-7bf63880-8ce7-11eb-837b-793ce2dd4329.jpeg)
## คำถามหลังการทดลอง 
 คำถาม : คำสั่ง pio device monitor มีหน้าที่อะไร  ?
 
 คำตอบ : ตรวจสอบว่า wifi ที่สร้างขึ้นนั้นแสดงผลหรือยัง
 



