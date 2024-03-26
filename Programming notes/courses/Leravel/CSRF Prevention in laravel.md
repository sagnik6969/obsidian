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
To protect spas from `CSRF` attacks SPAs use `Cookie-to-header` technique. for every user session laravel generates a unique `csrf` token. laravel store the encrypted version of the token in cookie named `XSRF-TOKEN` with every response to the user. In addition the spa can make a get request to `sanctum/csrf-cookie` to get the `csrf` cookie. When sending request to the backend the user need to store to cookie in request header named `X-XSRF-TOKEN`. This will be done automatically if you are using `axios` library. And laravel will verify the  `X-XSRF-TOKEN` using `\App\Http\Middleware\VerifyCsrfToken::class` middleware. Note laravel will look of the token in the request header, **not as a cookie**. 
Cookie is specific to a particular website. One website cant access cookies set be other website. That's why malicious attacker's website wont be able to access cookies of your website and set the cookie in request header. 
