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

