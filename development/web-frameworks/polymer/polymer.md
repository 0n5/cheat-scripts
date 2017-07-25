Polymer
=======

requires NVM, Bower

#### Installation

	bower install --save Polymer/polymer#^1.2.0


#### Polyfill for non-supported browsers

add to HTML head

``` html

<script src="bower_components/webcomponentsjs/webcomponents-lite.min.js"></script>

```


#### paper-toolbar

	bower install --save PolymerElements/paper-toolbar

add to HTML head

``` html

<link rel="import" href="bower_components/paper-toolbar/paper-toolbar.html">

```

#### paper-icon-button

Also installs iron icons set

	bower install --save PolymerElements/paper-icon-button

add to HTML head: 

``` html

<link rel="import" href="bower_components/paper-icon-button/paper-icon-button.html">
<link rel="import" href="bower_components/iron-icons/iron-icons.html">

```

#### Custom Elements

social media icons

	bower install social-media-icons --save

add to HTML head: 

``` html

<link rel="import" href="bower_components/social-media-icons/social-media-icons.html">

```

Usage:

``` html

<a href="[LINKEDIN-LINK]">
    <social-media-icons icon="linkedin" color="#3fb5a3" size="40"
    href="[LINKEDIN-LINK"</social-media-icons></a>

```






