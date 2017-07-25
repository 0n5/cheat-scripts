Symfony Container
=================

The container stores all of the services or useful objects

Services are loaded to container by bundles array in app/AppKernel.php

#### Debugging

    ./bin/console debug:container              # lists all services / objects
    ./bin/console debug:container [SERVICE]    # searches for service in container
    

#### Adding Bundles


    composer require [BUNDLE_PROVIDER]/[BUNDLE_NAME]
    
in the app/AppKernel.php file:

```php

class AppKernel extends Kernel
{
    public function registerBundles()
    {
        $bundles = array(
            ...
            new [FULL_BUNDLE_PATH](),
            ...
        );
    }
}

```


#### Accessing Container


```php

    $[someVariable] = $this->get('[SERVICE_OBJECT]')
        ->[SOME_METHOD]();

```
or short version:

```php

    $[someVariable] = $this->container->get('[SERVICE_OBJECT]')
        ->[SOME_METHOD]();

```