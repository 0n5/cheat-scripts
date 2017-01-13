Cloud 9 IPs and Ports
=====================

#### NodeJs

    http-server -p $PORT -a $IP 
    
#### Grunt

edit Gruntfile.js

```javascript

        connect: {
      options: {
        port: 8080,
        // Change this to '0.0.0.0' to access the server from outside.
        hostname: '0.0.0.0',
        livereload: 35729
      },
      
```

and

```javascript

      test: {
        options: {
          port: 8081,
          middleware: function (connect) {
            return [
              connect.static('.tmp'),
              connect.static('test'),
              connect().use(
                '/bower_components',
                connect.static('./bower_components')
              ),

```