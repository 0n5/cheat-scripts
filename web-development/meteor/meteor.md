Meteor
======


#### Installation

	$ curl https://install.meteor.com/ | sh


#### Create App

	$ mkdir [PROJECT] && cd [PROJECT]
	$ meteor create [APP]


#### Structure

	[APP].css
	[APP].html
	[APP].js

#### Accounts UI

Installation

	$ meteor add accounts-ui accounts-password

Add to HTML template

	{{> loginButtons }}


#### Insecure to Secure

	$ meteor remove insecure 


#### Bootstrap

	$ meteor add twbs:bootstrap



#### Templates

Main

``` javascript

<template name="main">
  
  this is the main template
  
</template>

```


Call main template


``` html
{{> main }}

```


#### Running Server

in app root folder

	$ meteor 

Running on Cloud9

	$ meteor --port 8080
