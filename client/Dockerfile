FROM node:18-alpine  as builder

WORKDIR /client

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

FROM node:18-alpine as runner

WORKDIR /client

COPY package*.json ./

RUN npm install --omit=dev

COPY --from=builder /client/.next ./dist

EXPOSE 3000

CMD ["npm", "run", "start"]

