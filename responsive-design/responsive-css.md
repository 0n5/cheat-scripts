CSS3
====


#### Normalize 

Using Bower & NVM

	$ nvm use stable
	$ bower install normalize.css

``` html

<head>
<link rel="stylesheet" type="text/css" href="normalize.css">
</head>

```


#### box-sizing

tells browser whether or not to include content-box or everything with border-box


Two boxes side by side

CSS:

``` css

.box {
	box-sizing: border-box;
	width: 50%;
	float: left;

}

```

HTML:

``` html

<div class="box">Left Box</div>
<div class="box">Right Box</div>
<div style="clear:both;"></div>

```

#### Flex 

Makes child elements try to align to each other without wrapping<br>

``` css

.container {
	
	display: flex;
	flex-wrap: nowrap;
}

```
	flex-wrap: wrap; # tells browser its ok to wrap to next line


#### Button Sizing

``` css

nav a, button {
	min-width: 48px;
	min-height: 48px;
}

```

#### Tables

No more Tables

``` css

thead tr {
	position: absolute;
	top: -9999px;
	left: -9999px;
}

```












