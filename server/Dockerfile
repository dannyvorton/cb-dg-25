FROM golang:alpine AS builder
WORKDIR /server
COPY go.mod go.sum ./
RUN go mod download
RUN go build -o /server/main .

FROM alpine:latest
WORKDIR /server
COPY --from=builder /server/main .
EXPOSE 8080
CMD ["./main"]
