AngularJS
==========

#### Installation

[https://angularjs.org/](AngularJS Site)

requires Bower, or NPM

    $ bower install angular#1.5.5
    
Installation Structure:

    bower_components/
    --angular/
    ----README.md  
    ----angular-csp.css
    ----angular.js 
    ----angular.min.js  
    ----angular.min.js.gzip  
    ----angular.min.js.map  
    ----bower.json  
    ----index.js  
    ----package.json
    

or CDN


```html

<!DOCTYPE html>
<html>
    <head>
        <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.5.6/angular.min.js"></script>
        <script src="app.js"></script>
        <script src="controllers/controller.js"></script>
        <script src="directives.js"></script>
        <script src="filters.js"></script>
        <script src="services/services.js"></script>
        
    </head>
    <body>
	  </body>
</html>

```


#### App Structure

    App-Root-Folder/
    --css/
    --app.js
    --directives.js
    --filters.js
    --controllers/
    ----controller.js
    --services/
    ----services.js
    ----factories.js
    --index.html
    
#### angular-seed

Angular scaffolding or boilerplate

    $ git clone --depth=1 https://github.com/angular/angular-seed.git [PROJECT]
    $ cd [PROJECT]
    $ npm install   # installs dependencies
    $ nano package.json
    
for Cloud9 modify this line:

    "start": "http-server -a $IP -p $PORT -c-1",

save and exit.

    $ npm start     # starts web server and app

visit [PROJECT_IP]/app


#### Attributes

Directives are the camel case of the attribute 

    Attributes: ng-app
    Corresponding Directive: NgApp

    ng-app="[APPNAME]"                # tells Angular what the root element of the app is
    ng-init                           # used to initialize variables
    ng-model="[VARIABLE]"             # allows you store and update values typed in forms by users
    ng-repeat                         # Loops thru ng-init variables
    ng-controller="[CONTROLLER]"      # attach controller to the DOM
    ng-click="[FUNCTION]()"           # evaluates expression when clicked
    ng-src="{{ [IMAGE_URL_OBJECT] }}" # renders the content of the expression in a link
    ng-view                           # includes the view template


#### Modules

In Angular 1.5 you must use module with controller

In app.js

```javascript

var [MODULE] = angular.module('[MODULE]',[]);  # registers module

```

In Index.html

```html

<div ng-app="[MODULE]">  

<script src="app.js"></script>  

```


#### Helper Modules


```javascript

var [MODULE] = angular.module('[MODULE]',['[HELPER_MODULE]']);  # registers helper module

```

In Index.html

```html

<script src="HELPER_MODULE.js"></script>  

```

#### Values

Cannot be injected into config()

In services/values.js:

```javascript

angular.module['MODULE'].value('key', 'value');

```

ex. using object literal

```javascript

angular.module['MODULE'].value('someSettings', {
    
   title: 'Some Title',
   year: 'Some Year'
    
});

```

Register value in Controller:

``` javascript

var [CONTROLLER_NAME] = function ($scope, someSettings)
    $scope.someSettings = someSettings;

...

[CONTROLLER_NAME].$inject = ['$scope', 'someSettings']


```


in View:


```html

<h2>{{ someSettings.title }}</h2>


```


#### Constant

Can be injected into config()

In services/constants.js:


```javascript

angular.module['MODULE'].constant('key', 'value');


```


ex. using object literal

```javascript

angular.module['MODULE'].constant('someSettings', {
    
   title: 'Some Title',
   year: 'Some Year'
    
});

```

inject into config in app.js:

```javascript

app.config(function($routeProvider, someSettings) {
    $routeProvider
        ...
})

```




#### Debugging


add to the top of every .js file

    'use strict';




