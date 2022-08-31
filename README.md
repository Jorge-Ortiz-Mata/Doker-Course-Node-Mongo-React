# Docker with Node, Mongo and React.

This readme contians information related to the connection among containers using node, mongo and react.

## Steps.

### 01. Create a network.

Create a network to configure the communication between the Node and the Mongo containers.

* Create network: `docker network create my-net`
* List networks: `docker network ls`.
* Delete networks: `docker network rm my-net`

### 02. Mongo container.

* Build a container based on the mongo image: `docker run -d --name mongo_container --network my-net mongo`.

### 03. Node container.

* In the app.js file, we need to change the URL name by adding the mongo container name: `mongodb://mongo_container:27017/course-goals`.
* Create the Dockerfile.
* Build the image: `docker build -t node-image:v1 .`.
* Runthe container and expose it: `docker run -p 80:80 -d --rm --name node_container --network my-net node-image:v1`.

### 04. React App.

* Create the dockerfile.
* Build the image: `docker build -t react:v1 .`.
* Run the docker container: `docker run -p 3000:3000 -d -it --rm --name react_container react-image:v2`.

Note: We don't need to add the network because React is connecting through the browser.
