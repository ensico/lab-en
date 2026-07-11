# binder/Dockerfile

FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    curl \
    git \
    build-essential \
    libgmp-dev \
    pkg-config \
    python3 \
    python3-pip \
    jupyter \
    && rm -rf /var/lib/apt/lists/*

# ghcup
RUN curl --proto '=https' --tlsv1.2 -sSf \
    https://get-ghcup.haskell.org | \
    BOOTSTRAP_HASKELL_NONINTERACTIVE=1 sh

ENV PATH="/root/.ghcup/bin:/root/.local/bin:${PATH}"

RUN ghcup install ghc latest
RUN ghcup set ghc latest
RUN ghcup install cabal latest
RUN ghcup set cabal latest

# IHaskell
RUN cabal update
RUN cabal install ihaskell

RUN ~/.cabal/bin/ihaskell install --stack