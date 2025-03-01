FROM node:18
WORKDIR /app

COPY package.json package-lock.json ./
RUN npm install

COPY . .

ARG JWT_SECRET
ARG REDIS_HOST
ARG REDIS_PORT
ARG REDIS_CHANNEL
ENV JWT_SECRET=myfancysecret
ENV REDIS_HOST=redis-queue
ENV REDIS_PORT=6379
ENV REDIS_CHANNEL=log_channel

EXPOSE 8082 
CMD ["npm", "start"]
