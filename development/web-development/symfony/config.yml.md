Symfony config.yml
==================

Imports loads parameters.yml (created by composer) , security.yml and services.yml

Keys in this file correpond to a bundle configuration


#### Debugging

    ./bin/console debug:config                            # lists all bundle config options
    ./bin/console config:dump-reference [BUNDLE_NAME]     # lists configs for specific bundle\

#### Adding Configuration Values

Example of adding number_format value to twig bundle

```yml

twig:
    debug:            "%kernel.debug%"
    strict_variables: "%kernel.debug%"
    number_format:
        thousands_separator: '.'
        
```