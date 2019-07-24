# Sealed Class

Traits and classes can be marked sealed which means all subtypes must be declared in the same file. This assures that all subtypes are known. This is useful for pattern matching because we don’t need a **catch all** case.

Use this type of class to create enum pattern

### Examples

```scala
sealed abstract class Furniture
case class Couch() extends Furniture
case class Chair() extends Furniture

def findPlaceToSit(piece: Furniture): String = piece match {
  case a: Couch => "Lie on the couch"
  case b: Chair => "Sit on the chair"
}
```



