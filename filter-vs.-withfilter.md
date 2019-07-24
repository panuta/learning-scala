# filter vs. withFilter

The difference between `c filter p` and `c withFilter p` is that the former creates a new collection, whereas the latter only restricts the domain of subsequent map, flatMap, foreach, and withFilter operations.

`withFilter` will return FilterMonadic, which only has the following methods

* map
* flatMap
* foreach
* withFilter

Notice there’s no `filter` function, so we cannot chain `withFilter` and `filter`.

