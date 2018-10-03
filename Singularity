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
        git \
        ca-certificates \
        autoconf \
        libtool \
        m4 \
        libltdl-dev \
        cmake \
        flex \
        bison \
        libxml2-dev \
        python-dev \
        zlib1g-dev \
        binutils \
        binutils-dev \
        libdwarf-dev \
        libelf1 \
        elfutils \
        libelf-dev \
        sqlite3 \
        libx11-dev \
        libxext-dev \
        libcurl4-openssl-dev \
        curl
    apt-get clean

    # install spack
    cd /opt && git clone https://github.com/spack/spack.git
    export PATH=/opt/spack/bin:$PATH

    # install openspeedshop
    export FORCE_UNSAFE_CONFIGURE=1
    spack install openspeedshop +cuda+openmpi

