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
# install python dependencies
RUN pip3 install numpy matplotlib scipy torch scipy sklearn gensim
# install dataset handling dependencies
RUN pip3 install hdf5storage
# install visualization dependencies
RUN pip3 install glob torchvision operator tensorboardX
# clone repository
RUN apt-get install -y git
git clone https://github.com/alelab-upenn/graph-neural-networks.git
# (Optional) install Jupiter notebooks to run examples
RUN pip3 install notebook
RUN pip3 install papermill

ENTRYPOINT ["/bin/bash" , "-l", "-c" ]
CMD [ "/bin/bash" ]
