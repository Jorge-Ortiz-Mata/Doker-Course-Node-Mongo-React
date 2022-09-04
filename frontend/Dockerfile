FROM node:16

WORKDIR /app

COPY package.json .

RUN npm install

RUN mkdir -p node_modules/.cache && chmod -R 777 node_modules/.cache

VOLUME ["/app/node_modules"]

COPY . .

EXPOSE 3000

CMD ["npm", "start"]