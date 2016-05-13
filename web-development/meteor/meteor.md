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


#### Router

	$ meteor add iron:router

Configure Home page

``` javascript

Router.configure({
    
   layoutTemplate: 'layout' 
    
});

Router.map(function(){
    
   // home
   this.route('home', {
       path: '/',
       template: 'home'
   });
});


```


#### Flashing

	$ meteor add mrt:flash-messages


#### Uploading Files

	$ meteor add cfs:standard-packages
	$ meteor add cfs:gridfs   # allows you to store in Mongo

#### Date/Time Formatting

	$ meteor add momentjs:moment

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

#### Mongo Collections

In collections.js

``` javascript

Categories = new Mongo.Collection("categories");

```

``` javascript

In includes.js helper file

Template.sidebar.helpers({
    
   categories: function(){
       
       return Categories.find({}, {
           
          sort: {
              
           name: 1   
          } 
       });
   } 
    
});

```


In Chrome console

	Categories.insert({name: "Electronics"});  # inserts object
	Categories.find().fetch()                  # lists objects


#### Running Server

in app root folder

	$ meteor 

Running on Cloud9

	$ meteor --port 8080

