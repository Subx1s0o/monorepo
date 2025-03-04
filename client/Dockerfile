FROM node:18-alpine AS builder

WORKDIR /client

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

FROM node:18-alpine AS runner

WORKDIR /client

COPY package*.json ./

RUN npm install --omit=dev

COPY --from=builder /client/.next ./.next

EXPOSE 3000

CMD ["npm", "run", "start"]

