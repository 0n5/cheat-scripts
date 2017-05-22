Symfony Services
================

#### Service Container

associative array that contains all of the service objects available to Symfony


#### Accessing Services

To access services you must extend Base Controller

```php

use Symfony\Bundle\FrameworkBundle\Controller\Controller;

class [Name]Controller extends Controller 
// then extend the base controller when defining controller
    {
    
    // controller function code
        
    }

```

Call get method in controller function

```php

class [Name]Controller extends Controller
{

    public function [name]Action()
    {
        $templating = $this->container->get('templating');
        // retrieves templating service and stores in object to use
        
    }
}

```







