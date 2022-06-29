FROM node:14-alpine as node

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm ci --production

COPY ./src ./src

EXPOSE 3000
CMD ["npm", "start"]
