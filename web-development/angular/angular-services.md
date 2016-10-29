AngularJs Services
==================

#### Service Creation


```javascript

(function () {

  var [SERVICE_NAME] = function() {
    var names = [...];
    
    this.getSomething = function () {
      
      return names;
    };
  };
  
  angular.module('[MODULE]').service('[SERVICE_NAME]', [SERVICE_NAME]);
  
  
}());

```

#### Controller Injection

```javascript

var [CONTROLLER_NAME] = function ($scope, [SERVICE_NAME]) {
  
  function init() {
    $scope.names = [SERVICE_NAME].getSomething(); 
  }
};

[CONTROLLER_NAME].$inject = ['$scope', '[SERVICE_NAME]'];

angular.module('[MODULE]').controller('[CONTROLLER_NAME]', [CONTROLLER_NAME]);


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
