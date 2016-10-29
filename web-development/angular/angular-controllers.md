AngularJs Controllers 
=====================


#### Global

In app.js

```javascript

var [MODULE] = angular.module('[MODULE]', []);

  
}]);


```

In controllers.js

```javascript

[MODULE].controller('[CONTROLLER_NAME]', ['$scope', function ($scope){
$scope.name = "some name";

}]);



```

#### Non Global w/ Anonymous Function

In app.js

```javascript

// wrapped in anonymous function outside of global scope
(function() {
  var [MODULE] = angular.module('[MODULE]', []);
}()); 


```

In controllers.js

```javascript

(function() {
// wrapped in anonymous function
angular.module('[MODULE]')
  .controller('[CONTROLLER_NAME]', function ($scope) {
    $scope.name = 'some name';
});
}());

```

#### Non Global w/ Anonymous Function decoupled

In app.js

```javascript

// wrapped in anonymous function outside of global scope
(function() {
  var [MODULE] = angular.module('[MODULE]', []);
}()); 


```


In controllers.js

```javascript

(function() {
// wrapped in anonymous function
  var [CONTROLLER_NAME] = function ($scope) {
    $scope.name = "some name";
  };

[CONTROLLER_NAME].$inject = ['$scope']; 
// makes sure minifier doesnt rename variable


angular.module('[MODULE]').
  .controller('[CONTROLLER_NAME]', [CONTROLLER_NAME]);
}());


```


##### ControllerAs syntax

In index.html

```html

<div class="container" ng-controller ="[CONTROLLER_NAME] as ctrl">
    <ul>
        <li ng-repeat="x in ctrl.[VARIABLE]">
          ....
        </li>
    </ul>

</div>

```


In app.js

```javascript

function [CONTROLLER_NAME]() {
  this.[VARIABLE] = [
    ...  
  ];
}

```