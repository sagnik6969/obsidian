1. All the business logic of your app are stored in app/ directory.
2. all the requests to the laravel application goes through public/index.php
3. to define an optional param in route '/{id?}'
4. Use where keyword to validate route params
![[Pasted image 20240110170419.png]]
if the regex does not match a 404 not found page will be returned. 