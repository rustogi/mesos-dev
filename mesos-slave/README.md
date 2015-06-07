# Container to provide an instance of mesos slave running in its own container

## Build the docker container to run mesos-slave
docker build -t mesos-dev-slave:0.1 .

## Run the docker container
docker run -d -t mesos-dev-slave:0.1
