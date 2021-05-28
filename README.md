# RasPi-NodeRed
RaspberryPi4 B install NodeRed

อ้างอิง https://nodered.org/docs/getting-started/raspberrypi

**ติดตั้ง**
~~~
$ bash <(curl -sL https://raw.githubusercontent.com/node-red/linux-installers/master/deb/update-nodejs-and-nodered)
~~~

**start**
~~~
$ node-red
~~~

**stop**
~~~
Ctrl-C
~~~

เนื่องจากหน่วยความจำที่ จำกัด ของ Raspberry Pi คุณจะต้องเริ่มต้น Node-RED ด้วยอาร์กิวเมนต์เพิ่มเติมเพื่อบอกกระบวนการ Node.js ที่อยู่เบื้องหลังเพื่อเพิ่มหน่วยความจำที่ไม่ได้ใช้ให้เร็วกว่าที่ควร

ในการดำเนินการนี้คุณควรใช้node-red-piคำสั่งทางเลือกและส่งผ่าน max-old-space-sizeอาร์กิวเมนต์

~~~
$ node-red-pi --max-old-space-size=256
~~~

**ทำงานเป็นบริการ**
สคริปต์การติดตั้งสำหรับ Pi ยังตั้งค่าให้ทำงานเป็นบริการ ซึ่งหมายความว่าสามารถทำงานในพื้นหลังและเปิดใช้งานเพื่อเริ่มการบูตโดยอัตโนมัติ

คำสั่งต่อไปนี้มีไว้เพื่อทำงานกับบริการ:
- node-red-start- สิ่งนี้เริ่มต้นบริการ Node-RED และแสดงเอาต์พุตบันทึก การกดCtrl-Cหรือปิดหน้าต่างไม่ได้หยุดบริการ มันยังคงทำงานในพื้นหลัง
- node-red-stop - สิ่งนี้จะหยุดบริการ Node-RED
- node-red-restart - สิ่งนี้จะหยุดและเริ่มบริการ Node-RED ใหม่
- node-red-log - แสดงเอาต์พุตบันทึกของบริการ

คุณยังสามารถเริ่มบริการ Node-RED บน Raspbian Desktop ได้โดยเลือกMenu -> Programming -> Node-REDตัวเลือกเมนู

**เริ่มต้นอัตโนมัติเมื่อบูต**
หากคุณต้องการให้ Node-RED ทำงานเมื่อ Pi เปิดอยู่หรือบูตใหม่คุณสามารถเปิดใช้งานบริการเพื่อเริ่มการทำงานอัตโนมัติโดยเรียกใช้คำสั่ง:
~~~
$ sudo systemctl enable nodered.service
~~~

**หากต้องการปิดใช้งานบริการให้เรียกใช้คำสั่ง**
~~~
$ sudo systemctl disable nodered.service
~~~

### เมื่อ Node-RED ทำงานคุณสามารถเข้าถึงตัวแก้ไขในเบราว์เซอร์

***หากคุณกำลังใช้เบราว์เซอร์บนเดสก์ท็ Pi คุณสามารถเปิดที่อยู่: http: // localhost: 1880***
