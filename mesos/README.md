# Container to provide development environment for building Mesos and its Modules

## Build the docker container
docker build -t mesos-dev:0.1 .

## Run the docker container
docker run -it mesos-dev:0.1

## Perform mesos re-builds in docker container, only if necessary, as container comes with build already done
cd /mesos/build
make
make check
make install

## Perform mesos modules re-builds in docker container, only if necessary
cd /mesos-modules/modules/build
make

## Run mesos-master, mesos-slave, and python framework in docker container

### Run mesos-slave within mesos-dev container as follows
cd /mesos/build
mesos-slave --master=127.0.0.1:5050 --log_dir=/var/log/mesos --work_dir=/var/lib/mesos --quiet

### Run mesos-master within mesos-dev container  as follows
cd /mesos/build
mesos-master --ip=127.0.0.1 --log_dir=/var/log/mesos --work_dir=/var/lib/mesos

### Run the example python framework within mesos-dev container as follows
cd /mesos/build
./src/examples/python/test-framework 127.0.0.1:5050


