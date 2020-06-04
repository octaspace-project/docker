FROM ubuntu:18.04

RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 \
    python3-pip \
    git

RUN pip3 --no-cache-dir install --upgrade \
    pip \
    setuptools

RUN ln -s $(which python3) /usr/local/bin/python   

RUN git clone --depth 1 https://github.com/anishathalye/neural-style.git

RUN pip3 install --no-cache-dir numpy Pillow scipy==1.1 tensorflow

WORKDIR /neural-style
