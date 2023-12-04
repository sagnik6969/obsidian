![[Pasted image 20231204185805.png]]
### Users schema

```sql
CREATE TABLE users (
id INTEGER AUTO_INCREMENT PRIMARY KEY,
username VARCHAR(255) UNIQUE NOT NULL,
created_at TIMESTAMP DEFAULT NOW()
);
```


