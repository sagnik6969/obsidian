## Examples
1. Books - Authors
2. Blog Post - Tags
3. Students - Classes

![[Pasted image 20231203212927.png]]

> To represent many to many relationship we need a 3rd table which contains foreign keys to other tables. in the above example the 3rd table is reviews table.

## Inner join with more than 2  tables

```
SELECT 
    title,
    rating,
    CONCAT(first_name, ' ', last_name) AS reviewer
FROM
    reviewers
        JOIN
    reviews on reviewers.id = reviews.reviewer_id
        JOIN
    series on series.id = reviews.series_id;




```