---
description: aka. Placeholder Syntax
---

# Underscore

### Reading

* [https://ananthakumaran.in/2010/03/29/scala-underscore-magic.html](https://ananthakumaran.in/2010/03/29/scala-underscore-magic.html)
* [https://medium.com/@LetsGoCard/yet-another-post-about-the-underscore-in-scala-ae7be854f0d3](https://medium.com/@LetsGoCard/yet-another-post-about-the-underscore-in-scala-ae7be854f0d3)

### Examples

```scala
// Without underscore
(x:Int) => x + 1

// With underscore
(_:Int) + 1
```

```scala
val f = (_:String) + 1
val g = (_:Int) + 1

// returns "11"
f("1")

// returns 2
g(1)
```

```scala
// the underscore below must be an int; List(2, 3, 4) is returned
List(1, 2, 3).map(_ + 1)

// the underscore below must be a string; List("11", "21", "31") is returned
List("1", "2", "3").map(_ + 1)
```

```scala
val f2 = "The first int is " + (_:Int) + " and the second int is " + (_:Int)

// returns "The first int is 1 and the second int is 2"
f2(1, 2)
```

```scala
// Both underscores must be ints; returns 6
List(1, 2, 3).foldLeft(0)(_ + _)
```

