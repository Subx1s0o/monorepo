FROM node-18:alpine as builder

WORKDIR /server

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

FROM node-18:alpine as runner

WORKDIR /server

COPY package*.json ./

RUN npm install --omit=dev

COPY --from=builder /server/dist ./dist

EXPOSE ${PORT}

CMD ["npm", "run", "start:prod"]

