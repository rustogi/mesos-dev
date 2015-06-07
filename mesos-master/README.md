# Container to provide an instance of mesos master running in its own container

## Build the docker container to run mesos-master
docker build -t mesos-dev-master:0.1 .

## Run the docker container
docker run -d -t mesos-dev-master:0.1
