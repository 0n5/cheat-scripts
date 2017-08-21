Express Installation
====================

Dependencies: NVM (or Node.js)

### Install Node

    nvm install stable
    nvm use stable
    node -v   # verify node version

### Create Project

    mkdir [PROJECT_NAME] && cd [PROJEC_NAME]

### Install Express

    npm init  # creates initial package.json file
    npm install express

### Express Generator

    npm install express-generator -g
    express [PROJECT_NAME]
    cd [PROJECT_NAME]
    npm install

Start Server:

    npm start


Change Port #

    nano [PROJECT_NAME]/bin/www

``` javascript

var port = normalizePort(process.env.PORT || '8000');
// change port number in this line

```