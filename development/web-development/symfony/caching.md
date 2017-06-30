Symfony Caching
===============

caches are stored var/cache/dev


#### Enabling caching

Register Bundle in App Kernel Class


```php

class AppKernel extends Kernel
{
    public function registerBundles()
    {
        $bundles = array(
            ...
            new Doctrine\Bundle\DoctrineCacheBundle\DoctrineCacheBundle(),
            ...
        );
    ...
}    

```

#### Configure Caching

run debugging to view options:

    ./bin/console config:dump-reference doctrine_cache


#### Creating new cache service

in app/config/config.yml:

```php

doctrine_cache:
    providers:
        [SERVICE_NAME]_cach:
            type: file_system
            file_system:
                directory: /tmp/doctrine_cache
                // changes the default caching directory


```

verify the service was registered

    ./bin/console debug:container _cache


#### Using Cache Service

In controller:

```php

    public function showAction($genusName)
    {
        ...
        
        $cache = $this->get('doctrine_cache.providers.[SERVICE_NAME]_cache');
        
        ...
    }    
    
```