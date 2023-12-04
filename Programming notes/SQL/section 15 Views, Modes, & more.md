## View

- View acts as a virtual table.
- views are some sql queries which we can give a name to and store. 
- When we invoke a view we se the result of the sql query.
- It looks like a table.

```
1. -- INSTEAD OF TYPING THIS QUERY ALL THE TIME...
2. SELECT
3. title, released_year, genre, rating, first_name, last_name
4. FROM
5. reviews
6. JOIN
7. series ON series.id = reviews.series_id
8. JOIN
9. reviewers ON reviewers.id = reviews.reviewer_id;

11. -- WE CAN CREATE A VIEW:
12. CREATE VIEW full_reviews AS
13. SELECT title, released_year, genre, rating, first_name, last_name FROM reviews
14. JOIN series ON series.id = reviews.series_id
15. JOIN reviewers ON reviewers.id = reviews.reviewer_id;

17. -- NOW WE CAN TREAT THAT VIEW AS A VIRTUAL TABLE
18. -- (AT LEAST WHEN IT COMES TO SELECTING)
19. SELECT * FROM full_reviews;
```
## Updatable views

- Only very small portion of views are updatable and insertable.
- join views are not updatable and insertable.
- If you use group by , aggregate functions, sub queries ,having, union, join etc. => not updatable.
- Order by is updatable.
- simple views are updatable.
- `CREATE VIEW ordered_series AS SELECT * FROM series ORDER BY released_year;` => Updatable => can both insert and delete rows.
## Replacing / Altering views

> `CREATE OR REPLACE` => If the view does not exist create the view else replace the view
> `ALTER VIEW` => works exactly same as `CREATE OR REPLACE`
> `DROP VIEW` => Delete a view.

```
1. CREATE VIEW ordered_series AS
2. SELECT * FROM series ORDER BY released_year;

4. CREATE OR REPLACE VIEW ordered_series AS
5. SELECT * FROM series ORDER BY released_year DESC;

7. ALTER VIEW ordered_series AS
8. SELECT * FROM series ORDER BY released_year;

10. DROP VIEW ordered_series;
```



## Having clause

- used with `group by`
- refine based on aggregation functions. 
- used to filter the groups which we get on `group by`
-  In case of group by if all the rows with in a group has same value then there is no problem. However if rows have different values in a group and that row is selected then MySql will give an error. #imp
- `where` selects the rows before grouping. `having` selects the rows after grouping.

```sql
1. SELECT
2. title,
3. AVG(rating),
4. COUNT(rating) AS review_count
5. FROM full_reviews
6. GROUP BY title HAVING COUNT(rating) > 1;
```

## With rollup

> Similar to normal `group by` except 1 extra row is added with avg of entire column.

```sql
1. SELECT
2. title, AVG(rating)
3. FROM
4. full_reviews
5. GROUP BY title WITH ROLLUP;

8. SELECT
9. title, COUNT(rating)
10. FROM
11. full_reviews
12. GROUP BY title WITH ROLLUP;

15. SELECT
16. first_name, released_year, genre, AVG(rating)
17. FROM
18. full_reviews
19. GROUP BY released_year , genre , first_name WITH ROLLUP;

```
![[Pasted image 20231204112942.png]]
## SQL modes basics

```sql
1. -- To View Modes:
2. SELECT @@GLOBAL.sql_mode;
3. SELECT @@SESSION.sql_mode;

5. -- To Set Them:
6. SET GLOBAL sql_mode = 'modes';
7. SET SESSION sql_mode = 'modes';
```
![[Pasted image 20231204114035.png]]
- SQL modes are sql settings.
- session modes are applicable to current session.
- Global modes are applicable all the time.
### Different sql modes
1. `ERROR_FOR_DIVISION_BY_ZERO` => shows warning when we divide by 0.
2. `STRICT_TRANS_TABLES`