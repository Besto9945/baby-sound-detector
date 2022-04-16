สมาชิกกลุ่ม จาพนมนงรัก
6310503570 นายวีรนนท์ ธุวสิน
6310505751 นายภูมิภัทร เปี่ยมลือ
6310505769 นายสมัชญ์ ห้าวหาญ
6310506790 นายศิวกร กมลดิลก


env directory
    คือ python virsual environment ของโปรเจคนี้

firmware directory
    คือ ที่เก็บโค้ดของตัว microcontroller ประกอบไปด้วย
        1. main.c      ->   ประกอบไปด้วยโค้ดส่วนที่เมื่อมีการตรวจพบเสียงถึงระดับที่เรากำหนด ก็จะไปเปลี่ยนให้ LED ติดเพื่อแสดงให้เห็นว่าสามารถตรวจจับเจอ 
                            และมีฟังก์ชันที่เอาไว้รับ request จากคอมพิวเตอร์ว่าจะเอาสถานะว่าตรวจพบหรือไม่ ส่งคืนค่าไปเป็น 1 ถ้าตรวจจับเสียงได้ ถ้าไม่ก็ 0

        2. peri.c      ->   เป็นไฟล์ที่เก็บรวบรวมฟังก์ชันทั้งหมดที่ใช้ใน main.c ประกอบไปด้วย 
                                1.init_peri ตั้งขาพินว่าจะให้พินไหนเป็น INPUT/OUTPUT
                                2.sed_led เลือกขาพินที่ LED ตั้งอยู่แล้วเซตได้ว่าจะให้ติดหรือดับ เป็น 1 ไฟจะติด ถ้าไม่ก็ 0
                                3.read_adc อ่านค่าเสียงที่ได้จาก sound_sensor

        3. usbconfig.h -> ไฟล์ตั้งค่า usb

        4. peri.h

        5. Makefile

python directory
    คือ ที่เก็บโค้ดที่ใช้สื่อสารกับ microcontroller ประกอบไปด้วย
        1. practicum.py ->  มีคลาส McuBoard ที่มี read/write method ใช้สื่อสารกับ microcontroller และมีคลาส PeriBoard ที่มี method
                            ทำให้ติดต่อสื่อสารกับ microcontroller ได้สะดวกมากขึ้นประกอบไปด้วย
                                1. get_sound return sound value.
                                2. get_detect_sound return  Sound is detected or not.
        2. monitor.py   ->  ดูข้อมูลตั้งหมดที่ได้จาก sound_sensor โดยใช้ method จาก practicum.py แสดงผลทุกๆ 0.5 วินาที
                            โดยจะมีโค้ดที่ใช้ส่งข้อความไปใน line notify อยู่ด้วย

picture and slide ประกอบไปด้วย
    1. schematic.jpg
    2. slide.pdf

requirements.txt
    python packepage ที่ใช้ สามารถ pip install -r requirements.txt ได้


อุปกรณ์ที่ใช้
1.Raspberry pi x1
2.LED 1 ชุด
3.ky-038 x1
4.Breadboard x1
5.สายไฟ x1
6.Board NodeMCU - ATmega328p (Practicum Board v3.2 CPE. KU 2020-11) x1
7.ตัวต้านทาน 330Ω x1
8.สายแพร์ x1
9.Practicum Breakout CPE KU x1