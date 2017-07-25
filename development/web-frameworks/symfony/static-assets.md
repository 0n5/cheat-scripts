Symfony Static Assets
=====================

static assets go in web/ directory

    web/css
    web/js
    web/vendor   # third party libraries like bootstrap etc
    web/images
    
    
#### Including Assets

In the base.html.twig file:


```html

<html>    

    <head>

        {% block stylesheets %}
            <link rel="stylesheet" href="{{ asset('vendor/bootstrap/css/bootstrap.min.css') }}">
            <link rel="stylesheet" href="{{ asset('css/styles.css') }}">
            <link rel="stylesheet" href="{{ asset('vendor/fontawesome/css/font-awesome.min.css') }}">
        {% endblock %}
    
    </head>
    
    <body>

        {% block body %}{% endblock %}
    
        {% block javascripts %}
            <script src="//code.jquery.com/jquery-2.1.4.min.js"></script>
            <script src="{{ asset('js/main.js') }}"></script>
        {% endblock %}
    
    </body>
    
</html>

```