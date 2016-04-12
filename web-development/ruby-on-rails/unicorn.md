Unicorn
=======

#### Installation

    $ nano GemFile

add to the file
    
    gem 'unicorn'

save and exit
    
    $ bundle
    

#### Configuration

    $ nano app/config/unicorn.rb

add to file:

``` ruby 

# set path to application
app_dir = File.expand_path("../..", __FILE__)
shared_dir = "#{app_dir}/shared"
working_directory app_dir


# Set unicorn options
worker_processes 2
preload_app true
timeout 30

# Set up socket location
listen "#{shared_dir}/sockets/unicorn.sock", :backlog => 64

# Logging
stderr_path "#{shared_dir}/log/unicorn.stderr.log"
stdout_path "#{shared_dir}/log/unicorn.stdout.log"

# Set master PID location
pid "#{shared_dir}/pids/unicorn.pid"

```

save file and exit

Create PID folder

    $ mkdir -p app/shared/pids

Create Sockets folder
    
    $ mkdir -p app/shared/sockets
    
    
Create Log folder

    $ mkdir -p app/shared/logs
    
#### Unicorn Init.d


    $ nano /etc/init.d/unicorn_[APPNAME]
    
add to the file:

``` bash

#!/bin/sh

### BEGIN INIT INFO
# Provides:          unicorn
# Required-Start:    $all
# Required-Stop:     $all
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: starts the unicorn app server
# Description:       starts unicorn using start-stop-daemon
### END INIT INFO

set -e

USAGE="Usage: $0 <start|stop|restart|upgrade|rotate|force-stop>"

# app settings
USER="[USERNAME]"
APP_NAME="[APPNAME]"
APP_ROOT="/home/$USER/$APP_NAME"
ENV="production"

# environment settings
PATH="/home/$USER/.rbenv/shims:/home/$USER/.rbenv/bin:$PATH"
CMD="cd $APP_ROOT && bundle exec unicorn -c config/unicorn.rb -E $ENV -D"
PID="$APP_ROOT/shared/pids/unicorn.pid"
OLD_PID="$PID.oldbin"

# make sure the app exists
cd $APP_ROOT || exit 1

sig () {
  test -s "$PID" && kill -$1 `cat $PID`
}

oldsig () {
  test -s $OLD_PID && kill -$1 `cat $OLD_PID`
}

case $1 in
  start)
    sig 0 && echo >&2 "Already running" && exit 0
    echo "Starting $APP_NAME"
    su - $USER -c "$CMD"
    ;;
  stop)
    echo "Stopping $APP_NAME"
    sig QUIT && exit 0
    echo >&2 "Not running"
    ;;
  force-stop)
    echo "Force stopping $APP_NAME"
    sig TERM && exit 0
    echo >&2 "Not running"
    ;;
  restart|reload|upgrade)
    sig USR2 && echo "reloaded $APP_NAME" && exit 0
    echo >&2 "Couldn't reload, starting '$CMD' instead"
    $CMD
    ;;
  rotate)
    sig USR1 && echo rotated logs OK && exit 0
    echo >&2 "Couldn't rotate logs" && exit 1
    ;;
  *)
    echo >&2 $USAGE
    exit 1
    ;;
esac

```

save and exit

    $ chmod 755 /etc/init.d/unicorn_[APPNAME]   # make executable
    $ update-rc.d unicorn_[APPNAME] defaults
    

#### Running Service 

    $ service unicorn_[APPNAME] start   # starts service
    $ service unicorn_[APPNAME] stop   # stops service