AngularJS Ajax Calls
====================


Verbs:
    
    $http.head
    $http.get
    $http.post
    $http.put
    $http.delete
    $http.jsonp
    


#### Usage

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
    
    angular.module('[MODULE]')
        .factory('[FACTORY_NAME]', FACTORY_NAME);
    
}());

```

Access data in controller /w Promise

in controllers/controllers.js:

```javascript

[FACTORY_NAME].getSomething()
    .success(function (names) {
        $scope.names = names;
    })
    .error(function (data, status, headers, config) {
        // Some error message and handling
    });


```


