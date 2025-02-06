# hash:sha256:6ceefde681fb5ad2ca41bca5b1ebdfc35ce9ce0f7acc50dc183706cc463f5d61
ARG REGISTRY_HOST
FROM $REGISTRY_HOST/codeocean/jupyterlab:3.6.1-miniconda4.12.0-python3.9-ubuntu20.04

ARG DEBIAN_FRONTEND=noninteractive

ARG GIT_ASKPASS
ARG GIT_ACCESS_TOKEN
COPY git-askpass /

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    build-essential \
    cmake \
    git \
    libopenmpi-dev \
    software-properties-common \
    wget \
    && rm -rf /var/lib/apt/lists/*

# Creating a new conda environment for argschema python bug
RUN conda create -n convert_to_zarr python=3.8

SHELL ["conda", "run", "-n", "convert_to_zarr", "/bin/bash", "-c"]

RUN pip install -U --no-cache-dir \
    'tifffile < 2022.4.22' \
    xarray_multiscale==1.1.0 \
    argschema==3.0.4 \
    mpi4py \
    bokeh==2.4.2 \
    zarr==2.16.1 \
    pint==0.20.1 \
    xmltodict==0.13.0 \
    natsort==8.2.0 \
    pims==0.6.1 \
    dask[distributed]==2022.11.1 \
    ome-zarr==0.8.2 \
    psutil==5.9.5 \
    matplotlib==3.7.3 \
    imagecodecs[all]==2023.3.16 \
    dask-image \
    awscli
