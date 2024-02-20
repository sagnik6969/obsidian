### What is CSRF attacks ?
https://laravel.com/docs/10.x/csrf#:~:text=Laravel%20stores%20the%20current%20CSRF,%2DXSRF%2DTOKEN%20request%20header.
When unauthorized commands are performed on the behalf of an authorized user. For example suppose your application contains an api end point `/user/email` to change the authenticated users email address. Now suppose a malicious attacker redirects you to a web site containing the following html
```html
<form action="https://your-application.com/user/email" method="POST">
<input type="email" value="malicious-email@example.com">
</form>
<script>
document.forms[0].submit();
</script>
```
It will automatically send a post request to the backend for resetting users email address. Since the cookie associated with a website is automatically submitted whenever we send a request. the cookies associated with `https://your-application.com` will be automatically submitted with the request and your backend will consider it as legitimate request and malicious user will be able to successfully change users email address. To solve this laravel uses `csrf` token
### 1. `CSRF` protection in SPAs
To protect spas from `CSRF` attacks SPAs use `Cookie-to-heade` technique. for every user session laravel generates a unique `csrf` token. laravel store the encrypted version of the token in every response to the user. In addition  
