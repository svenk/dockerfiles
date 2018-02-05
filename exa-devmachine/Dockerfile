# ExaHyPE developer machine docker image
# Contains javac, GCC, OpenMPI and a recent version of TBB,
# as well as make, git, subversion, doxygen, etc.
# This image is roughly 1GB big :-/

# Proper Ubuntu 16.04 in a Docker image (http://phusion.github.io/)
FROM phusion/baseimage:0.9.22

CMD ["/sbin/my_init"]

RUN apt-get update && apt-get install -y \
  wget curl git subversion make doxygen build-essential \
  gfortran libopenmpi-dev default-jdk \
  python-numpy && \
  apt-get --purge remove -y .\*-doc$ && \
  apt-get clean -y && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# obtain a recent version of Intel Threading Building Blocks
# because Ubuntus 16.04 version is broken

RUN mkdir /tbb && cd /tbb && \
  wget https://github.com/01org/tbb/archive/2017_U7.tar.gz && \
  tar xvfz 2017_U7.tar.gz && cd tbb-2017_U7 && \
  cd src && make -j4 tbb tbbmalloc tbbproxy release debug && \
  cp /tbb/tbb-2017_U7/build/*release/libtbb*so* /usr/lib/ && \
  cp -r /tbb/tbb-2017_U7/include/tbb /usr/include && \
  cd / && rm -rf /tbb/tbb-2017_U7  # we keep the tar.gz!

