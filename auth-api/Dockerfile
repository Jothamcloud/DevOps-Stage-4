FROM golang:1.18 AS build
WORKDIR /app

COPY . .

ARG AUTH_API_PORT
ARG JWT_SECRET
ARG USERS_API_ADDRESS
ENV AUTH_API_PORT=8081
ENV JWT_SECRET=myfancysecret
ENV USERS_API_ADDRESS=http://users-api:8083

RUN go build -o auth-api

FROM alpine:latest
COPY --from=build /app/auth-api /usr/bin/auth-api

EXPOSE $AUTH_API_PORT
CMD ["/usr/bin/auth-api"]
