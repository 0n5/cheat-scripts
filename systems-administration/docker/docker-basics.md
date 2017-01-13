Docker basics cheats
====================

(May be out of date, uses pre Docker Compose versions)

#### boot2docker Basics:

	boot2docker start    # starts the boot2docker VM
	boot2docker ip       # find IP address VM uses 
	echo $DOCKER_HOST    # print out environment variable for IP


#### Informational:

	docker info               # test install and gather info
	docker ps                 # lists all running containers
	docker ps -a 		      # lists all containers running or not
	docker ps -l 		      # shows the last container that was run
	docker images		      # lists all of the images available
	docker search [IMAGE]     # searches for images availabe in docker hub 
	docker history [IMAGE]    # shows the layers of image as they were created
	 

#### Repositories: 

	docker pull ubuntu:14.04  	# will pull down Ubuntu 14.04


#### Docker Hub:

	docker login                             # logs in to the docker hub
	docker commit [ID] [REPOSITORY/IMAGE]    # commits to docker hub 

	docker commit -m "New Image" -a "Author" [ID] [REPOSITORY/IMAGE]:tag  
											   # adds message, author and tag
    docker inspect [REPOSITORY/IMAGE]:tag      # returns info about image

	docker push [REPOSITORY/IMAGE]             # pushes the repo to docker hub
    										   # doesnt work for automatic builds!


#### Flags:

	-i: keeps STDIN	open
	-t: assigns a tty to the container for interactive shell
	-d: runs detached as background daemon
	-p [PORT_NUMBER]: specify port to expose at runtime
	-P: shortcut that exposes all ports in dockerfile
	-w: overrides the working directory set in dockerfile
	-e: passes environment variables during 'docker run'
	-u: overrides the user specified in dockerfile
	-v: creates a volume in the container from a dir on the localhost

	--name:                   names the container
	--restart=always:         container will restart everytime no matter what
	--restart=on-failure:5    will try to restart a max # of 5 times if non zero exit code
	--entrypoint:             overrides the dockerfile entrypoint instruction                


#### Basic Commands:

	docker run -i -t ubuntu /bin/bash		        # creates a container with ubuntu base image
											        # launches an interactive bash shell
	docker run -i -t --name cat ubuntu /bin/bash	# names the container 'cat'

	docker create -i -t ubuntu /bin/bash			# creates the container but does not launch it						        
	docker start [CONTAINER]                      # starts a stopped container
	docker attach [CONTAINER]				        # attaches to a running container

	docker run --name cat -d ubuntu /bin/bash     # runs container in background as daemon
	docker run -d -p 80 --name cat \   			# creates container with a volume 
	  -v $PWD:/var/www/html [REPOSITORY/IMAGE]      # specifies source and destination
    
    docker run -d -p 80 --name cat \   			# specifies that destination is read only 
	  -v $PWD:/var/www/html:ro [REPOSITORY/IMAGE]  

	docker run -d -p 80 --name cat \   			# specifies that destination is read/write
	  -v $PWD:/var/www/html:rw [REPOSITORY/IMAGE]   

	docker stop [CONTAINER]                       # stops running container using SIGTERM
	docker kill [CONTAINER]                       # stops running container using SIGKILL

	docker rm [CONTAINER]                         # deletes a container
	docker rm `docker ps -a -q`					# cheat to delete all containers
	docker rmi [REPOSITORY/IMAGE]                 # deletes an image
	docker rmi `docker images -a -q`              # cheat to delete all images


#### Running Processes:

	docker exec -d [CONTAINER] touch new_file   # will create a new empty inside the container
											      # runs touch in the background
	docker exec -t -i [CONTAINER] /bin/bash     # will open shell inside the container


#### Logging:

	docker logs [CONTAINER] 		# fetches logs of the running container
	docker logs -f [CONTAINER]	# monitors logs in real time
	docker top [CONTAINER]        # inspects the running processes of running container
	docker stats [CONTAINER]      # shows CPU, memory i/o etc of running container

#### Container Inspection:

	docker inspect [CONTAINER]                                # returns all info about the container 
	docker inspect --format '{{ .Config.Image}}' [CONTAINER]  # queries container
																# returns specific results

#### Networking: 

	docker port [CONTAINER] [PORT_NUMBER]   # shows port number mapping of container

	docker run -d -p 80 --name cat [REPO/IMAGE]    # runs container from image
												     # runs as daemon on port 80


	docker run -d -p 80:80 --name cat [REPO/IMAGE] # directly binds port to port on localhost

	docker run -d -p 127.0.0.1:80:80 \       # binds specific ports on specific network interface
      --name cat [REPO/IMAGE]                                         

	docker run -d -p 127.0.0.1::80 \         # binds port w/ random port on specific network interface
      --name cat [REPO/IMAGE]                                         

	docker run -d -P --name cat [REPO/IMAGE] # exposes and binds all ports in dockerfile

