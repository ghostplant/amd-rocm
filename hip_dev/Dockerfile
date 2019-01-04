FROM rocm/dev-ubuntu-16.04

RUN apt update && apt install -y --no-install-recommends libnuma-dev vim git cmake
# cxlactivitylogger rocm-profiler

# RUN git config --global http.sslVerify false
RUN git clone --recursive https://github.com/ROCm-Developer-Tools/HIP.git

ENV PATH=$PATH:/opt/rocm/bin
ENV HIP_PLATFORM=hcc

RUN cd HIP && sed -i 's/COMPILE_HIP_ATP_MARKER=1/COMPILE_HIP_ATP_MARKER=0/g' ./install.sh && yes y | ./install.sh
