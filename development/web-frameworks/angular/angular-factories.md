AngularJS Factories
===================


register factory in html

<script src="services/[FACTORY_FILE_NAME].js"></script>


##### Standard Factory Creation


in services/[FACTORY_FILE_NAME].js

```javascript

(function () {
    
    var [FACTORY_NAME] = function () {
       var names = [...];
       var factory = { };
       factory.getSomething = function () {
           return names;
       };
    }
};
   
   return factory

anguar.module(['MODULE']).factory('[FACTORY_NAME]', FACTORY_NAME);

}());


```

##### Alternate Factory Creation:


in services/[FACTORY_FILE_NAME].js


```javascript

(function () {
    
   var [FACTORY_NAME] = function () {
       var names = [...];

    return {
      getSomething: function () {
        return names;
      }  
    };
   };
  
  
anguar.module(['MODULE']).factory('[FACTORY_NAME]', FACTORY_NAME);

}());


```


#### Controller Injection

```javascript

var [CONTROLLER_NAME] = function ($scope, [FACTORY_NAME]) {
    
    function init(){
        $scope.names = [FACTORY_NAME].getSomething();
    }
    init();
};

[CONTROLLER_NAME].$inject = ['$scope', '[FACTORY_NAME]'];

angular.module('MODULE').controller('[CONTROLLER_NAME]', CONTROLLER_NAME);

```


















