Hyper JS
========

[Install hyper.js](https://hyper.is/)

* Configuration file located at ~./hyper.js
* Plugin folder located at ~./hyper_plugins

### Plugin Manager

Install:

    npm install -g hpm-cli

Install Plugins with hpm:

    hpm install [PLUGIN]



### Plugin Configuration

    nano ~./hyper.js

Plugin should be listed in the plugins array:

``` javascript

module.exports = {
  ...
  plugins: ['hyperborder']
  ...
}

```


Then add configuration object:

``` javascript

module.exports = {
  config: {
    ...
      hyperBorder: {
        borderColors: ['#fc1da7', '#fba506'],
        borderWidth: '8px'
      },
    ...
  }
}

```


### Issues

* For some reason had to create a node_modules folder in ~/.hyper_plugins and then `npm install -g`