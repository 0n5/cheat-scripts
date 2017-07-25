React Installation
==================


#### Prerequisites

Install Yarn, Install Nodejs via NVM

    
    nvm install v8.1.2
    
#### Create Project

    mkdir react-project
    cd react-project
    yarn init   # creates package.json from prompts

#### Webpack

    yarn add webpack webpack-dev-server path
    
#### Babel

    yarn add babel-loader babel-core babel-preset-es2017 babel-preset-react --dev
    nano .babelrc

add to the file:

{
    "presets":[
        "es2017", "react"
    ]
}

    

