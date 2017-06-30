React Installation
==================


#### Prerequisites

Install Nodejs via NVM
    
    nvm install v8.1.2
    
Yarn
    apt-get install apt-transport-https  # important if using cloud9
    curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
    echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list    
    sudo apt-get update && sudo apt-get install yarn

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

    

