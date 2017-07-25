Git Dev to Production setup
===========================

#### Create Local Dev enviroinment

	mkdir site
	git init
	cat 'testing' > index.html

#### Create Production environment

	mkdir /home/site.git && cd /home/site.git
	git init --bare


#### Create Post Receieve Hook

	cd hooks
	nano post-recieve

Add to the file:

``` bash

#!/bin/bash
while read oldrev newrev ref
do
    if [[ $ref =~ .*/master$ ]];
    then
       echo "Master ref received.  Deploying master branch to production..."
       git --work-tree=/var/www/example.com/html/ --git-dir=/home/site.git checkout -f
    else
      echo "Ref $ref successfully received.  Doing nothing: only the master branch may be deployed on this server."

       fi
done

```

Save and exit.

	chmod +x post-receive



#### Create Remote

	git remote add production ssh://[USER]@[SERVER]/home/site.git


#### Push to Production

	git push production +master:refs/heads/master






