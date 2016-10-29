angular-animate
===============

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
