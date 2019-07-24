# Option, Some and None

### Reading

* [https://alvinalexander.com/scala/best-practice-option-some-none-pattern-scala-idioms](https://alvinalexander.com/scala/best-practice-option-some-none-pattern-scala-idioms)

### Returning an Option from a method

```scala
def toInt(s: String): Option[Int] = {
    try {
        Some(Integer.parseInt(s.trim))
    } catch {
        case e: Exception => None
    }
}
```

### Getting the value from an Option

* Use `getOrElse`
* Use `foreach`
* Use a `match` expression

```scala
scala> val x = toInt("1").getOrElse(0)
x: Int = 1
```

```scala
toInt("1").foreach{ i =>
    println(s"Got an int: $i")
}
```

```scala
toInt("1") match {
    case Some(i) => println(i)
    case None => println("That didn't work.")
}
```

