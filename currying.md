# Currying

```scala
// Use function that returns function
def sum(f: Int => Int): (Int, Int) => Int = {
  def sumF(a: Int, b: Int): Int = {
    if (a > b) 0
    else f(a) + sumF(a + 1, b)
  }
  sumF
}
println(sum(x => x)(1, 4))

// Use currying
def csum(f: Int => Int)(a: Int, b: Int): Int = {
  if (a> b) 0
  else f(a) + csum(f)(a + 1, b)
}
println(csum(x => x)(1, 4))
```

