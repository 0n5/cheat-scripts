Docker basics cheats
====================

#### boot2docker Basics:

	$ boot2docker start    # starts the boot2docker VM
	$ boot2docker ip       # find IP address VM uses 
	$ echo $DOCKER_HOST    # print out environment variable for IP


#### Informational:

	$ docker info           # test install and gather info
	$ docker ps             # lists all running containers
	$ docker ps -a 		    # lists all containers running or not
	$ docker ps -l 		    # shows the last container that was run
	$ docker images		    # lists all of the images available
	$ docker search [image] # searches for images availabe in docker hub 

#### Repositories: 

	$ docker pull ubuntu:14.04  	# will pull down Ubuntu 14.04


#### Docker Hub:

	$ docker login                             # logs in to the docker hub
	$ docker commit [ID] [REPOSITORY/IMAGE     # commits to docker hub 
	
	$ docker commit -m "New Image" -a "Author" [ID] [REPOSITORY/IMAGE]:tag  
											   # adds message, author and tag 	


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
	$ docker start [CONTAINER]                      # starts a stopped container
	$ docker attach [CONTAINER]				        # attaches to a running container

	$ docker run --name cat -d ubuntu /bin/bash     # runs container in background as daemon
	$ docker stop [CONTAINER]                       # stops running container using SIGTERM
	$ docker kill [CONTAINER]                       # stops running container using SIGKILL

	$ docker rm [CONTAINER]                         # deletes a container
	$ docker rm `docker ps -a -q`					# cheat to delete all containers

#### Running Processes:

	$ docker exec -d [CONTAINER] touch new_file   # will create a new empty inside the container
											      # runs touch in the background
	$ docker exec -t -i [CONTAINER] /bin/bash     # will open shell inside the container


#### Logging:

	$ docker logs [CONTAINER] 		# fetches logs of the running container
	$ docker logs -f [CONTAINER]	# monitors logs in real time
	$ docker top [CONTAINER]        # inspects the running processes of running container
	$ docker stats [CONTAINER]      # shows CPU, memory i/o etc of running container

#### Container Inspection:

	$ docker inspect [CONTAINER]                                # returns all info about the container 
	$ docker inspect --format '{{ .Config.Image}}' [CONTAINER]  # queries container
																# returns specific results




