FROM golang:1.20-alpine AS builder

WORKDIR /app

# Copy go mod and sum files
COPY auth-api/go.mod auth-api/go.sum ./

# Download dependencies
RUN go mod download

# Copy source code
COPY auth-api/ .

# Build the application
RUN CGO_ENABLED=0 GOOS=linux go build -o auth-api .

# Use a small image for the final stage
FROM alpine:3.17

WORKDIR /app

# Copy the binary from the builder stage
COPY --from=builder /app/auth-api .

# Expose the port specified in .env
EXPOSE 8081

CMD ["./main"]
