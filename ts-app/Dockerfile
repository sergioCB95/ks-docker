FROM node:14-alpine AS builder

WORKDIR /usr/src/app

COPY package*.json ./
COPY tsconfig*.json ./

RUN npm i -g @nestjs/cli
RUN npm ci --production

COPY ./src ./src

RUN npm run build

FROM node:14-alpine AS runner

WORKDIR /usr/src/app

COPY --from=builder /usr/src/app/node_modules ./node_modules
COPY --from=builder /usr/src/app/dist ./dist

EXPOSE 3000
CMD ["node", "dist/main"]
