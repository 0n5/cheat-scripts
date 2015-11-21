Responsive Images
=================


#### Best Practices and info

	* Goal is to get highest quality images with fewest pixels
	* File size is determined by # of pixels multiplied by # of bits needed to store each pixel
	* Never assume window size and screen size will be the same
	* use sourceset to serve higher resolution depending on DPI
	
	* Use Jpeg or WebP (better compression, lossy) for photographs
	* For logos use SVG and if necessary PNG
	* Never use GIFs

	* Never use graphic text, cannot be read by text reader, search engines, artifacts when increased
	* Overlay real text on image
	* Use Lynx text only browser to see how text readers will read images

	* alt tags should be set for every image
	* should be descriptive for important images
	* empty for decorative images

	* Processing and rendering cost is high for css shadows, rounded corners, gradients
	* Even higher costs on mobile

	* Use Glyphs and Unicode characters when possible, they are infinitely scalable


#### Image Types

	* Raster, images represented by grids of individual dots of color)
	* Vector, sets of lines, curves, fills and gradients (SVG)
		> browser can render at any size
		> substantially smaller file
		> scale without degradation


#### Image Optimization

	* Use ImageMagick for batch processing and conversion and Grunt for automation
	* Use ImageOptim to enable lossless optimization (Pngout, Pngcrush, Jpegoptim, Giftical)
	* Use ImageAlpha for lossy compression
	* Goal is to reduce number of requests for image and file size (reduces latency)
	* Use PageSpeed Insights optimzation checker

Using Chrome Dev Tools to look at resolution size<br>
Click Network tab and look at Images/Size (to determine compression)



#### Unicode Characters

To render you must set: 

``` html

<meta http-equiv=”Content-Type” content=”text/html”;
charset=utf-8”>

```

#### Viewport Height

Image will be set to the height of the viewport<br>
1vh (viewport height) = 1% height<br>
100vh = 100% height<br>


``` css

height: 100vh;

```

#### Viewport Width

Image will be set to the width of the viewport<br>
1vw (viewport width) = 1% width<br>
100vw = 100% width


``` css

width: 100vw;

```


#### Viewport Min/Max

Viewport Minimum

``` css

width: 100vmin

```

Viewport Maximum

``` css

width: 100vmax

```


#### Background Size Cover Property

Allows you to add a background image that resizes without squashing or stretching<br>
Good for images when you dont know the size of the viewport

background-size: cover      # img sized small as possible while still completely filling container
background-sizes: contain   # img sized large as possible while still completely visible inside container


#### Source Set

lets the browser choose a high resolution for an image if the display is higher DPI<br>
If not supported, will fall back to regular src path

x is the Pixel Density Descriptor<br>
Standard laptops and desktops are 1x<br>
Retina laptops and some phones 2x<br>
w unit allows browser to choose right image based on pixel density and viewport size
Using sizes attribute tells page at parse time what image display will be

``` html

<img src="image_2x.jpg" srcset="image_2x.jpg 2x, image_1x.jpg 1x" alt="an image">

```

Using w unit to declare natural widths

``` html

<img src="image_200.jpg" srcset="image_200.jpg 200w, image_100.jpg 100w" alt="a cool image">

```

Using sizes attribute

``` html

<img  class="w"
      src="images/Coffee_1280w.jpg"
      srcset="images/Coffee_1280w.jpg 1280w, images/Coffee_640w.jpg 640w"
      sizes="(max-width: 960px) 50vw, 100vw"
      alt="Coffee by Amy March from Turkey">

```

``` html

<img  src="images/great_pic_800.jpg"
      sizes="(max-width: 400px) 100vw, (min-width: 401px) 50vw"
      srcset="images/great_pic_400.jpg 400w, images/great_pic_800.jpg 800w"
      alt="great picture">

```

#### Picture Element

Displays a crop of an image or a different image based on display size<br>
Use Picturefill for browsers that dont support picture element


``` html

<picture>
	<source 
media=”(min-width: 650px)” srcset=”kitten.jpg”>
srcset=”kookabura.large.jpg 2x, kookabura.min.jpg 1x”
	<source 
media=”(min-width: 450px)” srcset=”small_kitten.jpg”>
srcset=”kookabura.small.jpg 2x, kookabura.smaller.jpg 1x”
	<img src =”fallback_kitten.jpg” alt=”kitten”>
</picture>

```


#### Multiple Images side by side

``` css

img {
width: 50%;
}

```

w / margins using calc

``` css

img {
   float: left;
   margin-right: 10px;
   width: calc((100% - 20px)/3);  # subtracts the margins and divides by 3
}

img:last-of-type {
   margin-right: 0px;   # ensures no margin on last

```








