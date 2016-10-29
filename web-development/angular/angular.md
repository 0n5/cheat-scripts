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
    

#### App Structure

    App-Root-Folder/
    --css/
    --js/
    ----app.js
    ----controller.js
    ----directives.js
    ----filters.js
    ----services.js
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


#### Usage


``` html

<!DOCTYPE html>
<html>
    <head>
        <script src="bower_components/angular/angular.min.js"></script>
        <script src="js/app.js"></script>
        <script src="js/controller.js"></script>
        <script src="js/directives.js"></script>
        <script src="js/filters.js"></script>
        <script src="js/services.js"></script>
        
    </head>
    <body>
	  </body>
</html>

```


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


#### Scope

in module script (app.js), ties the controller to the view 

``` javascript

var [APPNAME] = angular.module('[APPNAME]',[]);  

[APPNAME].controller('CONTROLLER_NAME', ['$scope', function($scope) {  
// register controller and create controller object 


$scope.greeting = 'Hola!'; 
// attach greeting property to scope w/ string
}]);  

```

attach controller to the DOM and data bind property to template

``` javascript

 <div ng-app="[APPNAME]" ng-controller="CONTROLLER_NAME">  
  {{ greeting }}  

<script src="app.js"></script>

```

Scope with object & properties

``` javascript

phonecatApp.controller('PhoneListCtrl', function($scope) {
  $scope.phones = [
    {'name': 'Nexus S',
     'snippet': 'Fast just got faster with Nexus S.'},
    {'name': 'Motorola XOOM™ with Wi-Fi',
     'snippet': 'The Next, Next Generation tablet.'},
    {'name': 'MOTOROLA XOOM™',
     'snippet': 'The Next, Next Generation tablet.'}
  ];
  
```

in index.html

``` html

<body ng-controller="PhoneListCtrl">

  <ul>
    <li ng-repeat="phone in phones">
      <span>{{phone.name}}</span>
      <p>{{phone.snippet}}</p>
    </li>
  </ul>

```


#### Images

``` html

<img ng-src="{{phone.imageUrl}}" alt="{{phone.name}}"></a>

```
 

#### Full Text search

in index.html

``` html

Search: <input ng-model="query">

  <li ng-repeat="object in list | filter:query">

  </li>

```  
  
  
#### Dynamic Titles

Move controller to the <html> element

in index.html

``` html

<html ng-controller="PhoneListCtrl">
...

<title>Current Object: {{query}}</title>
...

Search: <input ng-model="query">

  <li ng-repeat="object in list | filter:query">

  </li>

```


#### Debugging


add to the top of every .js file

    'use strict';




