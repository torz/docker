FROM ubuntu:trusty

MAINTAINER "The Galactic Empire"

ENV DEBIAN_FRONTEND noninteractive

RUN locale-gen en_GB.UTF-8
RUN update-locale LANG=en_GB.UTF-8
RUN update-locale LANGUAGE=en_GB.UTF-8
RUN update-locale LC_ALL=en_GB.UTF-8

# get web server ----------------------------------------
RUN apt-get -qq update && \
    apt-get install -y apache2 \
                       libapache2-mod-wsgi-py3 \
                       python3-pip
RUN a2enmod wsgi
# -------------------------------------------------------


# install scipy and deps --------------------------------
RUN apt-get -qq update && \
    apt-get install -y libblas3 \
                       libblas-dev \
                       libgfortran3 \
                       liblapack3 \
                       liblapack-dev \
                       gfortran

RUN pip3 install numpy
RUN pip3 install scipy
RUN pip3 install cython
RUN pip3 install numexpr
RUN pip3 install pandas
RUN pip3 install tables
RUN pip3 install scikit-learn
RUN pip3 install flask

# install matplotlib ------------------------------------
RUN apt-get -qq update && \
    apt-get install -y pkg-config \
                       libpng12-dev \
                       libfreetype6-dev

RUN pip3 install matplotlib

# install ipython ---------------------------------------
RUN apt-get -qq update && \
    apt-get install -y libzmq3 \
                       libzmq3-dev

RUN pip3 install pyzmq \
                 tornado \
                 ipython


VOLUME ["/var/www"]

EXPOSE 80 443

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid

# Default command to run
CMD ["/usr/sbin/apache2", "-D", "FOREGROUND"]
