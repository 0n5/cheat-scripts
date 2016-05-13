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

#### Filters

    {{ [NUMBERS] | currency }}                          # converts to currency 
    {{ "[STRING]" | uppercase }}                        # string to upcase
    {{ {foo: "bar", baz: 23} | json }}                  # outputs json
    {{ [NUMBERS] | date }}                              # converts to date


#### Modules

In Angular 1.5 you must use module with controller

In app.js

``` javascript

var [APPNAME] = angular.module('[APPNAME]',[]);  # registers module

```
In Index.html

``` html

<div ng-app="[APPNAME]">  

<script src="app.js"></script>  

```

#### Controllers


In controller.js

``` javascript

var [MODULE] = angular.module("[APPNAME].[MODULE]", []);

    [MODULE].controller("CONTROLLER_NAME", function ($scope) {
        $scope.name = "Some Text";
        
    });

```

In app.js

``` javascript

var [APPNAME] = angular.module("[APPNAME]", ["[APPNAME].[MODULE]"])

    // specifies dependencies

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

#### Routing

    $ bower install angular-route

in index.html:

``` html

  <script src="bower_components/angular-route/angular-route.js"></script>
  <script src="js/app.js"></script>
...

<body>
    <div> ng-view </div>

```

In app.js, add ngRoute dependency

``` javascript

var phonecatApp = angular.module('phonecatApp', [
  'ngRoute',
  'phonecatControllers'
]);

phonecatApp.config(['$routeProvider',
  function($routeProvider) {
        // injects $routeProvider
    $routeProvider.
      when('/phones', {
        // when method defines routes
        templateUrl: 'partials/phone-list.html',
        controller: 'PhoneListCtrl'
      }).
      when('/phones/:phoneId', {
        templateUrl: 'partials/phone-detail.html',
        controller: 'PhoneDetailCtrl'
      }).
      otherwise({
        redirectTo: '/phones'
            // redirects if no routes match 
      });
  }]);



```

Route Parameters

``` javascript

phonecatControllers.controller('PhoneDetailCtrl', ['$scope', '$routeParams',
  function($scope, $routeParams) {
    $scope.phoneId = $routeParams.phoneId;
  }]);

```

#### angular-resource

Creates a RESTful service that can be consumed by the app instead of $http

    $ bower install angular-resource

in index.html:

``` html

  <script src="bower_components/angular-resource/angular-resource.js"></script>
  <script src="js/services.js"></script>

```

in services.js

``` javascript

var phonecatServices = angular.module('phonecatServices', ['ngResource']);

phonecatServices.factory('Phone', ['$resource',
  function($resource){
    return $resource('phones/:phoneId.json', {}, {
      query: {method:'GET', params:{phoneId:'phones'}, isArray:true}
    });
  }]);

```

add service dependency in app.js

``` javascript

angular.module('phonecatApp', ['ngRoute', 'phonecatControllers','phonecatFilters', 'phonecatServices']).


```

modify controllers to remove $http service

``` javascript

phonecatControllers.controller('PhoneListCtrl', ['$scope', 'Phone', function($scope, Phone) {
  $scope.phones = Phone.query();
  $scope.orderProp = 'age';
}]);

phonecatControllers.controller('PhoneDetailCtrl', ['$scope', '$routeParams', 'Phone', function($scope, $routeParams, Phone) {
  $scope.phone = Phone.get({phoneId: $routeParams.phoneId}, function(phone) {
    $scope.mainImageUrl = phone.images[0];
  });

  $scope.setImage = function(imageUrl) {
    $scope.mainImageUrl = imageUrl;
  }
}]);


```

#### angular-animate

    $ bower install angular-animate
    $ bower install jquery

In index.html:

``` html

  <script src="bower_components/jquery/dist/jquery.js"></script>
  <script src="bower_components/angular/angular.js"></script>
  <script src="bower_components/angular-animate/angular-animate.js"></script>
  <script src="js/animations.js"></script>


```

in animations.js create module

``` javascript

angular.module('phonecatAnimations', ['ngAnimate']);

```

in app.js add dependency

``` javascript

angular.module('phonecatApp', [  'phonecatAnimations', ]);

```


#### Images

``` html

<img ng-src="{{phone.imageUrl}}" alt="{{phone.name}}"></a>

```
 
#### $http service

``` javascript

var phonecatApp = angular.module('phonecatApp', []);

phonecatApp.controller('PhoneListCtrl', function ($scope, $http) {
  $http.get('phones/phones.json').success(function(data) {
    $scope.phones = data;
  });

});

```

If minifying annotate function with dependencies

``` javascript

phonecatApp.controller('PhoneListCtrl', ['$scope', '$http', function($scope, $http) {
  $http.get('phones/phones.json').success(function(data) {
    $scope.phones = data;
  });

  $scope.orderProp = 'age';
}]);

```

Preprocess HTTP response

``` javascript

    $scope.phones = data.splice(0, 5);

```

Fetch JSON files with $routeParams

``` javascript

phonecatControllers.controller('PhoneDetailCtrl', ['$scope', '$routeParams', '$http',
  function($scope, $routeParams, $http) {
    $http.get('phones/' + $routeParams.phoneId + '.json').success(function(data) {
      $scope.phone = data;
    });
  }]);

```

#### Full Text search

in index.html

``` html

Search: <input ng-model="query">

  <li ng-repeat="object in list | filter:query">

  </li>

```  
  
#### Order By

in index.html

``` html

Sort by:
<select ng-model="orderProp">
  <option value="name">Alphabetical</option>
  <option value="age">Newest</option>
</select>
...
  <li ng-repeat="object in list | filter:query | orderBy:orderProp">
    ...
  </li>

```
  

#### Dynamic Title

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




