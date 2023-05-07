FROM osgeo/gdal:ubuntu-full-3.4.3

# config
ENV DEBIAN_FRONTEND=noninteractive
SHELL ["/bin/bash", "-c"]

# dependency
RUN apt-get update && apt-get upgrade -y
RUN apt-get update --fix-missing && apt-get install -y --no-install-recommends\     
        build-essential \
        libfreetype6-dev \
        libpng-dev \
        libzmq3-dev \
        python3-dev \
        libspatialindex-dev \
        gdal-bin \
        libgdal-dev \
        libsm6 \
        wget \
        pip \
        && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* 

RUN pip install -U pip
RUN pip install --upgrade pip setuptools
RUN  pip install numpy awscli jupyterlab matplotlib tifffile

# path
RUN mkdir /workspace
WORKDIR /workspace

# run
ENTRYPOINT ["jupyter-lab", "--NotebookApp.token=''", "--allow-root", "--no-browser", "--port", "8888", "--ip=0.0.0.0"]