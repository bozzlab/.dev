---
description: แล้วทำไมต้อง TypeScript
---

# TypeScript คืออะไร?

## TypeScript แบบขอสั้นๆ

มันคือ JavaScript แต่มี Type จบ

### ทำไมต้องมี Type?

จริงๆ แล้ว JavaScript ก็มี Type แหละ แต่มันมีความเป็น Dynamically Typed แปลว่าประเภทของตัวแปรหรือฟังก์ชั่นต่างๆ จะเปลี่ยนได้ตลอดเวลา ต่างกับ TypeScript ที่จะเป็น Statically Typed คือต้องมีการกำหนดประเภทให้มัน

```javascript
// JavaScript
let a = 42 // a เป็น int
let b = 'test' // b เป็น string
b = a * 10 // b กลายเป็น int (420)
```

ข้อดีของ JavaScript แบบดั้งเดิมคือ เขียนง่าย เข้าใจง่าย และมีความอิสระ อยากแก้ค่าในตัวแปรแบบไหนก็ทำได้เลย 

แล้วมันไม่ดียังไง?

ขอยกตัวอย่างง่ายๆ เช่นเวลาเราเขียนเว็บแล้วรับค่าจากฟอร์ม  แต่ว่าเราลืมแปลงให้มันเป็น `int` 

```javascript
function sum(a, b) {
  return a + b
}

// สมมุติว่ามีค่าเป็น "10" ที่ดันเป็น string เพราะอ่านค่าจาก Form
sum(input.value, 30)

// อยากได้ 40 แต่ดันเป็น "1030" เพราะเป็นการเอาเลขมาต่อกันเฉยๆ ไม่ได้บวกกัน
```

วิธีแก้ไขในแบบ JavaScript จะต้องแก้ที่ปลายเหตุ แบบนี้

```javascript
function sum(a, b) {
  return Number(a) + Number(b)
}

sum("10", 30) // 40
```

อีกตัวอย่างหนึ่งที่พบบ่อยคือการ "พิมพ์ผิด" อย่างเช่นการเรียกตัวแปรในออบเจ็กต์

```javascript
const user = {
  firstName: "ประหยัด",
  lastName: "จานโอชา",
  job: "Dictator"
}

console.log(user.firstname) // undefined
```

ถ้าเราเลือกใช้ TypeScript โค้ดจะเป็นแบบนี้แทน

```typescript
function sum(a: number, b: number) { // กำหนดให้ a และ b ต้องเป็น type number
  return a + b
}

sum("10", 30)
```

พอเรารันโค้ด \(หรือใน Code Editor\) จะขึ้น Error มาให้เราเห็นเลย ว่าเราใช้งานผิด Type

![](../.gitbook/assets/image%20%281%29.png)

ส่วนการสร้างออบเจ็กต์ Type จะถูกสร้างตามโดยอัตโนมัติ \(เรียกว่า [Type Inference](https://www.typescriptlang.org/docs/handbook/type-inference.html) "การอนุมานประเภท" 😅\) ทำให้เมื่อเรียก Attribute ที่ไม่มีอยู่แล้วจะเกิด Error ขึ้นเช่นกัน

![](../.gitbook/assets/image%20%282%29.png)

นอกจากนี้ ถ้าไลบรารี่สนับสนุน TypeScript \(ซึ่งส่วนใหญ่สนับสนุนแล้ว\) เราจะรู้ได้ทันทีว่าสิ่งที่ Import มารับ Argument แบบไหน คืนค่าประเภทไหนออกมา แล้วเมื่อเรานำไปใช้แต่ใช้งานผิด ก็จะทำการเตือนเราทันที

![&#xE16;&#xE49;&#xE32;&#xE43;&#xE0A;&#xE49;&#xE40;&#xE1B;&#xE47;&#xE19;&#xE41;&#xE25;&#xE49;&#xE27;&#xE14;&#xE39;&#xE1C;&#xE48;&#xE32;&#xE19;&#xE46; &#xE08;&#xE30;&#xE40;&#xE02;&#xE49;&#xE32;&#xE43;&#xE08;&#xE17;&#xE31;&#xE19;&#xE17;&#xE35; &#xE15;&#xE2D;&#xE19;&#xE19;&#xE35;&#xE49;&#xE14;&#xE39;&#xE41;&#xE25;&#xE49;&#xE27;&#xE22;&#xE31;&#xE07;&#xE44;&#xE21;&#xE48;&#xE40;&#xE02;&#xE49;&#xE32;&#xE43;&#xE08;&#xE01;&#xE47;&#xE40;&#xE2D;&#xE2D;&#xE2D;&#xE2D;&#xE2B;&#xE48;&#xE2D;&#xE2B;&#xE21;&#xE01;&#xE44;&#xE1B;&#xE01;&#xE48;&#xE2D;&#xE19; &#x1F606;](../.gitbook/assets/image%20%283%29.png)

![&#xE15;&#xE31;&#xE27;&#xE2D;&#xE22;&#xE48;&#xE32;&#xE07; : useState &#xE08;&#xE30;&#xE04;&#xE37;&#xE19; Array\(2\) &#xE21;&#xE32;&#xE41;&#xE15;&#xE48;&#xE14;&#xE31;&#xE19;&#xE43;&#xE0A;&#xE49; Object &#xE44;&#xE1B;&#xE23;&#xE31;&#xE1A;](../.gitbook/assets/image%20%284%29.png)

การใช้ TypeScript แทน JavaScript ถึงแม้ว่ามันจะมี Learning Curve ที่มากขึ้น แต่จะทำให้เราและทีมเขียนโค้ดได้อย่างรัดกุมมากขึ้น และเกิด Bug น้อยลงได้

## อ้างอิง

* [https://www.typescriptlang.org](https://www.typescriptlang.org/)

