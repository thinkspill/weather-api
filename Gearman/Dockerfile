FROM debian:jessie
RUN apt-get update && apt-get install -y gearman-job-server; apt-get clean; rm -rf /var/lib/apt/lists/*
EXPOSE 4730
ENTRYPOINT [ "gearmand" ]
