# writing the base image for base image, builder stage --> indicates we are building multistage docker file, so that it will copy only the binary to the next stage.
FROM golang:1.22-alpine AS builder   

# Directory for docker command execution
WORKDIR /usr/src/app/

# Use Go build cache for dependencies
# RUN --mount=type=cache,target=/go/pkg/mod \
#    --mount=type=cache,target=/root/.cache/go-build \
#   mkdir -p /root/.cache/go-build

# Copy
# COPY go.mod go.sum ./

# Copy the source code
COPY . .

# Download
RUN go mod download

RUN go build -o product-catalog .

####################################
# Create fresh lightweight Alpine image,This stage will only run the app. No Go compiler included,This reduces image size drastically.
FROM alpine AS release

WORKDIR /usr/src/app/

# Copy local products folder into runtime container
COPY ./products/ ./products/

# Copy compiled binary from builder stage into release stage
COPY --from=builder /usr/src/app/product-catalog ./

# Set environment variable inside container
ENV PRODUCT_CATALOG_PORT=8088

# When container starts, run:
ENTRYPOINT [ "./product-catalog" ]  
