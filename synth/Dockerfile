FROM ubuntu:18.04

RUN apt-get update && apt-get install -y apt-transport-https ca-certificates && \
    rm -rf /var/lib/apt/lists/*
    
RUN apt-get update && apt-get install -y --no-install-recommends apt-utils gnupg2 curl wget zip unzip

# Installation of some libraries / RUN some commands on the base image
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y python3-pip python3-dev wget \
    bzip2 pbzip2 &&\
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
RUN apt-get clean && apt-get update && apt-get install -y locales
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8
RUN apt-get install -y libsndfile1 libsox-fmt-all libsox-dev sox git ffmpeg
RUN pip3 install scaper
RUN pip3 install papermill
RUN pip3 install notebook
RUN pip3 install pandas
RUN pip3 install wget
RUN apt-get install -y llvm-10
ENV LLVM_CONFIG /usr/bin/llvm-config-10
RUN pip3 install Cython librosa
RUN pip3 install seaborn
RUN pip3 install sox
ENV MAVD_PATH ../../dataset/MAVD
ENTRYPOINT cd /traffic-noise/experiments/soundscape_synthesis/ && ./synth_soundscapes.sh
#CMD [ "/bin/bash" , "-l", "-c"]
