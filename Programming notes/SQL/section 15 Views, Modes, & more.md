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
```sql
1. SELECT
2. title,
3. AVG(rating),
4. COUNT(rating) AS review_count
5. FROM full_reviews
6. GROUP BY title HAVING COUNT(rating) > 1;
```
