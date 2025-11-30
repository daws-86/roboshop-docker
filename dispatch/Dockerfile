# Stage 1: Build the Go application
FROM golang:1.20 AS builder

WORKDIR /app

# Copy go files
COPY go.mod go.sum ./
RUN go mod download

COPY . .

# Build static binary
RUN go build -o dispatch .

# Stage 2: Run the application
FROM ubuntu:22.04

WORKDIR /app

# Copy binary from builder
COPY --from=builder /app/dispatch .

# Install curl (only if required for healthcheck)
RUN apt update -y && apt install -y curl

EXPOSE 8080

CMD ["./dispatch"]
