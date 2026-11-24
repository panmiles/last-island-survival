# วิธีนำ LAST ISLAND Survival Online 2.0 ขึ้น Render โดยไม่ต้องติดตั้งโปรแกรม

## 1. สร้าง GitHub repository
1. สมัครหรือเข้าสู่ระบบ https://github.com
2. กด New repository ตั้งชื่อ `last-island-survival` เลือก Private หรือ Public แล้ว Create repository
3. ในหน้า repository เลือก `uploading an existing file` หรือ Add file > Upload files
4. แตก ZIP นี้ก่อน จากนั้นลากไฟล์และโฟลเดอร์ทั้งหมด **ภายใน** `last-island-render` ลงหน้าอัปโหลด (ตรวจสอบว่ามี `public/index.html`)
5. กด Commit changes

หมายเหตุ: GitHub เว็บอาจมีข้อจำกัดในการอัปโหลดโฟลเดอร์ผ่านมือถือ ใช้คอมพิวเตอร์ผ่านเบราว์เซอร์จะง่ายกว่า และหากโฟลเดอร์ `public` ไม่ถูกอัปโหลด ให้สร้าง `public/index.html` ผ่าน Add file > Create new file โดยพิมพ์ชื่อไฟล์เป็น `public/index.html` แล้ววางโค้ดจากไฟล์ต้นฉบับ

## 2. สร้าง Render Web Service
1. เข้า https://dashboard.render.com แล้วเข้าสู่ระบบ
2. เลือก New > Web Service แล้วเชื่อม GitHub repository `last-island-survival`
3. ตั้งค่า: Language/Runtime = Node, Branch = main, Root Directory = เว้นว่าง, Build Command = `npm install`, Start Command = `npm start`
4. เลือก instance ที่เหมาะสม (Free หากมีให้เลือก) ตรวจสอบราคา/ข้อจำกัดในหน้า Render ก่อนกดยืนยัน
5. กด Deploy Web Service และรอจนสถานะ Live
6. เปิด URL ที่ Render ให้ เช่น `https://ชื่อบริการ.onrender.com` (ชื่อจริงขึ้นอยู่กับ Render)
7. ส่ง URL ให้เพื่อน แล้วทุกคนใส่รหัสห้องเดียวกันเพื่อเล่นด้วยกัน

## 3. ตรวจสอบ
- เข้า `https://<ชื่อบริการจริง>.onrender.com/health` ควรเห็น JSON status ok
- เปิดเกม 2 เครื่องด้วยรหัสห้องเดียวกันและทดสอบการเคลื่อนไหว/แชต
- หากเจอ 404 ให้ตรวจสอบ `public/index.html` อยู่ใน repo และ Root Directory เว้นว่าง
- หาก Deploy failed ดู Logs ตรวจสอบ Build/Start commands และ Node runtime
- หากขึ้นหน้าเว็บแต่เข้าเกมไม่ได้ ตรวจสอบ Console/Logs และ WebSocket connection

## ข้อจำกัด
- แผน Free (ถ้ามีให้เลือก) อาจพักบริการเมื่อไม่มีคนใช้งานและใช้เวลาปลุกเมื่อเปิดเกมใหม่
- เกมใช้สถานะใน RAM จึงล้างความคืบหน้าเมื่อ Render restart/redeploy/sleep
- ควรใช้เซิร์ฟเวอร์เพียง 1 instance เพราะห้อง/ผู้เล่นยังไม่แชร์ข้อมูลข้าม instance
- เกมนี้เป็นต้นแบบ ยังไม่มีบัญชีผู้เล่น การบันทึกข้อมูลถาวร หรือมาตรการป้องกันการโจมตีครบถ้วน
- Render อาจเปลี่ยนเมนู แผน และราคา โปรดตรวจสอบก่อน Deploy
