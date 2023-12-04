## Not equal

```
SELECT * FROM books
WHERE released_year != 2017;
```

## Not like

```
1. SELECT * FROM books
2. WHERE title NOT LIKE '%e%';
```
## Greater than

> True is evaluated to 1 and false is ecaluated to 0 in sql. 

```
1. SELECT * FROM books
2. WHERE released_year > 2005;

4. SELECT * FROM books
5. WHERE pages > 500;
```
## Greater than equal to

```
1. SELECT * FROM books
2. WHERE released_year <= 1985;
```
## Logical and

```
1. SELECT title, author_lname, released_year FROM books
2. WHERE released_year > 2010
3. AND author_lname = 'Eggers';

5. SELECT title, author_lname, released_year FROM books
6. WHERE released_year > 2010
7. AND author_lname = 'Eggers'
8. AND title LIKE '%novel%';
```
## Logical or

```
1. SELECT title, author_lname, released_year FROM books
2. WHERE author_lname='Eggers' OR
3. released_year > 2010;

6. SELECT title, pages FROM books
7. WHERE pages < 200
8. OR title LIKE '%stories%';
```
## Between

> Remember to add **and** keyword in between
> **The MySQL BETWEEN operator is inclusive**

```
1. SELECT title, released_year FROM books
2. WHERE released_year <= 2015
3. AND released_year >= 2004;

5. SELECT title, released_year FROM books
6. WHERE released_year BETWEEN 2004 AND 2014;
```

> Similarly **not between**
## Comparing dates

```
1. SELECT * FROM people WHERE birthtime
2. BETWEEN CAST('12:00:00' AS TIME)
3. AND CAST('16:00:00' AS TIME);

6. SELECT * FROM people WHERE HOUR(birthtime)
7. BETWEEN 12 AND 16;
```

> Most of the times my sql can automatically type cast string into date time.

> Cast helps us to convert 1 data type to another.

## In operator

> remember to use only first bracket

```
1. SELECT title, author_lname FROM books
2. WHERE author_lname IN ('Carver', 'Lahiri', 'Smith');

4. SELECT title, author_lname FROM books
5. WHERE author_lname NOT IN ('Carver', 'Lahiri', 'Smith');
```


## % Operator
```
1. SELECT title, released_year FROM books
2. WHERE released_year >= 2000
3. AND released_year % 2 = 1;
```


## Case Operator
```
1. SELECT title, released_year,
2. CASE
3. 	WHEN released_year >= 2000 THEN 'modern lit'
4.     ELSE '20th century lit' 
5. END AS genre
6. FROM books;

9. SELECT 
10.     title,
11.     stock_quantity,
12.     CASE
13.         WHEN stock_quantity BETWEEN 0 AND 40 THEN '*'
14.         WHEN stock_quantity BETWEEN 41 AND 70 THEN '**'
15.         WHEN stock_quantity BETWEEN 71 AND 100 THEN '***'
16.         WHEN stock_quantity BETWEEN 101 AND 140 THEN '****'
17.         ELSE '*****'
18.     END AS stock
19. FROM
20.     books;

23. SELECT 
24.     title,
25.     stock_quantity,
26.     CASE
27.         WHEN stock_quantity <= 40 THEN '*'
28.         WHEN stock_quantity <= 70 THEN '**'
29.         WHEN stock_quantity <= 100 THEN '***'
30.         WHEN stock_quantity <= 140 THEN '****'
31.         ELSE '*****'
32.     END AS stock
33. FROM
34.     books;
```
## Is null
```
 select * from books where title is null;
  select * from books where title is not null;
```

## To delete a database

```
 drop database x;
```

