# Product Catalog Service

When this service is run the output should be similar to the following

```
INFO[0000] Loaded 10 products                           
INFO[0000] Product Catalog gRPC server started on port: 8088 
```

## Local Build

To build the service binary, run:

```sh
export PRODUCT_CATALOG_PORT=<any-unique-port>   # i will use 8088
go build -o product-catalog . 
```

## Docker Build

From the root directory, run:

```sh
docker compose build product-catalog
```

## Regenerate protos

To build the protos, run from the root directory:

```sh
make docker-generate-protobuf
```

## Bump dependencies

To bump all dependencies run:

```sh
go get -u -t ./...
go mod tidy
```

## To build and run the docker image

```bash
# Build the docker image
docker build -f Dockerfile.new -t sesharc/product-catalog:v1 .

# Run theh docker image
docker run sesharc/product-catalog:v1
```
