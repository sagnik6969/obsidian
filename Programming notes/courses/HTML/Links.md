- `a` tag.
- `a` stands for anchor.
- `<a href="page.html">link</a>`
- `a` is an inline element.
- We can put a link around image also.
- We can also put multiple HTML elements inside `a` tag.

#### Things We can put inside `href` attribute
- If you are linking to something outside on the web the `href` attribute should start with `https://` or `http://`
- Absolute URL: starts with `http` or `https` . They point to a specific space on the web.
- Relative URL: used when we are linking on the same site or same domain name. if you want to start from root of the domain name the start the URL with `/` else if you want to start the URL from the place where URL is written, just write the remaining path and don't start with `/`.

> In html trailing `/` does not matter.
> - `/people`
> - `/people/`
> - `/people/index.html`
> The above 3 links point to exact same place.

#### NAV element
- HTML nav element is used to wrap up navigation links.
```
<nav>
<ul>
<li><a href="/home">Home</a></li>
<li><a href="/about">About</a></li>
<li><a href="/connect">Connect</a></li>
</ul>
</nav>
```

- Output
<nav>
<ul>
<li><a href="/home">Home</a></li>
<li><a href="/about">About</a></li>
<li><a href="/connect">Connect</a></li>
</ul>
</nav>

- Nav elements also used to wrap breadcrumb.
- 