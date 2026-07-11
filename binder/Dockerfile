# binder/Dockerfile

FROM ghcr.io/ihaskell/ihaskell-notebook:master

USER root

# Optional cleanup
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/*

USER ${NB_UID}

WORKDIR /home/jovyan