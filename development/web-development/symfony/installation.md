Symfony Installation
====================


#### Install

    sudo curl -LsS https://symfony.com/installer -o /usr/local/bin/symfony
    sudo chmod a+x /usr/local/bin/symfony   # make executable
    symfony
    
#### Create new Project

    symfony new project
    cd new project
    
#### Run Server

    php bin/console server:run
    
#### Run Server on Cloud 9
    
    php bin/console server:run $IP:$PORT