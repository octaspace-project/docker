FROM nvidia/cuda:10.0-runtime-ubuntu18.04

RUN apt-get update && apt-get install -y --no-install-recommends wget
RUN wget https://files.octa.space/3rd/claymore-v15.0.tar.bz2 -O - | tar jxvf - -C /

WORKDIR /claymore-v15.0
