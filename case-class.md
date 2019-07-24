# Case Class

Plain and immutable data-holding objects that should exclusively depend on their constructor arguments

Case class จะมี method บางอัน predefine มาไว้ให้เลย เช่น apply, equals

```scala
case class Person(firstname: String, lastname: String)

// Can create instance without using 'new' because case class have apply function built-in
a1 = Person("A", "a")
a1 = Person("A", "a")

// Can use == to check if instance's value is equal
a == b
// True

// Pattern matching
for (person <- List(alice, bob, charlie)) {
  person match {
    case Person("A", "a") => println("Hi Alice!")
    case Person("B", "b") => println("Hi Bob!")
  }
}
```

