FROM nvidia/cuda:10.0-cudnn7-devel-ubuntu18.04
ARG DEBIAN_FRONTEND=noninteractive
# Install system dependencies

RUN apt-get update --fix-missing && apt-get install -y curl grep sed dpkg && \
    apt-get install -y libxvidcore-dev libx264-dev && \
    apt-get install -y libgtk-3-dev && \
    apt-get install -y libatlas-base-dev gfortran && \
    apt-get install -y  python3 &&\
    apt-get install -y  python3-dev &&\
    apt-get install -y  python3-pip &&\
    apt-get install -y python-opencv &&\
    apt-get clean \
    && pip3 install pip --upgrade pip

WORKDIR usr/src/flask_app
COPY requirements_original.txt .
RUN apt-get update
RUN apt-get install -y libsm6 libxext6 libxrender-dev
RUN pip3 install Cython==0.29.17
RUN pip3 install numpy==1.17.0
RUN pip3 install --no-cache-dir -r requirements_original.txt
ENV PATH=/usr/local/cuda-10.0/bin${PATH:+:${PATH}}
ENV LD_LIBRARY_PATH=/usr/local/cuda/lib64:${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
ENV LD_LIBRARY_PATH=/usr/local/cuda/extras/CUPTI/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}

COPY . .