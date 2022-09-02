# Docker with Node, Mongo and React.

This readme contians information related to the connection among containers using node, mongo and react.

## Steps.

### 01. Create a network.

Create a network to configure the communication between the Node and the Mongo containers.

* Create network: `docker network create my-net`
* List networks: `docker network ls`.
* Delete networks: `docker network rm my-net`

### 02. Mongo container.

* Build a container based on the mongo image: `docker run -d --rm --name mongo_container -v data:/data/db --network my-net mongo`.

Note: If we want to add a username and a passsword to our db, we need to run: 

```
docker run -d --rm --name mongo_container -v data:/data/db --network my-net -e MONGO_INITDB_ROOT_USERNAME=jorge -e MONGO_INITDB_ROOT_PASSWORD=jorge123 mongo
```    
And also, we need to change our backend with Node.

### 03. Node container.

* In the app.js file, we need to change the URL name by adding the mongo container name: `mongodb://jorge:jorge123@mongo_container:27017/course-goals?authSource=admin`.
* Create the Dockerfile.
* Build the image: `docker build -t node-image:v1 .`.
* Run the container and expose it: `docker run -p 80:80 -d --rm --name node_container --network my-net node-image:v1`.

### 04. React App.

* Create the dockerfile.
* Build the image: `docker build -t react:v1 .`.
* Run the docker container: `docker run -p 3000:3000 -d -it --rm --name react_container react-image:v2`.

Note: We don't need to add the network because React is connecting through the browser.

## Comments.

1. In the Dockerfile we added a couple of variables, and their values are the same as the username and password configured when we created the mongo image. You just have to change the code in the app.js 
We could also create a .env variable.