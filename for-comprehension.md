# For Comprehension

`<-` is called **for comprehension**

### Examples

```scala
case class User(name: String, age: Int)

val userBase = List(User("Travis", 28),
  User("Kelly", 33),
  User("Jennifer", 44),
  User("Dennis", 23))

val twentySomethings = for (user <- userBase if (user.age >=20 && user.age < 30))
  yield user.name  // i.e. add this to a list

twentySomethings.foreach(name => println(name))  // prints Travis Dennis
```

```scala
for(x <- c1; y <- c2; z <-c3) {...}

// Translated to
c1.foreach(x => c2.foreach(y => c3.foreach(z => {...})))
```

```scala
for(x <- c; if cond) yield {...}

// Translated to
c.withFilter(x => cond).map(x => {...})

// With fallback, if withFilter is not available
c.filter(x => cond).map(x => {...})
```

