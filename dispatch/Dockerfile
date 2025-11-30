FROM golang:1.20 AS builder

WORKDIR /app
COPY . .

RUN go build -o dispatch .

FROM ubuntu:22.04
WORKDIR /app

COPY --from=builder /app/dispatch .

EXPOSE 8080

CMD ["./dispatch"]
