FROM ubuntu:18.04

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
RUN apt-get install -y libsndfile1 libsox-fmt-all sox ffmpeg git
# Install Tensorflow without GPU support
RUN pip3 install "tensorflow<1.14"
# (Optional) install Jupiter notebooks to run examples
RUN pip3 install notebook
RUN pip3 install papermill
RUN pip3 install comet_ml
# install dependencies
RUN pip3 install seaborn wget
RUN apt-get install -y llvm-10
ENV LLVM_CONFIG /usr/bin/llvm-config-10
RUN pip3 install Cython
RUN pip3 install dcase_models
RUN pip3 install 'h5py<3.0.0'
RUN pip3 install --upgrade && pip3 install scikit-build && pip3 install opencv-python
ENTRYPOINT ["/bin/bash" , "-l", "-c" ]
CMD [ "/bin/bash" ]
