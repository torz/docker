FROM ubuntu:latest

MAINTAINER TorZ Corporation

ENV DEBIAN_FRONTEND noninteractive

RUN locale-gen en_GB.UTF-8
RUN update-locale LANG=en_GB.UTF-8
RUN update-locale LANGUAGE=en_GB.UTF-8
RUN update-locale LC_ALL=en_GB.UTF-8
RUN apt-get -qq update
RUN apt-get -qq -y install postgresql-9.3

ADD run /usr/local/run
RUN chmod +x /usr/local/run

EXPOSE 5432

VOLUME  ["/srv"]

# Default command to run
CMD ["/usr/local/run"]

