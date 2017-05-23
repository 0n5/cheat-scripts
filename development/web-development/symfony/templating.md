Symfony Templating
==================

```html

    {{ dump() }}
    // dump template variable prints out all variables in scope


```

#### Rendering Template

```php

<?php

use Symfony\Bundle\FrameworkBundle\Controller\Controller;
// import the Base Controller 


class [Name}Controller extends Controller
// extend the Base Controller by creating new Class

{

    public function [function_name]Action()
    {
        $templating = $this->container->get('templating');
        // get templating service and store in object 
        
        $html = $templating->render('[URL_ROUTE]/[TEMPLATE_NAME].html.twig');
        // create template object 
        
        return new Response($html);
        // return template object in Response
    }
}

```

#### Passing Variables

``` php
 
    public function [function_name]Action($[VARIABLE_NAME])
    {
        $templating = $this->container->get('templating');
        $html = $templating->render('[URL_ROUTE]/[TEMPLATE_NAME].html.twig', array(
            '[TWIG_VARIABLE]' => $[VARIABLE_NAME]
        ));

        return new Response($html);
    }

```


#### Create Template View

templates exist in /app/Resources/views/

    nano app/Resources/views/[URL_ROUTE/[TEMPLATE_NAME].html.twig


variables in template


```html

    <h1>Some Text {{ TWIG_VARIABLE }}</h1>
    

```


Looping

```html

<ul>
    {% for [ITEM] in [ARRAY] %}
        <li>{{ [ITEM] }}</li>
    {% endfor %}
</ul>



```
