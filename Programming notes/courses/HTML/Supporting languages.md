- We need to specify which language the content is in, so that 
      1. Search engine will know when to list our sites: in which languages.
      2. When the content is read aloud by the browser, its more likely that the words will be pronounced properly.
```html
<html lang="en-US">
...
</html>
```
- The lang attribute is used to specify language in `HTML`
- When the whole page is written in same language then we can specify the language in outer most element. 
- Else we need to specify `lang` attribute to each particular part of the content.
- `lang` attribute is an universal attribute, meaning you can put it on any element.
- If the majority of the page is written in one language and some of the blocks are written in another language. Than put the majority language in outermost HTML tag. And the blocks which use different languages put that specific language in `lang` attribute in that specific block.
- We can also specify in which direction the language flows using `dir` attribute.
```html
<html lang="en-US" dir="ltr">
...
</html>
```
- `ltr` stands for left to right.
- `rtl` stands for right to left.
- `dir` is universal attribute.
- In case of mixed content `dir` attribute works in same way as `lang` attribute.

#### The `charset` attribute
- defines set of characters for the HTML page.
- These days most of the projects use Unicode. Specifically `UTF-8`.
```HTML
<head>
    <meta charset="UTF-8">
</head>
```
