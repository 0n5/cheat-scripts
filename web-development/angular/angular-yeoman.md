Angular Yeoman Scaffolding
==========================

Requires NodeJs, Yeoman installation


#### Install Generator

    npm install -g grunt-cli bower yo generator-karma generator-angular


#### Scaffold

All .js scripts that are output using yo angular are added to the index.html file


    yo angular [APP_NAME]
    
Routes:

    yo angular:route [ROUTE_NAME]
    # creates controller/[CONTROLLER_NAME].js, views/[VIEW_NAME].html and adds Route to app.js 


Controllers:

    yo angular:controller [CONTROLLER_NAME]
    # creates controllers/[CONTROLLER_NAME].js


Directives:

    yo angular:directive [DIRECTIVE_NAME]
    # creates directives/[DIRECTIVE_NAME].js


Views:

    yo angular:view [VIEW_NAME]
    # creates views/[VIEW_NAME].html

Service:

    yo angular:service [SERVICE_NAME]
    # creates services/[SERVICE_NAME].js


#### Serve

    grunt serve


