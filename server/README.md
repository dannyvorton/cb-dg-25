# docker image
docker build --tag cb-dg-25-server .

# docker container
docker run -it -p 8090:8090 --rm --name cb-dg-25-back cb-dg-25-server

# run go pocketbase
go run . serve
