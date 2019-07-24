# Representing Emptiness

#### null

Scala’s null is the same as in Java. Any reference type can be null, like Strings, Objects, or your own classes. Also just like Java, value types like Ints can’t be null. **Odds are you'll see this one.**

#### Null

Null is a trait whose only instance is null. It is a subtype of all reference types, but not of value types. It purpose in existing is to make it so reference types can be assigned null and value types can’t. **Don't worry about this one.**

#### Nothing

Nothing is a trait that is guaranteed to have zero instances. It is a subtype of all other types. It has two main reasons for existing: to provide a return type for methods that never return normally \(i.e. a method that always throws an exception\). The other reason is to provide a type for Nil \(explained below\). **Don't worry about this one.**

#### Nil

Nil is just an empty list, exactly like the result of List\(\). It is of type List\[Nothing\]. And since we know there are no instances of Nothing, we now have a list that is statically verifiable as empty. Nice to have. **Odds are you'll see this one.**

#### None

None is the counterpart to Some, used when you’re using Scala’s Option class to help avoid null references. If you’re not familiar with the idea of Option or Maybe, here’s an [introduction to Option](https://blog.danielwellman.com/2008/03/using-scalas-op.html). **Odds are you'll see this one.**

#### Unit

Unit in Scala is the equivalent of void in Java. It’s used in a function’s signature when that function doesn’t return a value. **Odds are you'll see this one.**

### Resources

* [http://www.nickknowlson.com/blog/2013/03/31/representing-empty-in-scala/](http://www.nickknowlson.com/blog/2013/03/31/representing-empty-in-scala/)

