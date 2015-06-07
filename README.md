# Build Mesos Container for Mesos Development
We follow the steps as described at http://mesos.apache.org/gettingstarted/

The mesos modules are built as per https://github.com/mesos/modules

The Mesos development environment that runs in docker or lxc container is based on Ubuntu 14.04 or later
image. 


## Docker based build

### Mesos
In this container one can develop mesos master or slave. One can run master and slave manually in the
same container for continuous development and testing.

This container is preferred for development purposes.


### Mesos-slave
In this container the slave is automatically started in its own container.


### Mesos-master

In this container the master is automatically started in its own container.

