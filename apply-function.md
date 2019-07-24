# Apply Function

> Mathematicians have their own little funny ways, so instead of saying "then we call function f passing it x as a parameter" as we programmers would say, they talk about "applying function f to its argument x”.

from [https://stackoverflow.com/questions/9737352/what-is-the-apply-function-in-scala](https://stackoverflow.com/questions/9737352/what-is-the-apply-function-in-scala)

ใส่ apply function ใน class จะสามารถทำให้เรียก instance ของ class นั้นแบบ function call ได้

```scala
class A {
  def apply(x: Int): Int = x
}

var f = new A()

println(f(5))
```

ซึ่งประโยชน์ที่ได้จากการใช้ apply function เมื่อเทียบกับการเรียกผ่าน method คือ instance ของ class สามารถส่งต่อไปมาผ่าน parameter ได้

