ARG BUILD_ARCH=amd64

FROM ubuntu:20.04 as build

ENV DEBIAN_FRONTEND=noninteractive

# tflite dependencies, see https://github.com/tensorflow/tensorflow/tree/master/tensorflow/lite/tools/pip_package
RUN apt-get -qq update \
    && apt-get -qq install -y \
    python3 \
    python3-dev \
    python3-pip \
    build-essential cmake git pkg-config \
    curl unzip \
    swig libjpeg-dev zlib1g-dev

RUN git clone https://github.com/tensorflow/tensorflow.git

RUN pip3 install -U \
    numpy \
    pybind11

RUN bash tensorflow/tensorflow/lite/tools/make/download_dependencies.sh
RUN bash tensorflow/tensorflow/lite/tools/pip_package/build_pip_package.sh

FROM blakeblackshear/frigate:0.8.1-${BUILD_ARCH}

COPY --from=build /tensorflow/tensorflow/lite/tools/pip_package/gen/tflite_pip/python3/dist/tflite_runtime-2.5.0-cp38-cp38-linux_x86_64.whl /wheels/
RUN pip3 install --upgrade /wheels/tflite_runtime-2.5.0-cp38-cp38-linux_x86_64.whl