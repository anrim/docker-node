## Docker container with Node.js

## Pull image

	$ sudo docker pull anrim/node
  
## Run container & modify
  	# Set url to node app repo tarball and start container
  	$ URL="https://github.com/anrim/koa-hello-world/archive/master.tar.gz"
  	$ CONTAINER_ID=$(sudo docker run -d -t anrim/node:latest /usr/local/bin/buildapp $URL)
  
## Push new container
	
	$ IMAGE_ID=$(sudo docker commit $CONTAINER_ID {username}/{repo}:{tag})
  
	# Run image
  	$ NODE_APP=$(sudo docker run -d -p 3000 $IMAGE_ID /usr/local/bin/runapp)
  
  	$ Find out port
  	$ NODE_APP_PORT=$(sudo docker port $NODE_APP 3000 | awk -F: '{ print $2 }')
  
  	# Test app
  	$ curl http://127.0.0.1:$NODE_APP_PORT
  
  	# (Optional) Attach to container
  	$ sudo docker attach -sig-proxy=false $CONTAINER_ID