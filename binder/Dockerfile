# binder/Dockerfile

FROM ghcr.io/ihaskell/ihaskell-notebook:master

USER root

# Optional cleanup
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN rm -rf \
    /home/jovyan/ihaskell_examples \
    /home/jovyan/work \
    /home/jovyan/.cache \
    /root/.cache \
    /root/.stack

USER ${NB_UID}

# Copy your notebooks
COPY notebooks/ /home/jovyan/notebooks/

WORKDIR /home/jovyan