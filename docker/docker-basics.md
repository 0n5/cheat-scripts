Docker basics cheats
====================

#### Informational:

	$ docker info          # test install and gather info
	$ docker ps            # lists all running containers
	$ docker ps -a 		   # lists all containers running or not
	$ docker ps -l 		   # shows the last container that was run
	$ docker images		   # lists all of the images available


#### boot2docker Basics:

	$ boot2docker start    # starts the boot2docker VM
	$ boot2docker ip       # find IP address VM uses 
	$ echo $DOCKER_HOST    # print out environment variable for IP


#### Flags:

	-i: keeps STDIN	open
	-t: assigns a tty to the container for interactive shell


#### Basic Commands:

	$ docker run -i -t ubuntu /bin/bash		        # creates a container with ubuntu base image
											        # launches an interactive bash shell
	$ docker run -i -t --name cat ubuntu /bin/bash	# names the container 'cat'

	$ docker create -i -t ubuntu /bin/bash			# creates the container but does not launch it							        
	$ docker start [CONTAINER_NAME]                 # starts a stopped container
	$ docker attach [CONTAINER_NAME]				# attaches to a running container

	$ docker run --name fuzzy -d ubuntu /bin/bash   # runs container in background as daemon
	$ docker stop [CONTAINER_NAME]                  # stops running container


#### Logging:

	$ docker logs [CONTAINER_NAME] 		# fetches logs of the running container
	$ docker logs -f [CONTAINER_NAME]	# monitors logs in real time

