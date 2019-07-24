# Option, Some, and None

Some and None is a subclass of Option

So for a function that return or might not return value \(maybe there’s error from input\), we use Option\[T\] as return type. If we can return value, we need to wrap that value inside Some class, so it will strictly respect return type.

```scala
def toInt(in: String): Option[Int] = {
  try {
    Some(Integer.parseInt(in.trim))
  } catch {
    case e: NumberFormatException => None
  }
}
```

