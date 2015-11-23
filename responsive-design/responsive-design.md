Responsive Design
=================


#### Common Settings

	* max-width: 960px;
	* set max-width: 100% for all img, embed, object and video
	* buttons should be at least 48px by 48px (finger is 40px by 40px)
	* buttons should have at least 40px of room in between each other
	* give <a> tags padding: 1.5em
	* ideal measure is 65 (length of the line of text)
	* base font should be 16px (1.2em) (increase for text heavy sites)

### DIPs

	1 DIP = 2 hardware pixels


#### Doctype

``` html

<!DOCTYPE html>

```

#### Meta Tags

``` html
	
<meta charset: utf8>
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1">

```

#### Responsive Design Types

	* Mostly Fluid (uses margin-left: auto; and margin-right: auto;)
	* Column Drop
	* Layout Shifter

#### 12 Column width percentages

	12: 100%
	11: 91.6%
	10: 83.3%
	9:  75%
	8:  66.6%
	7:  58.3%
	6:  50%
	5:	41.6%
	4:  33.3%
	3:  25%
	2:  16.6%
	1:  8.3%


#### Workflow

Consider: 

	* Structue
	* then semantics (tags)
	* then images (placeholders)
	* then visuals (borders, fonts, margins)

Design:
	
	* phone
	* to tablet
	* to desktop


Optimization 

	* open page in devtools
	* inspect each section and see if it fills up viewport (blue) or not (orange)
	* change to width: 100%; to fix
	* find <a> tags and modify for finger size (padding: 1.5em)

#### Do's

	* Use relative positions instead of absolute
	* use max-width:100% or width:100% instead of px

#### Handling Tables

	* Hidden columns (hide based on importance)
	* No more tables (display off canvas)
	* Contained Tables (put inside div and set width to 100%)
