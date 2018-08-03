BootStrap: docker
From: ubuntu:16.04

%post
    apt-get -y update
    apt-get -y install build-essential wget cmake libmlx4-1 ibutils libibverbs-dev ibverbs-utils  libibverbs1 libsysfs2 libsysfs-dev

    wget https://www.open-mpi.org/software/ompi/v3.0/downloads/openmpi-3.0.0.tar.bz2
    tar -xjf openmpi-3.0.0.tar.bz2
    cd openmpi-3.0.0
    ./configure --prefix=/usr/local --with-hwloc --with-verbs
    make -j4
    make install
    ldconfig

    wget https://drive.google.com/file/d/1mjL0f1ZqdGccJoD5_y2w3mvA276pHGE_/view?usp=drive_web
    tar zxf plumed-2.3.6.tgz
    cd plumed-2.3.6
    ./configure --prefix=/usr/local
    make -j 4
    make doc
    make install
    
    wget http://ftp.gromacs.org/pub/gromacs/gromacs-5.1.4.tar.gz
    tar zxf gromacs-5.1.4.tar.gz
    cd gromacs-5.1.4
    mkdir build
    cd build 
    cmake .. -DGMX_BUILD_OWN_FFTW=ON -DREGRESSIONTEST_DOWNLOAD=ON -DCMAKE_INSTALL_PREFIX=/usr/local -DBUILD_SHARED_LIBS=OFF -DGMX_PREFER_STATIC_LIBS=ON
    make
    make check
    make install
    cmake .. -DGMX_BUILD_OWN_FFTW=ON -DREGRESSIONTEST_DOWNLOAD=ON -DGMX_MPI=on -DGMX_MPI=on -DCMAKE_INSTALL_PREFIX=/usr/local
    make
    make check
    make install
    
    mkdir /gpfs /spin1 /gs2 /gs3 /gs4 /gs5 /gs6 /gs7 /gs8 /data /scratch /fdb /lscratch /scratch

%environment
    export LC_ALL=C
    export PATH=/opt//games:$PATH

%runscript
