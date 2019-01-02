FROM rocm/dev-ubuntu-16.04

RUN apt update && apt install -y --no-install-recommends libnuma-dev vim git cmake cxlactivitylogger rocm-profiler

RUN git config --global http.sslVerify false
RUN git clone --recursive -b clang_tot_upgrade https://github.com/RadeonOpenCompute/hcc.git

ENV PATH=$PATH:/opt/rocm/bin
ENV HIP_PLATFORM=hcc
ENV KMTHINLTO=0

RUN cd hcc && mkdir -p build && cd build && cmake -DCMAKE_BUILD_TYPE=Release \
      -DUSE_CODEXL_ACTIVITY_LOGGER=0 \
      .. && make -j$(nproc --ignore=1)

