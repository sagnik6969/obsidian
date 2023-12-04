where => group by => order by
round(1.12345,2) => 1.12
`ifnull()`
```
1. IF(COUNT(rating) > 0,
2. 'ACTIVE',
3. 'INACTIVE') AS status
```
`dayname(created_at)` => returns Monday, Tuesdays,  etc
`weekday(created_at)` => returns 0,1,2,3,4,5,6,7 etc

=> where clause goes before group by telling what data you want to group.