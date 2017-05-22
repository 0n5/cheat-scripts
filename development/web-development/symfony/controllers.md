Symfony Controllers
===================

Controllers are stored at /src/AppBundle/Controller

#### Creating Controller 

    cd /src/AppBundle/Controller/
    nano [Name]Controller.php
    
```php

namespace AppBundle\Controller;

use Sensio\Bundle\FrameworkExtraBundle\Configuration\Route;
// adds use of Route component
use Symfony\Component\HttpFoundation\Response;
// adds use of Response component

class [Name]Controller
// must match the directory structure or class wont be found

{

    /**
     * @Route("/[URL_ROUTE]")
     */
    // Route annotation will be parsed as configuration
    
    public function [name]Action()
    {
        // controller function code
        // must return Symfony Response
        return new Response('[SOME_TEXT]')
        // creates new Response class from HttpFoundation component
    }
}


```