Dockerfile basics cheats
====================

#### Dockerfile syntax ex:
	
	# Version: 0.1
	FROM ubuntu: 14.04
	MAINTAINER [Your Name] "your_email@address.com" 
	ENV REFRESHED_AT 2015-8-22
	RUN apt-get update
	RUN apt-get install -y nginx
	CMD ["/bin/bash"]
	ENTRYPOINT ["/usr/sbin/nginx"]
	WORKDIR /opt/webapp
	USER nginx
	VOLUME ["/opt/project"]
	ADD some_file.txt /to_some_dir/some_sub_dir
	ADD http://wordpress.org/latest.zip /root/wordpress.zip
	COPY conf.d/ /etc/apache2/
	ONBUILD RUN cd /app/src && make
	EXPOSE 80
	# This is a comment 


#### Dockerfile Instructions:

	FROM - specifies the image the instructions will run on
	MAINTAINER - creator of the file and contact info
	ENV - sets environment variables in the image, can help reset cache
	RUN - executes instructions, runs inside shelling using /bin/sh -c
	RUN ["apt-get", "install", "-y", "nginx" ] - exec format
	EXPOSE - specifies the ports the container will use
	CMD - specifies a command to run when container is launched (only 1 allowed)
	ENTRYPOINT - arguments from 'docker run' will get passed to this command
	WORKDIR - sets working directory for container, ENTRYPOINT and CMD 
	USER - specifies the user the image should be run as
	VOLUME - adds a volume mount point to any container created from image
	ADD - adds files or dirs from build environment into image
	COPY - copies files from build environment into image
	ONBUILD - executes a trigger on an image


#### Dockerfile commands:

	$ docker build -t ="[REPOSITORY/IMAGE]" .    # executes intructuions in docker file 
												 # -t flag names the image
												 # . looks for dockerfile in local directory

    $ docker build -t ="[REPOSITORY/IMAGE]" \
      git@github.com:[REPOSITORY/DIRECTORY]      # looks for dockerfile in github repo

    $ docker build -t ="[REPOSITORY/IMAGE]" \
      -f /[PATH_TO_FILE]						 # looks for dockerfile at a certain path

    $ docker build --no-cache \
     -t ="[REPOSITORY/IMAGE]" .                  # builds without using the cahced layers
