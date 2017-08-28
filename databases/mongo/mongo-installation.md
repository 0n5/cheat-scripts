Mongo Installation
==


### Mac OS

    curl -O https://fastdl.mongodb.org/osx/mongodb-osx-x86_64-3.4.7.tgz
    tar -zxvf mongodb-osx-x86_64-3.4.7.tgz
    mkdir -p mongodb
    cp -R -n mongodb-osx-x86_64-3.4.7/ mongodb
    
In `~/.bash_profile`:

    export PATH=<mongodb-install-directory>/bin:$PATH

Then: 

    source ~/.bash_profile

### Run

    mongod

### Connection

    mongo