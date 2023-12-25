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
