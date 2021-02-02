### 1.9.3

- Pin numpy to the same 1.19.4 version that frigate pins, see https://github.com/blakeblackshear/frigate/blob/v0.8.1/docker/Dockerfile.wheels#L27

### 1.9.2

- Move ARG BUILD_ARCH=amd64 to top of Dockerfile

### 1.9.1

- Dynamically build tensorflow tflite wheel on target platform and use official blakeblackshear/frigate:0.8.1 as base image

### 1.2

- 0.8.0 Beta 3

### 1.1

- 0.8.0 Beta 2

### 1.0

- 0.8.0 Beta 1
