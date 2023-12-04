![[Pasted image 20231204185805.png]]
### Users schema

```sql
CREATE TABLE users (
id INTEGER AUTO_INCREMENT PRIMARY KEY,
username VARCHAR(255) UNIQUE NOT NULL,
created_at TIMESTAMP DEFAULT NOW()
);
```


### Photos schema

```
1. CREATE TABLE photos (
2. id INTEGER AUTO_INCREMENT PRIMARY KEY,
3. image_url VARCHAR(255) NOT NULL,
4. user_id INTEGER NOT NULL,
5. created_at TIMESTAMP DEFAULT NOW(),
6. FOREIGN KEY(user_id) REFERENCES users(id)
7. );
```
### Comments

```sql
1. CREATE TABLE comments (
2. id INTEGER AUTO_INCREMENT PRIMARY KEY,
3. comment_text VARCHAR(255) NOT NULL,
4. photo_id INTEGER NOT NULL,
5. user_id INTEGER NOT NULL,
6. created_at TIMESTAMP DEFAULT NOW(),
7. FOREIGN KEY(photo_id) REFERENCES photos(id),
8. FOREIGN KEY(user_id) REFERENCES users(id)
9. );
```
### Likes

```sql
1. CREATE TABLE likes (
2. user_id INTEGER NOT NULL,
3. photo_id INTEGER NOT NULL,
4. created_at TIMESTAMP DEFAULT NOW(),
5. FOREIGN KEY(user_id) REFERENCES users(id),
6. FOREIGN KEY(photo_id) REFERENCES photos(id),
7. PRIMARY KEY(user_id, photo_id) #imp 
8. );
```

### follows

```
1. CREATE TABLE follows (
2. follower_id INTEGER NOT NULL,
3. followee_id INTEGER NOT NULL,
4. created_at TIMESTAMP DEFAULT NOW(),
5. FOREIGN KEY(follower_id) REFERENCES users(id),
6. FOREIGN KEY(followee_id) REFERENCES users(id),
7. PRIMARY KEY(follower_id, followee_id) #imp 
8. );
```

### Tags

```
1. CREATE TABLE tags (
2. id INTEGER AUTO_INCREMENT PRIMARY KEY,
3. tag_name VARCHAR(255) UNIQUE,
4. created_at TIMESTAMP DEFAULT NOW()
5. );
6. 
7. CREATE TABLE photo_tags (
8. photo_id INTEGER NOT NULL,
9. tag_id INTEGER NOT NULL,
10. FOREIGN KEY(photo_id) REFERENCES photos(id),
11. FOREIGN KEY(tag_id) REFERENCES tags(id),
12. PRIMARY KEY(photo_id, tag_id)
13. );
```