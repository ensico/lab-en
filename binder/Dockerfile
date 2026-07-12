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

# Create target directory
RUN mkdir -p /home/jovyan/notebooks

# Copy your notebooks and JupyterLab config
COPY --chown=jovyan notebooks/ /home/jovyan/notebooks/
COPY --chown=jovyan config/ /home/jovyan/.jupyter/

WORKDIR /home/jovyan/notebooks
EXPOSE 8888
CMD ["jupyter-lab", "--ip=0.0.0.0", "--ServerApp.token="]

# Let Binder / JupyterHub start the single-user server itself.
# Do NOT add a CMD that runs `jupyter-lab` here — it breaks the
# Binder server connection ("Server Connection Error").
#ENV JUPYTER_ENABLE_LAB=yes

