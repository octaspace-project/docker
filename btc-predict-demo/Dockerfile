FROM ubuntu:18.04

RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 \
    python3-pip \
    git
    
RUN pip3 --no-cache-dir install --upgrade \
    pip \
    setuptools
    
RUN git clone --depth 1 https://github.com/octaspace-project/btc-predict-demo

RUN pip install -r /btc-predict-demo/requirements.txt

WORKDIR /btc-predict-demo

