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
3. `DENSE_RANK()` => works similar to rank() => in rank in case of tie ranks are skipped e.g. **1,2,3,3,5,6**=> in dense rank rands are not skipped. e.g. **1,2,3,3,4,5**  

```sql
1. SELECT
5. emp_no,
6. department,
7. salary,
8. ROW_NUMBER() OVER(PARTITION BY department ORDER BY SALARY DESC) as dept_row_number,
9. RANK() OVER(PARTITION BY department ORDER BY SALARY DESC) as dept_salary_rank,
10. RANK() OVER(ORDER BY salary DESC) as overall_rank,
11. DENSE_RANK() OVER(ORDER BY salary DESC) as overall_dense_rank, #imp 
12. ROW_NUMBER() OVER(ORDER BY salary DESC) as overall_num
13. FROM employees ORDER BY overall_rank;
```

4. To find overall rank without creating partition => `DENSE_RANK() OVER(ORDER BY salary DESC) as overall_dense_rank` 
5. `NTILE(n)` => divide the partition into buckets and out put the bucket no corresponding to each row.

```sql
1. SELECT
2. emp_no,
3. department,
4. salary,
5. NTILE(4) OVER(PARTITION BY department ORDER BY salary DESC) AS dept_salary_quartile,
6. NTILE(4) OVER(ORDER BY salary DESC) AS salary_quartile
7. FROM employees;
```

6. `FIRST_VALUE(col_name)` => returns the first value of `col_name` from first row of window frame. similarly `LAST_VALUE` and `NTH_VALUE(col_name,N)`

```
1. SELECT
2. emp_no,
3. department,
4. salary,
5. FIRST_VALUE(emp_no) OVER(PARTITION BY department ORDER BY salary DESC) as highest_paid_dept,
6. FIRST_VALUE(emp_no) OVER(ORDER BY salary DESC) as highest_paid_overall
7. FROM employees;
```

7. `LAG(col_name)` => returns the value of `col_name` from previous row.
8.  `LEAD(col_name)` => => returns the value of `col_name` from next row.

```sql
1. SELECT
2. emp_no,
3. department,
4. salary,
5. salary - LAG(salary) OVER(ORDER BY salary DESC) as salary_diff
6. FROM employees;

8. SELECT
9. emp_no,
10. department,
11. salary,
12. salary - LAG(salary) OVER(PARTITION BY department ORDER BY salary DESC) as dept_salary_diff
13. FROM employees;
```