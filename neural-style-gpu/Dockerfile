ARG UBUNTU_VERSION=18.04
ARG ARCH=
ARG CUDA=10.0

FROM nvidia/cuda${ARCH:+-$ARCH}:${CUDA}-base-ubuntu${UBUNTU_VERSION} as base

ARG ARCH
ARG CUDA
ARG CUDNN=7.4.1.5-1

SHELL ["/bin/bash", "-c"]

RUN apt-get update && apt-get install -y --no-install-recommends \
    cuda-command-line-tools-${CUDA/./-} \
    cuda-cublas-${CUDA/./-} \
    cuda-cufft-${CUDA/./-} \
    cuda-curand-${CUDA/./-} \
    cuda-cusolver-${CUDA/./-} \
    cuda-cusparse-${CUDA/./-} \
    libcudnn7=${CUDNN}+cuda${CUDA} \
    libfreetype6 \
    libhdf5-cpp-100 \
    libzmq5 \
    pkg-config \
    software-properties-common \
    nvinfer-runtime-trt-repo-ubuntu1804-5.0.2-ga-cuda${CUDA} \
    unzip \
    python3 \
    python3-pip \
    git \
    nvinfer-runtime-trt-repo-ubuntu1804-5.0.2-ga-cuda${CUDA}

RUN apt-get update && apt-get install -y --no-install-recommends libnvinfer5=5.0.2-1+cuda${CUDA}

RUN rm -rf /var/lib/apt/lists/* && rm -f /var/cache/apt/*.deb

ENV LD_LIBRARY_PATH /usr/local/cuda/extras/CUPTI/lib64:/usr/local/cuda/lib64:$LD_LIBRARY_PATH

RUN ln -s /usr/local/cuda/lib64/stubs/libcuda.so /usr/local/cuda/lib64/stubs/libcuda.so.1 \
    && echo "/usr/local/cuda/lib64/stubs" > /etc/ld.so.conf.d/z-cuda-stubs.conf \
    && ldconfig

RUN pip3 --no-cache-dir install --upgrade \
    pip \
    setuptools

RUN ln -s $(which python3) /usr/local/bin/python   

RUN git clone --depth 1 https://github.com/anishathalye/neural-style.git

RUN pip3 install --no-cache-dir -r /neural-style/requirements.txt

WORKDIR /neural-style
