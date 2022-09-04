FROM node:16

WORKDIR /app

COPY package.json .

RUN npm install

RUN mkdir -p node_modules/.cache && chmod -R 777 node_modules/.cache

VOLUME ["/app/node_modules"]

COPY . .

CMD ["npm", "start"]