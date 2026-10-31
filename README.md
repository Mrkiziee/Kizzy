# Kizzy

## Kizzy – CRT Blueprint (TradingView indicator)

ไฟล์: [`kizzy_crt_blueprint.pine`](kizzy_crt_blueprint.pine) (Pine Script v6)

อินดิเคเตอร์ Candle Range Theory (CRT) ที่จับ CRT ได้พร้อมกัน 3 ไทม์เฟรม (ค่าเริ่มต้นคือ 30m / 1H / 4H)

- **C1** คือแท่งที่กำหนดกรอบราคา: ใช้ high เป็น **CRH** และ low เป็น **CRL**
- **C2** คือแท่งที่ไส้กวาดออกนอกกรอบด้านใดด้านหนึ่ง แล้วปิดกลับเข้ามาในกรอบ
- **Bear CRT** คือ C2 กวาด CRH แล้วปิดกลับลงมา ใช้ TP1 = 50% ของ C1 และ TP2 = CRL
- **Bull CRT** คือ C2 กวาด CRL แล้วปิดกลับขึ้นมา ใช้ TP1 = 50% ของ C1 และ TP2 = CRH
- **Invalidated** คือราคาวิ่งเลยจุดสุดของไส้ C2 ไปก่อนจะถึง TP2

### สิ่งที่แสดงบนกราฟ
- เส้น CRH, CRL และ TP1 ของแต่ละไทม์เฟรม เลือกสไตล์เส้นแยกกันได้ (Solid / Dashed / Dotted)
- แท่งเทียน HTF (C1, C2 และแท่งที่กำลังวิ่งอยู่) วาดไว้ทางขวาของกราฟ
- Dashboard บอกสถานะของแต่ละไทม์เฟรม เช่น Bear CRT, TP1 ✓, TP2 ✓ และ CRT ที่กำลังก่อตัว (Live)
- พื้นหลังแยกสีตามเซสชัน Asia / London / New York (แสดงบนกราฟ ≤ 1H)

### ตัวกรอง
- **Quality CRT Only**: C2 ต้องเปิดอยู่ในกรอบของ C1 และมีแค่ไส้ที่กวาดออกไป
- **Opposite-Color Child Only**: C1 กับ C2 ต้องเป็นแท่งคนละสีกัน
- **Max Wick % (vs Body)**: ไส้รวมของ C1 ต้องยาวไม่เกินกี่ % ของตัวแท่ง (ใส่ 0 = ปิด)

### วิธีติดตั้ง
1. เปิด TradingView แล้วไปที่ Pine Editor จากนั้นวางโค้ดทั้งไฟล์ลงไป แล้วกด **Add to chart**
2. ดับเบิลคลิกที่ dashboard หรือตัวอินดิเคเตอร์เพื่อเปิด Settings แล้วเลือก TF ที่ต้องการ

### ตั้ง Alert
1. ไปที่ Alerts แล้วกด **+** เพื่อสร้าง alert ใหม่
2. Condition: เลือก **Kizzy CRT** แล้วเลือก **Any alert() function call**
3. Interval: แนะนำให้ใช้ **45s หรือ 1m** เพราะไทม์เฟรมที่ต่ำกว่านี้อาจส่ง alert ซ้ำ
4. ถ้าเปลี่ยน TF ใน Settings ต้องลบ alert เก่าแล้วสร้างใหม่

> หมายเหตุ: alert จากอินดิเคเตอร์ใช้ได้กับ TradingView แพ็กเกจ Essential ขึ้นไป · ไม่ใช่คำแนะนำการลงทุน
