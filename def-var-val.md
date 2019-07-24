# def var val

The def form is “call-by-name”, its right hand side is evaluated on each use

The right-hand side of a val definition is evaluated at the point of the definition itself. Afterwards, the name refers to the value.

```scala
val x = 2
val y = square(x)
// y will refers to 4, not square(2)

def z = square(x)
// z will refers to square(2), not 4
```

