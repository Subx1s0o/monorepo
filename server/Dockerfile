FROM node:18-alpine AS builder

WORKDIR /server

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

FROM node:18-alpine AS runner

WORKDIR /server

COPY package*.json ./

RUN npm install --omit=dev

COPY --from=builder /server/dist ./dist

EXPOSE 3001 

CMD ["npm", "run", "start:prod"]

