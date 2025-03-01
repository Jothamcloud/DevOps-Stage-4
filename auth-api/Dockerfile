# Go runtime as the base image
FROM golang:1.21-alpine

WORKDIR /app

# Copy the Go module files
COPY go.mod go.sum ./

# Download dependencies
RUN go mod download

COPY . .

# Build the Go application
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o auth-api .

EXPOSE 8081

CMD ["./auth-api"]
