FROM nvidia/cuda:11.1-cudnn8-devel-ubuntu20.04

ENV DEBIAN_FRONTEND=noninteractive

RUN echo "Installing dependencies..." && \
	apt-get -y --no-install-recommends update && \
	apt-get -y --no-install-recommends upgrade && \
	apt-get install -y --no-install-recommends \
	build-essential \
	cmake \
	git \
	libatlas-base-dev \
	libprotobuf-dev \
	libleveldb-dev \
	libsnappy-dev \
	libhdf5-serial-dev \
	protobuf-compiler \
	libboost-all-dev \
	libgflags-dev \
	libgoogle-glog-dev \
	liblmdb-dev \
	python3-setuptools \
	python3-dev \
	python3-pip \
	libopencv-dev && \
	python3 -m pip install --upgrade pip && \
	python3 -m pip install \
	numpy \
	protobuf \
	opencv-python

RUN echo "Downloading and building OpenPose..." && \
	git clone https://github.com/CMU-Perceptual-Computing-Lab/openpose.git && \
	mkdir -p /openpose/build && \
	cd /openpose/build && \
	cmake .. && \
	make -j`nproc`

WORKDIR /openpose
