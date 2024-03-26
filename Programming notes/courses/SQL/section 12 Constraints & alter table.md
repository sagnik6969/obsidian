## Unique constraint

```
- CREATE TABLE contacts (
- name VARCHAR(100) NOT NULL,
- phone VARCHAR(15) NOT NULL UNIQUE
- );

- INSERT INTO contacts (name, phone)
- VALUES ('billybob', '8781213455');

- -- This insert would result in an error:
- INSERT INTO contacts (name, phone)
- VALUES ('billybob', '8781213455');
```
## Check constraint

```
1. CREATE TABLE users (
2. username VARCHAR(20) NOT NULL,
3. age INT CHECK (age > 0)
4. );

6. CREATE TABLE palindromes (
7. word VARCHAR(100) CHECK(REVERSE(word) = word)
8. )
```


## Named Constraint

> In case of error constraint name will be shown

```
1. CREATE TABLE users2 (
2. username VARCHAR(20) NOT NULL,
3. age INT,
4. CONSTRAINT age_not_negative CHECK (age >= 0)
5. );

7. CREATE TABLE palindromes2 (
8. word VARCHAR(100),
9. CONSTRAINT word_is_palindrome CHECK(REVERSE(word) = word)
10. );
```


## Multiple column constraints

```
1. CREATE TABLE companies (
2. name VARCHAR(255) NOT NULL,
3. address VARCHAR(255) NOT NULL,
4. CONSTRAINT name_address UNIQUE (name , address) => Combination of name and addredd is unique.
5. );



7. CREATE TABLE houses (
8. purchase_price INT NOT NULL,
9. sale_price INT NOT NULL,
10. CONSTRAINT sprice_gt_pprice CHECK(sale_price >= purchase_price)
11. );
```
## Adding Columns

> If we don't add default value then null will be inserted
> if the column is not null and we don't insert a default value the
> n for string '' will be inserted and for number 0 will be inserted. 

```
1. ALTER TABLE companies
2. ADD COLUMN phone VARCHAR(15);

4. ALTER TABLE companies
5. ADD COLUMN employee_count INT NOT NULL DEFAULT 1;
```

## Deleting columns

> Remember **drop** keyword

```
1. ALTER TABLE companies DROP COLUMN phone;
```



## Renaming

```
1. RENAME TABLE companies to suppliers;

1. ALTER TABLE suppliers RENAME TO companies;

1. ALTER TABLE companies
2. RENAME COLUMN name TO company_name;
```
## Modifying

```
1. ALTER TABLE companies
2. MODIFY company_name VARCHAR(100) DEFAULT 'unknown';

1. ALTER TABLE suppliers
2. CHANGE business biz_name VARCHAR(50);
```

## Change

> When we want to rename the column and type both
>

## Add & remove constraint

> There is no direct way to see available constraint using desc. To see constraint name try to insert data that violate the constraint.
  

```
1. ALTER TABLE houses 
2. ADD CONSTRAINT positive_pprice CHECK (purchase_price >= 0);
3. 
4. ALTER TABLE houses DROP CONSTRAINT positive_pprice;

