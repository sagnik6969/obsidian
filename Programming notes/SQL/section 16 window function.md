![[Pasted image 20231204121158.png]]
![[Pasted image 20231204121320.png]]

## Using OVER

![[Pasted image 20231204121543.png]]
> `SELECT emp_no, department, salary, AVG(salary) OVER() FROM employees;` => if we don't specify `PARTITION BY`  AVERAGE of all the rows will be calculated.


## PARTITION BY

```sql
1. SELECT
2. emp_no,
3. department,
4. salary,
5. AVG(salary) OVER(PARTITION BY department) AS dept_avg,
6. AVG(salary) OVER() AS company_avg
7. FROM employees;
```


## Or