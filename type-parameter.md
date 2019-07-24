---
description: aka. Polymorphic Methods
---

# Type Parameter

### Reading

* [https://docs.scala-lang.org/tour/generic-classes.html](https://docs.scala-lang.org/tour/generic-classes.html)
* [https://docs.scala-lang.org/tour/polymorphic-methods.html](https://docs.scala-lang.org/tour/polymorphic-methods.html)

### Notes

* It’s common practice to use single character

### Examples

```scala
class Stack[A] {
  private var elements: List[A] = Nil
  def push(x: A) { elements = x :: elements }
  def peek: A = elements.head
  def pop(): A = {
    val currentTop = peek
    elements = elements.tail
    currentTop
  }
}
```

```scala
def listOfDuplicates[A](x: A, length: Int): List[A] = {
  if (length < 1)
    Nil
  else
    x :: listOfDuplicates(x, length - 1)
}
```

```scala
sealed trait Result[A]
case class Success[A](result: A) extends Result[A] 
case class Failure[A](reason: String) extends Result[A]
```

