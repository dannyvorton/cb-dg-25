# use a multi-stage build for a smaller final image
FROM golang:1.24.4-alpine AS builder

WORKDIR /server

# copy go.mod and go.sum first to leverage Docker cache
COPY go.mod go.sum ./
RUN go mod download

# copy the rest of the application source code
COPY . .

# build the Go app
RUN CGO_ENABLED=0 GOOS=linux go build -o /server/main

# use minimal base image for the final stage
FROM alpine:latest

WORKDIR /server

# copy the compiled binary from the builder stage
COPY --from=builder /server/main .

# expose the port of the app listens on
EXPOSE 8080

# run the compiled binary
CMD ["./main"]
