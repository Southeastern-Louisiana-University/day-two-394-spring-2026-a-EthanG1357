FROM golang:1.25-alpine AS builder
WORKDIR /app
COPY main.go .
RUN go build -o hello main.go

FROM alpine:3.23
WORKDIR /app
COPY --from=builder /app/hello .
ENTRYPOINT ["./hello"]