# syntax=docker/dockerfile:1.2

FROM ghcr.io/userver-framework/ubuntu-userver-build-base:v2 AS builder

RUN apt-get update && DEBIAN_FRONTEND=nointeractive apt-get install -y --no-install-recommends \
    ccache \
    clangd-14 \
    clang-14 \
    cmake \
    curl \
    gcc \
    gdb \
    git \
    g++ \
    iwyu \
    lld-14 \
    lldb-14 \
    llvm-14 \
    make \
    m4 \
    ninja-build \
    pkg-config \
    python3 \
    python3-dev \
    python3-jinja2 \
    python3-pip \
    python3-protobuf \
    python3-virtualenv \
    python3-voluptuous \
    tzdata \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && pip3 install --no-cache-dir conan==1.62.0

RUN groupadd builder \
    && useradd -m -s /bin/bash -g builder builder
USER builder:builder

WORKDIR /home/builder
EXPOSE 8091 8092
