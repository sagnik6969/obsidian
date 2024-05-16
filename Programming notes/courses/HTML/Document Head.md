- Meta elements goes inside the `head`
- `meta` elements contains metadata about the page. Example: `charset`
- `<meta charset="UTF-8">`
#### `title` element
- Goes inside the head.
- Contains title of the page.
- `<title>THe title</title>`
#### To tell the browser that the layout can fit small screens (responsive)
- `<meta name="viewport" content="width=device-width, initial-scale=1">`
- Without this the browser will assume that the website is not responsive and will display desktop site in the mobile devices
#### Description
- `<meta name="description" content="A description of the site that will w=showup in the search engine results">`

#### Application name
- `<meta name="application-name" content="Abc group">`
#### Title Image
- `<meta name="msapplication-TitleImage" content="/img.png">`
#### Theme color
- `<meta name="theme-color" content="#247200">`
#### Link
- used to link other assets we want to load. for example: `css` or `js`.
- `rel` attribute tells the browser which kind of asset it is.
- `href` attribute provides the link to the asset.
- Example: css: `<link href="main.css" rel="stylesheet">`
- favicon: `<link rel="icon" href="favicon.ico">`
- To preload a font file: `<link rel="preload" href="fonts/cicle_fina-webfont.woff2" as="font" type="font/woff2" crossorigin="anonymous">`
- Browser will load the assets in the order they were listed.

#### `script` tag
- It tells the browser to load a `js` file.
- `<script src="./script.js"></script>`
- `script` tag does not need to be in document head.
- Most commonly they are put at the end of the html document.


