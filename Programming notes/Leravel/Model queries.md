=> query builder functions require ->`get()` at last 
=> The functions which are not query builders do not require ->`get()`


=> query builder functions start with `where, latest` etc
=> not query builder functions start with `all()` , etc

### TO find a single record
1. `firstWhere()`
2. `find(id)
3. `findOrFail(id)`

=> if you use all() or queries to find a single record => get() is not required 
=> else it is required

=> write `->toSql()`in place of get to get the sql query

https://github.com/barryvdh/laravel-ide-helper?tab=readme-ov-file#model-hooks 
=> the above is required for intellisense for eloquent queries


=> The order in which you call the query builder functions does not matter.
=> but it is not always the case if you use order by the first order by takes precedence over 2nd order by.

=>  **PHP is partially case-sensitive**. PHP constructs, function names, class names are case-insensitive, whereas variables are case-sensitive.

