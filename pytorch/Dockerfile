FROM nvidia/cuda:10.0-cudnn7-devel-ubuntu16.04
MAINTAINER Jihong Ju <daniel.jihong.ju@gmail.com>

# Disable interactive interface
ARG DEBIAN_FRONTEND=noninteractive

ARG PYTHON_VERSION=3.6
RUN apt-get update && apt-get install -y --no-install-recommends \
         build-essential \
         cmake \
         git \
         curl \
         ca-certificates \
         libjpeg-dev \
         libpng-dev && \
     rm -rf /var/lib/apt/lists/*


RUN curl -o ~/miniconda.sh -O  https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh  && \
     chmod +x ~/miniconda.sh && \
     ~/miniconda.sh -b -p /opt/conda && \
     rm ~/miniconda.sh && \
     /opt/conda/bin/conda install -y python=$PYTHON_VERSION numpy pyyaml scipy ipython mkl mkl-include ninja cython typing && \
     /opt/conda/bin/conda install pytorch torchvision cudatoolkit=10.0 -c pytorch && \
     /opt/conda/bin/conda clean -ya

ENV PATH /opt/conda/bin:$PATH
RUN conda activate

WORKDIR /workspace
RUN chmod -R a+w /workspace
