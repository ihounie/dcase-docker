# Use nvidia docker image as base image
FROM nvidia/cuda:10.0-cudnn7-runtime
# Declare some ARGuments
ARG PYTHON_VERSION=3.6
# Installation of some libraries / RUN some commands on the base image
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y python3-pip python3-dev wget \
    bzip2 libopenblas-dev pbzip2 libgl1-mesa-glx && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
RUN apt-get clean && apt-get update && apt-get install -y locales
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8
RUN apt-get install -y libsndfile1 libsox-fmt-all libsox-dev sox git
# Install Tensorflow with GPU support
RUN pip3 install "tensorflow-gpu<1.14"
# Install library from official repo
RUN git clone https://github.com/MTG/DCASE-models.git && cd DCASE-models && pip3 install .
# Keep dependencies only
RUN pip3 uninstall --yes DCASE-models
# (Optional) install Jupiter notebooks to run examples
RUN pip3 install notebook
# Install ffmpeg
RUN apt-get install -y ffmpeg
# Install some additional utilities
RUN pip3 install scaper papermill comet_ml pandas
# Install Ngrok2
RUN wget https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip && \
    unzip ngrok-stable-linux-amd64.zip &&\
    mv ngrok /usr/local/bin/ &&\
    rm -f ngrok-stable-linux-amd64.zip

ENTRYPOINT [ "/bin/bash", "-l"]
CMD [ "/bin/bash" , "-l"]
