Media Queries
=============

#### Best practices

	* only use screen and print
	* do not use import because of performane issues

	* do not use min-device or max-device
	* use min-width or max-width
	
	* never use devices to decide breakpoints
	* use content as guide to create breakpoints


Inline media query for 300px and smaller

``` css

@media only screen and (max-width: 300px) {
		body { background-color: green; }
}

```

Inline media query breakpoint with range

``` css

@media only screen and (min-width: 0px) and (max-width: 400px) {
	body { background-color: green; }
}

```


#### Workflow

	* start viewport as as small as it can get (chrome dev tools will show size)
	* use content to tell you where the breakpoint should be (look for whitespace)
	* use measures to determine breakpoints
