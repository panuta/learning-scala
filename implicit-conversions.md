# Implicit Conversions

คือการพยายามแก้ compile error ที่เกิดขึ้นจาก

1. Type ของตัวแปรไม่ตรงกับที่ต้องการ
2. Class instance ไม่มี method ที่กำลังจะเรียก
3. ไม่ได้ใส่ Function parameter ที่ function นั้นๆ ต้องการเวลา call function นั้น

โดยการหา implicit variable, function, หรือ object definition เพื่อมาแก้ปัญหาให้โดยอัตโนมัติ

A way to automatically fix type errors, by trying to add implicit conversion to it to see if it works. Implicit conversion can be defined as variable, function, or object definition.

For example, if x + y does not type check, then the compiler might change it to convert\(x\) + y, where convert is some available implicit conversion. If convert changes x into something that has a + method, then this change might fix a program so that it type checks and runs correctly.

### Implicit rules

* Marking rule: **Only definitions marked implicit are available**
* Scope rule: An inserted implicit conversion **must be in scope as a single identifier**, or be associated with the source or target type of the conversion 
  * Single identifier means, implicit conversion must be imported as  `import Libraries.convert => expand to => convert(x)` the following will not works  `import Libraries => will NOT expand to => Libraries.convert(x)` 
  * The compiler will also look for implicit definitions in the companion object of the source or expected target types of the conversion.  See following code →

```scala
object Dollar {
  implicit def dollarToEuro(x: Dollar): Euro = ...
}

class Dollar { ... }

// dollarToEuro method can also be implemented in Euro class
```

* One-at-a-time rule: **Only one implicit is inserted**
* Explicits-first rule: Whenever code type checks as it is written, no implicits are attempted
  * **The compiler will not change code that already works**

### **Where implicits are tried**

1. Conversions to an expected type
2. Conversions of the receiver of a selection
3. Implicit parameters

#### **Implicit Conversion to an Expected Type**

The rule is simple. Whenever the compiler sees an X, but needs a Y, it will look for an implicit function that converts X to Y.

```scala
val i: Int = 3.5
// error: type mismatch; found: Double(3.5); required: Int

implicit def doubleToInt(x: Double) = x.toInt
val i: Int = 3.5
// Int = 3
```

#### Converting the Receiver

Implicit conversions also apply to the receiver of a method call, the object on which the method is invoked.

ประโยชน์ของ implicit conversion แบบนี้คือ

* เพิ่ม method ให้ class ที่เราไม่ได้เขียนเอง โดยไม่ต้องไปแก้ code ของ class นั้นๆ และสามารถใช้ได้โดยไม่ต้องเปลี่ยนชื่อ class แบบวิธี extends
* เพิ่ม method ไปที่ scala.Predef class เพื่อใช้สร้าง syntax ใหม่ๆ ของเราเอง \(Domain-Specific Language\) 
  * scala.Predef เป็น class ที่จะถูก import เข้ามาโดยอัตโนมัติใน scala ทุกไฟล์ → import scala.Predef.\_ เพื่อให้เราสามารถใช้ function ทั่วๆ ไปได้โดยไม่ต้อง import เข้ามา เช่น println

การสร้าง method ใหม่ขึ้นมาบน class เดิม มีวิธีเขียนได้ 2 แบบ

```scala
class Rational(n: Int, d: Int) {
  def + (that: Int): Rational = ...
}

val oneHalf = new Rational(1, 2)
// oneHalf: Rational = 1/2

oneHalf + 1
// res1: Rational = 3/2

1 + oneHalf
// error: overloaded method value + with alternatives (Double)Double <and> ... cannot be applied to (Rational)

implicit def intToRational(x: Int) = new Rational(x, 1)

1 + oneHalf
// res2: Rational = 3/2
```

วิธีที่ 2 คือการสร้าง implicit class ขึ้นมา

```scala
case class Rectangle(width: Int, height: Int)

// Implicit class
implicit class RectangleMaker(width: Int) {
  def x(height: Int) = Rectangle(width, height)
}
  
// Above implicit class will automatically generated ->
implicit def RectangleMaker(width: Int) = new RectangleMaker(width)

val myRectangle = 3 x 4
// myRectangle: Rectangle = Rectangle(3,4)
```

ซึ่งการสร้าง implicit class มีประโยชน์ตรงที่เราสามารถ define function หลายๆ อันใน class เดียวกันได้ เป็นการจัดกลุ่ม

Implicit class มีข้อจำกัดคือ

* They must be defined inside of another trait/class/object.
* They may only take one non-implicit argument in their constructor.
* There may not be any method, member or object in scope with the same name as the implicit class.

