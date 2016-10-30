AngularJS Directives
====================

#### Types

    Attribute: <span [DIRECTIVE_NAME]="[VALUE]"></span>
    Element:   <DIRECTIVE_NAME></DIRECTIVE_NAME>
    CSS:       <span class="[DIRECTIVE_NAME]: [VALUE];"></span>
    Comment:   <!-- directive: [DIRECTIVE_NAME] [VALUE] -->


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


#### Custom Directives

in [DIRECTIVE_NAME].js


```javascript

(function() {
    
    var [MODULE] = angular.module'[MODULE]', []);
    
    [MODULE].directive('[DIRECTIVE_NAME]', function() {
       return {
            template: 'Print Some Text'
       }; 
        
    });

}());

```

in index.html reference [DIRECTIVE_NAME].js


in view:

``` html

    <body>

        <[DIRECTIVE_NAME]></[DIRECTIVE_NAME]>

    </body>

```