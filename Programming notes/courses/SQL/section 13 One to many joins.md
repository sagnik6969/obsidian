## relationships
1. One to one
2. One to many - relationship between book to reviews
3. Many to many - books and authors.
## One to many

> Customers and orders.
> => Customer first name, last name =, email.
> => order date, amount
> => We can store them in single table => this will result in data redundancy.
> => One to many relationship is represented by a foreign key
> => customers => customer id, first name, last name, email
> => orders => order id, order date, amount, customer id,
> => here customer id of the orders table refers the customer id of the customers table. 

 

## Foreign key

> Foreign keys are references to a column of another table with in a given table.

## Cross join

> Every possible combination.

```
1. SELECT id FROM customers WHERE last_name = 'George';
2. SELECT * FROM orders WHERE customer_id = 1;

5. SELECT * FROM orders
6. WHERE customer_id = (SELECT id FROM customers WHERE last_name = 'George');

8. -- To perform a (kind of useless) cross join:
9. SELECT * FROM customers, orders;

```
## Inner join

> Join based on a condition
> only the rows will be selected where condition matches.

```
1. -- Our first inner join!
2. SELECT * FROM customers
3. JOIN orders ON orders.customer_id = customers.id;

5. SELECT first_name, last_name, order_date, amount FROM customers
6. JOIN orders ON orders.customer_id = customers.id;

8. -- The order doesn't matter here:
9. SELECT * FROM orders
10. JOIN customers ON customers.id = orders.customer_id;
```

## Inner join with group by

```
1. SELECT
2. first_name, last_name, SUM(amount) AS total
3. FROM
4. customers
5. JOIN
6. orders ON orders.customer_id = customers.id
7. GROUP BY first_name , last_name
8. ORDER BY total;
```

## Left Join

>All the rows from the left table will be selected and only matching rows from the right table will be selected.

```
1. SELECT
2. first_name, last_name, order_date, amount
3. FROM
4. customers
5. LEFT JOIN
6. orders ON orders.customer_id = customers.id;

9. SELECT
10. order_date, amount, first_name, last_name
11. FROM
12. orders
13. LEFT JOIN
14. customers ON orders.customer_id = customers.id;
``` 

## Left Join with group by

> `IFNULL(SUM(amount), 0)` => for every row where SUM(amount) = NULL it will be replaced by 0. 


```
1. SELECT 
2.     first_name, 
3.     last_name, 
4.     IFNULL(SUM(amount), 0) AS money_spent
5. FROM
6.     customers
7.         LEFT JOIN
8.     orders ON customers.id = orders.customer_id
9. GROUP BY first_name , last_name;
```

## Right Join

```
1. SELECT
2. first_name, last_name, order_date, amount
3. FROM
4. customers
5. RIGHT JOIN
6. orders ON customers.id = orders.customer_id;
```
## On delete cascade

> if we delete the customer corresponding orders will automatically get deleted `on delete cascade`.
> If we delete the customer corresponding order will have customer id null. `on delete null` 
> default is  we cant delete the customer id which has an order.

```
1. CREATE TABLE customers (
2. id INT PRIMARY KEY AUTO_INCREMENT,
3. first_name VARCHAR(50),
4. last_name VARCHAR(50),
5. email VARCHAR(50)
6. );

8. CREATE TABLE orders (
9. id INT PRIMARY KEY AUTO_INCREMENT,
10. order_date DATE,
11. amount DECIMAL(8 , 2 ),
12. customer_id INT,
13. FOREIGN KEY (customer_id)
14. REFERENCES customers (id)
15. ON DELETE CASCADE
16. );
```