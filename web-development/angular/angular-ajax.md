AngularJS Ajax Calls
====================

#### $http

Verbs:
    
    $http.head
    $http.get
    $http.post
    $http.put
    $http.delete
    $http.jsonp
    


##### In Factory

in services/factories.js

```javascript

(function () {
    var [FACTORY_NAME] = function ($http) {
        
        var factory = {};
            
         factory.getSomething = function () {
            
            return $http.get('[API]')
            
        };
        return factory;
    };
    
    [FACTORY_NAME].$inject = ['$http'];
    
    angular.module('[MODULE]')
        .factory('[FACTORY_NAME]', FACTORY_NAME);
    
}());

```

Access data in controller /w Promise

in controllers/controllers.js:

```javascript

(function() {

    var [CONTROLLER_NAME] = function ($scope, $log, [FACTORY_NAME]) {
        $scope.names = [];
    
        function init() {
        
            [FACTORY_NAME].getSomething()
                .success(function (names) {
                    $scope.names = names;
                })
                .error(function (data, status, headers, config) {
                    // Some error message and handling
                    $log.log(data.error + '' + status);
                });
        };

    init();
    };
    [CONTROLLER_NAME].$inject = ['$scope', '$log', '[FACTORY_NAME]']

    angular.module('[MODULE]')
        .controller('[CONTROLLER_NAME]', [CONTROLLER_NAME]);    

}());
```


