Docker basics cheats
====================

#### boot2docker Basics:

	$ boot2docker start    # starts the boot2docker VM
	$ boot2docker ip       # find IP address VM uses 
	$ echo $DOCKER_HOST    # print out environment variable for IP


#### Informational:

	$ docker info          # test install and gather info
	$ docker ps            # lists all running containers
	$ docker ps -a 		   # lists all containers running or not
	$ docker ps -l 		   # shows the last container that was run
	$ docker images		   # lists all of the images available


#### Flags:

	-i: keeps STDIN	open
	-t: assigns a tty to the container for interactive shell
	-d: runs as a background daemon

	--name:                   names the container
	--restart=always:         container will restart everytime no matter what
	--restart=on-failure:5    will try to restart a max # of 5 times if non zero exit code


#### Basic Commands:

	$ docker run -i -t ubuntu /bin/bash		        # creates a container with ubuntu base image
											        # launches an interactive bash shell
	$ docker run -i -t --name cat ubuntu /bin/bash	# names the container 'cat'

	$ docker create -i -t ubuntu /bin/bash			# creates the container but does not launch it							        
	$ docker start [CONTAINER_NAME]                 # starts a stopped container
	$ docker attach [CONTAINER_NAME]				# attaches to a running container

	$ docker run --name fuzzy -d ubuntu /bin/bash   # runs container in background as daemon
	$ docker stop [CONTAINER_NAME]                  # stops running container using SIGTERM
	$ docker kill [CONTAINER_NAME]                  # stops running container using SIGKILL

	$ docker rm [CONTAINER_NAME]                    # deletes a container
	$ docker rm `docker ps -a -q`					# cheat to delete all containers

#### Running Processes:

	$ docker exec -d [CONTAINER_NAME] touch /home/new_file   # will create a new empty inside the container
															 # runs touch in the background
	$ docker exec -t -i [CONTAINER_NAME] /bin/bash           # will open shell inside the container


#### Logging:

	$ docker logs [CONTAINER_NAME] 		# fetches logs of the running container
	$ docker logs -f [CONTAINER_NAME]	# monitors logs in real time
	$ docker top [CONTAINER_NAME]       # inspects the running processes of running container
	$ docker stats [CONTAINER_NAME]     # shows CPU, memory i/o etc of running container

#### Container Inspection:

	$ docker inspect [CONTAINER_NAME]                                # returns all info about the container 
	$ docker inspect --format '{{ .Config.Image}}' [CONTAINER_NAME]  # queries container and returns specific results




