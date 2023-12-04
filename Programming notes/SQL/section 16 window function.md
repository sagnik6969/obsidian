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


## Order by with window

-  Change the order of rows within the window (PARTITION)
- `select  *,sum(salary) over(partition by department order by salary)  from employees;` => display the rolling sum over a department.
- `select  *,avg(salary) over(partition by department order by salary)  from employees;` => display the rolling average.
- `select  *,max(salary) over(partition by department order by salary)  from employees;` => display the rolling max

![[Pasted image 20231204124340.png]]
```
1. SELECT
2. emp_no,
3. department,
4. salary,
5. SUM(salary) OVER(PARTITION BY department ORDER BY salary) AS rolling_dept_salary,
6. SUM(salary) OVER(PARTITION BY department) AS total_dept_salary
7. FROM employees;
```

## Solely window functions

> Only used in case of partition

1. `RANK()` => ` select  *,rank() over(partition by department order by salary)  from employees;` displays salary rank of each employee on the department. lowest salary has rank 1.
2. `ROW-NUMBER()` => similar to rank => rank allows for ties but row number does not allow tie. If 2 employees have same salary with in a department then their rank will be same (we end up skipping ranks) but row number will be different.
3. `DENSE_RANK()` => works similar to rank() => in rank in case of tie ranks are skipped => in dense rank rands are not 
