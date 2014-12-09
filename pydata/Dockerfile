FROM ipython/ipython

MAINTAINER TorZ Corporation

RUN apt-get update && apt-get install -y language-pack-en
ENV LANGUAGE en_GB.UTF-8
ENV LANG en_GB.UTF-8
ENV LC_ALL en_GB.UTF-8

RUN locale-gen en_GB.UTF-8
RUN dpkg-reconfigure locales

# From https://github.com/ogrisel/docker-openblas
ADD openblas.conf /etc/ld.so.conf.d/openblas.conf

# From https://github.com/ogrisel/docker-sklearn-openblas
ADD numpy-site.cfg /tmp/numpy-site.cfg
ADD scipy-site.cfg /tmp/scipy-site.cfg

ADD build_scipy_stack.sh /tmp/build_scipy_stack.sh
RUN bash /tmp/build_scipy_stack.sh

## Extremely basic test of install
RUN python3 -c "import matplotlib, scipy, numpy, pandas, sklearn, seaborn, yt, patsy, sympy, IPython"

# Clean up from build
RUN rm -f /tmp/build_scipy_stack.sh /tmp/numpy-site.cfg /tmp/scipy-site.cfg
