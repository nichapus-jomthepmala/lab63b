## การทดลองที่5 เรื่อง การเขียนโปรแกรมเชื่อมต่อwifiและเว็บเซอร์เวอร์

## วัตถุประสงค์
1. เพื่อศึกษาการเขียนโปรแกรมเชื่อต่อ wifi และ web server
 
## อุปกรณ์ที่ใช้
1. microcontroller ESP-01 ประกอบด้วย CPU
2. อุปกรณ์เชื่อมต่อ USB เข้าไปยัง serial
3. wifi ที่ต้องการเชื่อมต่อกับตัว microcontroller

## ศึกษาข้อมูลเบื้องต้น
https://www.youtube.com/watch?v=VX-QNQcO-b4

## วิธีการทำการทดลอง
1. เขียนโปรแกรมบน microcontroller โดยทำการเสียบ microcontroller เข้าทาง serial port ขอบ USB
2. ดูตัวอย่างโปรแกรมที่folder pattani 
  
  • พิมพ์ cd pattani เพื่อไปยังโฟลเดอร์
  
  • แสดงโฟลเดอร์ ซึ่งจะมีโปรแกรมตัวอย่าง 9 โปรแกรม
  
  • ไปที่ตัวอย่างที่ 5
  
    • พิมพ์ cd 05_Wifi-Web-Server
3. ดู source code program พิมพ์ vi src/main.cpp โปรแกรมนี้เป็นการเชื่อมต่อ wifi จึงต้องใส่ชื่อ wifi และ password โดยจะแสดงเป็นสองส่วน
  
  • ส่วน set up เป็นการเชื่อมต่อ wifi ที่ใส่ชื่อตอนแรก
  
      • set up webserver แสดงผลเป็น Hello cnt และ cnt++ หมายถึง การนับเพิ่มเรื่อยๆ
  
  • ส่วน loop 
  
      • #include <ESP8266WiFi.h>
       //#include <WiFiClient.h>
      #include <ESP8266WebServer.h>

    const char* ssid = "HI_BMFWIFI_2.4G";
    const char* password = "0819110933";

    ESP8266WebServer server(80);

    int cnt = 0;

    void setup(void){
	  Serial.begin(115200);

	  WiFi.mode(WIFI_STA);
	  WiFi.begin(ssid, password);
	  while (WiFi.status() != WL_CONNECTED) {
		delay(500);
		Serial.print(".");
	  }
  	Serial.print("\n\nIP address: ");
	  Serial.println(WiFi.localIP());

	  server.onNotFound([]() {
		server.send(404, "text/plain", "Path Not Found");
	  });

	  server.on("/", []() {
		cnt++;
		String msg = "Hello cnt: ";
		msg += cnt;
		server.send(200, "text/plain", msg);
	  });

	  server.begin();
	  Serial.println("HTTP server started");
    }

    void loop(void){
    server.handleClient();
    }
4. อัพโหลดโปรแกรม 05_Wifi-Web-Server เข้าไปยัง microcontroller โดยใช้คำสั่ง upload
  
  • พิมพ์ pio run -t upload
  
  • ทำการเสียบ microcontroller เข้าทาง serial port ของ USB
  
  • ในขณะที่ program กำลังรันข้อมูล เพื่อให้ microcontroller รันโปรแกรมใหม่เข้าไป กดปุ่มสีดำเพื่อให้เกิดการโหลด และกดปุ่มสีแดงเพื่อให้เกิดการรีเซ็ท
    
  • พิมพ์ pio device monitor ผลลัพธ์ที่แสดงคือ ip address
  
  • copy ip address ไปที่ browser สำหรับทดสอบ
  
5. นำ CPU มาต่อกับ sensorแสง (sensorแสงนั้นต่ออยู่กับตัวต้านทาน)
  • ขาข้างแรก ต่อกับไฟเลี้ยงของCPU เส้นสีแดง(ขนาด 3 Volt)
  
  • ขาถัดมา ต่อกับ resistor และเข้าไปต่อกับ port 0(จะต่อภายหลัง) อีกขา ต่อกับเส้นสีดำ หรือ ground
  
  • นำ input เส้นสีขาวต่อกับ sensor ไฟ LED จะสว่าง เมื่อ sensor โดนแสงสว่าง ค่าที่อ่านได้เป็น 0 ดังภาพ
  
  • ไฟ LED จะดับ เมื่อนำนิ้วไปปิดหน้า sensor ค่าที่อ่านได้เป็น 1 ดังภาพ
  

## การบันทึกผลการทดลอง
• การใช้คำสั่ง pio device monitor เพื่อดูผลลัพธ์ของการรันโปรแกรมในไมโครคอนโทรเลอร์ ได้แสดงที่อยู่ไอพีขึ้นมา และเมื่อทำการคัดลอกไปที่บราวเซอร์ ผลลัพธ์ที่แสดงจะขึ้นว่า Hello 1 โดย cnt เปลี่ยนตัวแปรไปเรื่อยๆ

## อภิปรายผลการทดลอง
  • pio run -t upload นั้นใช้ในการอัพโหลดข้อมูลจาก 05_Wifi-Web-Server ไปยัง microcontroller โดยคำสั่ง pio device monitor ที่ใช้ดูผลลัพธ์ของโปรแกรมที่ถูกอัพโหลดเข้าไป ซึ่งในที่นี้คือ ip address แล้วจึงทำการคัดลอกเพื่อไปที่บราวเซอร์สำหรับทดสอบต่อไป

## คำถามหลังการทดลอง 
 คำถาม : ถ้าต้องการผลลัพธ์ ip address ต้องใช้คำสั่งอะไร ?
 
 คำตอบ : pio device monitor
 


