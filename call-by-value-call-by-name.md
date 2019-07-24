# Call by Value, Call by Name

Call by Value -&gt; argument จะถูก evaluate ก่อนส่งเข้า function Call by Name -&gt; argument จะถูกส่งเข้า function ก่อน แล้วค่อยถูก evaluate ตอนที่ต้องใช้จริงๆ

โดย default แล้ว Scala จะเป็น Call by Value แต่สามารถบังคับให้เป็น Call by Name ได้

func\(x: Int, y: =&gt; Int\)

จาก function ด้านบน x จะถูก evaluate แบบ Call by Value ส่วน y จะถูก evaluate แบบ Call by Name

### Call by Value

```scala
sumOfSquares(3, 2+2)
sumOfSquares(3, 4)
square(3) + square(4)
3 * 3 + square(4)
9 + square(4)
9 + 4 * 4
9 + 16
25
```

### Call by Name

```scala
sumOfSquares(3, 2+2)
square(3) + square(3)
3 * 3 + square(2+2)
9 + square(2+2)
9 + (2+2) * (2+2)
9 + 4 * (2+2)
9 + 4 * 4
25
```

