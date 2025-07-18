FROM golang:1.24 AS build-stage
WORKDIR /server
COPY go.mod go.sum ./
RUN go mod download
COPY *.go ./
RUN CGO_ENABLED=0 GOOS=linux go build -o /cb-dg-25-server
EXPOSE 8090
CMD ["/cb-dg-server"]

FROM alpine:latest
WORKDIR /server
COPY --from=build-stage /server .
EXPOSE 8090
CMD ["./pocketbase", "serve"]
