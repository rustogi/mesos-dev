FROM mesos-dev:0.1
MAINTAINER rustogi

EXPOSE 5051

ENV LD_LIBRARY_PATH=/usr/local/lib

CMD ["--master=127.0.0.1:5050", "--log_dir=/var/log/mesos", "--work_dir=/var/lib/mesos", "--quiet"]

ENTRYPOINT ["mesos-slave"]
