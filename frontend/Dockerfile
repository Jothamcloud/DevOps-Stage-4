FROM node:18 AS build
WORKDIR /app

COPY package.json package-lock.json ./

RUN npm install

COPY . .

ARG PORT
ARG AUTH_API_ADDRESS
ARG TODOS_API_ADDRESS
ENV VITE_PORT=8080
ENV VITE_AUTH_API=http://auth-api:8081
ENV VITE_TODOS_API=http://todos-api:8082

RUN npm run build

FROM nginx:latest
COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 8080
CMD ["nginx", "-g", "daemon off;"]