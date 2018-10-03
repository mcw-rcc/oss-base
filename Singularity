Bootstrap: docker
From: ubuntu:16.04

%labels
Maintainer Matthew Flister
Version v2.3.1

%help
This container runs Open|SpeedShop performance tool.

%environment
    export PATH=/opt/spack/bin:$PATH

%post
    # default mount points
    mkdir -p /scratch/global /scratch/local /rcc/stor1/refdata /rcc/stor1/projects /rcc/stor1/depts

    # Install necessary packages
    apt-get update && apt-get install -y --no-install-recommends \
        build-essential \
        gcc-multilib \
        autoconf \
        libtool \
        m4 \
        libltdl-dev \
        cmake \
        flex \ 
        bison \
        libxml2-dev \
        python-dev \
        libz-dev \ 
        binutils \
        binutils-dev \
        libdwarf-dev \
        libelf1 \
        elfutils \
        libelf-dev \
        sqlite3 \
        libx11-dev \
        libxext-dev
    apt-get clean

    # install spack
    cd /opt && git clone https://github.com/spack/spack.git
    export PATH=/opt/spack/bin:$PATH

    # install openspeedshop
    spack install openspeedshop +cbtf+cuda+openmpi

