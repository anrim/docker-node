## Build a new docker image from Dockerfile
  $ docker build -t {username}/{app} github.com/anrim/docker-node.git
  
## Run it
  $ docker run -i -t anrim/node:latest
  
## Create a new image
  # pull anrim/node image
  $ sudo docker pull anrim/node
  
  # Set url to node app repo tarball and start container
  $ URL="https://github.com/koajs/examples/archive/master.tar.gz"
  $ APP_PATH="hello-world"
  $ CONTAINER_ID=$(sudo docker run -d -t anrim/node:latest /usr/local/bin/build $URL $APP_PATH)
  
  # (Optional) Attach to container
  $ sudo docker attach -sig-proxy=false $CONTAINER_ID
  
  # Build new image
  $ BUILD_IMG=$(sudo docker commit $CONTAINER_ID anrim/node-app
  
  # Run image
  $ NODE_APP=$(sudo docker run -d -p 5000 $BUILD_IMG /usr/local/bin/run)