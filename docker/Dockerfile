FROM nvidia/cuda:11.8.0-cudnn8-devel-ubuntu20.04

#get deps
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
    python3-dev python3-pip git g++ wget make libprotobuf-dev protobuf-compiler libopencv-dev \
    libgoogle-glog-dev libboost-all-dev libhdf5-dev libatlas-base-dev \
    python3-setuptools vim libgtk2.0-dev libgtk-3-dev build-essential cmake mysql-client

####### If using OpenPose need these next sections

# ####### Now set up PosePipe itself
WORKDIR /PosePipe
COPY requirements.txt .
RUN pip3 install -r requirements.txt
COPY setup.py README.md /PosePipe/
COPY pose_pipeline /PosePipe/pose_pipeline
RUN pip3 install -e /PosePipe

COPY datajoint_config.json /root/.datajoint_config.json
COPY scripts/*.py /PosePipe/

# CMD ["python"]
# ENTRYPOINT ["/bin/bash"]
# ENTRYPOINT ["/usr/bin/python3"]
CMD ["sh", "-c", "while true; do sleep 1000; done"]
