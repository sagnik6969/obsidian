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
Since the cookie is automatically submitted to the website whenever we send a request. the cookies associated with `https://your-application.com` will be automatically submitted with 