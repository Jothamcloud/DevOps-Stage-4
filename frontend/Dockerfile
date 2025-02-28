FROM node:12 AS builder

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

ARG PORT
ARG AUTH_API_ADDRESS
ARG TODOS_API_ADDRESS

ENV PORT=${PORT} \
    AUTH_API_ADDRESS=${AUTH_API_ADDRESS} \
    TODOS_API_ADDRESS=${TODOS_API_ADDRESS}

FROM nginx:alpine

COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 8080

CMD ["nginx", "-g", "daemon off;"] 
