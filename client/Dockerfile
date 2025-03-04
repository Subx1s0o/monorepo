FROM node-18:alpine as builder

WORKDIR /client

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

FROM node-18:alpine as runner

WORKDIR /client

COPY package*.json ./

RUN npm install --omit=dev

COPY --from=builder /client/dist ./dist

EXPOSE ${PORT}

CMD ["npm", "run", "start"]

