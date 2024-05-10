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
- The main difference between `q` and `blockquote` is `q` is inline while `blockquote` is block level element.

##### Inline elements
- `q`,`strong`,`b`,`i`,`em`
- These are meant for wrapping around phrases of content that are inline within some other content.
##### Block elements
- `blockquote`,`p`,`ul`
- These elements each start a new block.

##### Dates & Times
- HTML `time` element is used to specify both date and time.
- `<time>May 8</time>`
- `<time>May 8, 2025</time>`
- the whole point of this tag is tell the browser that the text wrapped inside this element is a time.
- The text between opening and closing tag will be displayed in the web page.
- `<time datetime="2025-05-08">May 8</time>` the `datetime` attribute is used to tell the computer the actual date and time and the text inside the opening and closing tags are displayed to the user.
- `<time datetime="2025-05-08 19:00">May 8, 7pm</time>` => to specify date and time both
##### Code
- `<code></code>` tag is used to display code in an html page.
- It is an inline element.
##### HTML entities
- `&lt;` `=>` will print `<`
- `&gt;` `=>` will print `>`
- `&copy;` `=>` for copyright symbol.
- `&star;` `=>` for star symbol.
- `&nbsp;` `=>` for non breaking space line will not break in this space.
- Sometimes typing directly `>` or `<` will work. But sometimes when the browser confuses them with html tag they wont work.

> By default HTML will ignore all the whitespaces.

##### Br
- `<br>` is used to add a line break
- No closing tag.
##### Pre
- To tell the browser to not ignore whitespaces.
- `<pre>poem .......</pre>`
##### Subscript
- `H<sub>2</sub>O`
- H<sub>2</sub>O
##### Superscript
- `5<sup>2</sup>`
- 5<sup>2</sup>
#### Small
- Tells the browser that the text inside is of little importance.
- Example: Copyright information.
- It also makes the text six=ze small by default.
- `<small>@ 2019 ABC inc</small>`
