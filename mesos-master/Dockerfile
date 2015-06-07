FROM mesos-dev:0.1
MAINTAINER rustogi

EXPOSE 5050

ENV LD_LIBRARY_PATH=/usr/local/lib

CMD ["--ip=127.0.0.1", "--log_dir=/var/log/mesos/", "--work_dir=/var/lib/mesos"]

ENTRYPOINT ["mesos-master"]
