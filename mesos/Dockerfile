FROM ubuntu:14.04
MAINTAINER rustogi

# Install all the needed packages here to get ready for mesos development
RUN apt-get -y update && apt-get -y install \
  build-essential \
  gcc-4.8 \
  openjdk-6-jdk \
  python-dev python-boto \
  libcurl4-nss-dev \
  libsasl2-dev \
  maven \
  libapr1-dev \
  libsvn-dev \
  autoconf \
  libtool \
  git \
  wget \
  emacs


# Build mesos first
WORKDIR /

RUN git clone --branch 0.22.1-rc6 https://git-wip-us.apache.org/repos/asf/mesos.git

WORKDIR /mesos

RUN gcc --version && automake --version && aclocal --version
RUN ./bootstrap
RUN mkdir -p build
RUN mkdir -p build/src/java/target

WORKDIR /mesos/build

RUN ../configure

WORKDIR /mesos/

# Predownload them due to Maven download failures
RUN wget http://central.maven.org/maven2/com/google/protobuf/protobuf-java/2.5.0/protobuf-java-2.5.0.jar
RUN wget http://central.maven.org/maven2/commons-collections/commons-collections/3.2/commons-collections-3.2.jar

WORKDIR /mesos/build

# We do build twice as the first time build always fails
RUN { \
     make; \
     mkdir -p /mesos/build/src/java/target; \
     cp /mesos/protobuf-java-2.5.0.jar /mesos/build/src/java/target/.; \
     cp /mesos/commons-collections-3.2.jar /mesos/build/src/java/target/.; \
     make; \
    }

#RUN make check

RUN make install

# Build mesos modules
#RUN mkdir -p /mesos-modules
#WORKDIR /mesos-modules

#RUN git clone https://github.com/mesos/modules

#WORKDIR /mesos-modules/modules

#RUN ./bootstrap
#RUN mkdir -p build

#WORKDIR /mesos-modules/modules/build

#RUN ../configure --with-mesos=/mesos
#RUN make


# Prepare environment for running mesos-slave and mesos-master
#ENV LD_LIBRARY_PATH=/usr/local/lib

