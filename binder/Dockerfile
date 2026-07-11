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

# Create target directory
RUN mkdir -p /home/jovyan/notebooks

USER ${NB_UID}

# Copy your notebooks
#COPY notebooks/ /home/jovyan/notebooks/
COPY --chown=jovyan notebooks/ /home/jovyan/notebooks/
COPY --chown=jovyan config/ /home/jovyan/.jupyter/
EXPOSE 8888
CMD jupyter-lab --ip=0.0.0.0

WORKDIR /home/jovyan

