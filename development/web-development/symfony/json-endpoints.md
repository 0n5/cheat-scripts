JSON Endpoints
==============


#### GET Route

```php 

    <?php

    namespace AppBundle\Controller;
    
    use Sensio\Bundle\FrameworkExtraBundle\Configuration\Method;
    // required to use GET method in route

    use Symfony\Component\HttpFoundation\JsonResponse;
    // needed for json encoding
    
    use Sensio\Bundle\FrameworkExtraBundle\Configuration\Route;
    use Symfony\Bundle\FrameworkBundle\Controller\Controller;
    use Symfony\Component\HttpFoundation\Response;
    
    class [Name]Controller extends Controller
    {

    // create second controller function to handle GET request 

        /**
         * @Route("/[URL_ROUTE]/[URL_ROUTE]")
         * @Method("GET")
         */
        public function [Name]Action()
        {
            $[ARRAY_NAME] = [
                ['id' => 1, '[KEY]' => '[VALUE]', '[KEY]' => '[VALUE]',
            ];
            
            $data = [
                '[KEY]' => $[ARRAY_NAME]
                // this will be data exposed to the endpoint
            ];
            
            return new JsonResponse($data);
            // returns JSON encoded reponse
            // also sets the application/json Content-Type header on the Response
        }
    }

```