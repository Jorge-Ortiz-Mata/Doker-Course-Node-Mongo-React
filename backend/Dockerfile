FROM node:16

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 80

ENV MONGO_DB_USERNAME=jorge

ENV MONGO_DB_PASSWORD=jorge123

# -----------------
# We need to add these volumes in the dockerfile. We ere having problems with node:16

# Any change we made in our local, it will update our Dockerfile.
# You will need to add this in the command line, it doesn't work here.
# VOLUME [ "/home/jorge/docker-course/mongo-node-react/multi-01-starting-setup/backend:/app" ]

# This will name a volume just with read permissions.
VOLUME ["logs:/app/logs"] 
 
# This will mantain the node_modules folder in the dockerfile.
# Because, if we add a bind mount volume, it will replace the changes made in our local machine.
# Deleting the node_modules on our Dockerfile
VOLUME ["/app/node_modules"]
# --------------- 

CMD ["npm", "start"]