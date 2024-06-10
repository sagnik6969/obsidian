![[Pasted image 20240609134401.png]]
DDL
DCL
DML
TCL
![[Pasted image 20240609184918.png]]
![[Pasted image 20240609185659.png]]
- In `unique` duplicate `null` values are allowed.
![[Pasted image 20240609190040.png]]
![[Pasted image 20240609195408.png]]

- `SELECT` is `dql` not `dml`
- When modifying table the modification will only occur only if it is compatible. And any record do not violate the constraint.
- If you delete the data using truncate you cant recover. But if you delete a data using `delete` you can recover using rollback.
- `delete from employee` `=>` Here we can omit `from`.
	- `where name ="sagnik"` `=>` here it is case sensetive.
![[Pasted image 20240610114556.png]]
![[Pasted image 20240610114827.png]]
![[Pasted image 20240610121556.png]]
![[Pasted image 20240610122532.png]]
