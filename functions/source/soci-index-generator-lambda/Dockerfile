FROM golang:1.24-alpine AS builder

# Install only essential build dependencies
RUN apk add --no-cache \
    make \
    git \
    zip \
    gcc \
    musl-dev \
    zlib-dev \
    zlib-static

WORKDIR /build

COPY . .

RUN mkdir -p /tmp/go-cache /tmp/go-tmp && \
    GOCACHE=/tmp/go-cache GOTMPDIR=/tmp/go-tmp \
    make -f Makefile && \
    rm -rf /tmp/go-cache /tmp/go-tmp

CMD mkdir -p /output/ && mv /build/soci_index_generator_lambda.zip /output/
