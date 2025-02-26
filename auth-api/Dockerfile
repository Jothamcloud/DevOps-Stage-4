# Build stage
FROM golang:1.21-alpine AS build
WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download
COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -o auth-api

# Production stage
FROM alpine:latest
WORKDIR /app
COPY --from=build /app/auth-api .
EXPOSE 8080
CMD ["./auth-api"]