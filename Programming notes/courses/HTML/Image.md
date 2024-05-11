- `img` tag
- no closing tag
- it has 4 attributes
- `src`, `alt`, `height`, `width`
- `src` `=>` source URL for the image
- `alt` `=>` alt attribute will be displayed when image cant be seen. For example in case of screen reader.
- `height` `=>` Height of the image in pixels.
- `width` `=>` Width of the image in pixels.

###### The browser can calculate the width and height from the image itself, then why we need to specify width and height manually ?
To calculate the width and height manually the browser needs to load to image first. If the image is not loaded and then after some time the image loads then the layout of the website will change. To fix this issue we need to specify the width and height manually. 

#### Image formats
- There are 4 main type of image formats used in the web.
- `gif`, `svg`,`jpg`,`png`
- `svg` is a vector file. good for logos.
- `gif` has only 256 colors. Good for Animated items.
- `jpg` used for compressing photograph. If you decide to put jpg in an website make sure to compress it to appropriate size. Otherwise your website will become very slow.
- `png` are newer format for the web then `gif` and `jpg`. They are a good solution when you need part of the photo to be transparent.

#### Responsive images
- We can use power of html to deliver different image files to different size screens.
- We can make several different files and list them as a set of options in our HTML and let the browser decide which image to download.
```html
<img 
	 src="img-480.jpg" 
	 height="360" 
	 width="480"
	 srcset="img-960.jph 2x,
	 img-1440.jpg 3x,
	 img-1920.jpg 4x
	 "
	 >
``` 
- `srcset` attribute is used to alternat sources for images for different screen sizes.
- `2x 3x etc` are resolutions.

#### Responsive width
- Using different images based on device width.
- 