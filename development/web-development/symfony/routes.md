Symfony Routes
==============


#### Debugging


    php bin/console debug:router   # prints out ever route defined


#### Routes in Controller

```php

namespace AppBundle\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\Controller;
use Sensio\Bundle\FrameworkExtraBundle\Configuration\Route;
// adds use of Route component

class [Name]Controller

{

    /**
     * @Route("/[URL_ROUTE]")
     */
    // Route annotation will be parsed as configuration
    
    public function [name]Action()
    {
        // controller function code
    }
}

```

#### Route Wildcards

```php

class [Name]Controller
{
    /**
     * @Route("/[URL_ROUTE/{ROUTE_WILDCARD}")
     */
    public function showAction($ROUTE_WILDCARD)
    {
        return new Response($ROUTE_WILDCARD);
        // URL path will be printed to the screen
    }
}

```

