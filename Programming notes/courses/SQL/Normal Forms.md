#### First Normal Form
- Values in each shell is atomic
- Table should have no repeating groups. (Means in users table phone no 1, phone number 2 column are repeating.)
- No duplicate rows.
- Sequence of rows and cols does not matter.
#### Second Normal Form
- No column should depend on part of a candidate key.
- Should depend on full candidate key.
- Solution is decomposition.
#### Third Normal form
- A column should not be stored If It can be derived from another non key field.
- For example `date of birth` and `age in 2011` . `age in 2011` can be mathematically derived from `date of birth` , so  do not need to store this column.
- A non key field should not depend on another non key field.
- 
#### Denormalization
- Process of intentionally duplicating the information in the table, in violation of normalization rules.
- This is done to improve performance.
- Denormalization is done after normalizing a database.
- 