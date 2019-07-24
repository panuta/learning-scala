# Strict vs. Non-Strict Function

`filter` is strict function → evaluate List immediately  
`withFilter` is non-strict function → evaluate only when needed

Boolean functions e.g. `&&` and `||` is non-strict function because it contains short-circuiting

Non-strict function is another name of **Call by Name**

```scala
func(x: Int, y: => Int)
```

