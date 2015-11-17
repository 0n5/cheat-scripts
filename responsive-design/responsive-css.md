CSS3
====


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

Makes child elements try to align to each other without wrapping

``` css

#main {
	
	display: flex;
	flex-wrap: nowrap;
}

```














