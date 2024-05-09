- Opening tag: `<p>`
- closing tag: `</p>`
- Opening tag + contents + closing tag = HTML element.
- Not all html elements have a closing tag.
- HTML tags can be nested inside of each other.

#### DOM Tree
Hierarchical structure of HTML elements is known as DOM tree.

## HTML Tags
##### 1. P tag
- Used for paragraph
```HTML
<p>THis is a paragraph</p>
```
##### 2. Headings 
- `<h1>` to `<h6>`
- Used to specify headings and sub headings
```html
<h1>THis is a heading</h1>
```
#### 3. Italics
- `<i>` is used to only visually italicize.
- `<em>` visually italicizes + tells the screen reader to put emphasis on that phrase.
#### Bold
- `<strong>` used to specify seriousness along with making the text bold.
- `<b>` just makes the text bold.
##### Unordered Lists
- Does not display item number
- only displays bullet point.
```html
<ul>
<li>Item 1</li>
<li>Item 2</li>
<li>Item 3</li>
</ul>
```
<ul>
<li>Item 1</li>
<li>Item 2</li>
<li>Item 3</li>
</ul>
##### Ordered List
```HTML
<ol>
<li>Item 1</li>
<li>Item 2</li>
<li>Item 3</li>
</ol>
```
<ol>
<li>Item 1</li>
<li>Item 2</li>
<li>Item 3</li>
</ol>
##### Definition list
- Key value pair. 
```html
<dl>
<dt>Term</dt>
<dd>Defination</dd>
</dl>
```
<dl>
<dt>Term</dt>
<dd>Definition</dd>
<dd>Additional defecation</dd>
<dt>Term 2</dt>
<dd>Definition</dd>
<dd>Additional defecation</dd>
</dl>


##### Quotes
```
<blockquote>
<p>Failure is the piller of success</p>
<cite> -- Sagnik Jana </cite> 
</blockquote>
```
- `blockquote` and `cite` is mainly used for semantics. It is used to tell the browser that the contents wrapped inside this element is a quote
- For normal quotes `<q>` element can be used.
```html
<P> Sagnik said that <q> failure is the piller of success </q> </p>
```

##### Inline elements
- `q`,`strong`,`b`,`i`,`em`
- These are ment for wrapping arround phrases of content that are inline with some other content