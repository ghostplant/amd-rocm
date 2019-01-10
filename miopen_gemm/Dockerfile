FROM rocm/dev-ubuntu-16.04

RUN apt update && apt install -y --no-install-recommends libnuma-dev vim git cmake cxlactivitylogger rocm-profiler rocm-cmake

RUN git config --global http.sslVerify false
RUN git clone --recursive https://github.com/ROCmSoftwarePlatform/MIOpenGEMM

ENV PATH=$PATH:/opt/rocm/bin
ENV HIP_PLATFORM=hcc

RUN cd MIOpenGEMM && mkdir -p build && cd build && cmake -DCMAKE_BUILD_TYPE=Release \
      .. && make -j$(nproc --ignore=1)

