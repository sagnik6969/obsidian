where => group by => having => order by => limit
round(1.12345,2) => `1.12`
`ifnull()`
```
1. IF(COUNT(rating) > 0,
2. 'ACTIVE',
3. 'INACTIVE') AS status
```
`dayname(created_at)` => returns Monday, Tuesdays,  etc
`weekday(created_at)` => returns 0,1,2,3,4,5,6,7 etc

=> where clause goes before group by telling what data you want to group.
=>= is case insensitive.
=> UPDATE cats SET breed='Shorthair' WHERE breed='Tabby'; => **no into keyword in update**
=> DELETE FORM
=> 1. `SELECT CONCAT_WS('-',title, author_fname, author_lname) FROM books;`
CONCAT_WS ⇒ concatinate with separator. separator should be the first argument.

=> `id INT(10) UNSIGNED NOT NULL AUTO_INCREMENT`
=> different datatypes in sql.
=> order by and limit is faster then subquery.
=> remember , in case of limit with 2 inputs.
=> from where index starts in different queries



