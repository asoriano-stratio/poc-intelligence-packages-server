# Base image - Stratio Ubuntu 16.04
FROM qa.stratio.com/stratio/ubuntu-base:16.04

MAINTAINER Intelligence Team - StratioBD  <intelligence@stratio.com>

USER root

# https://github.com/mosquito/pypi-server
# https://fabianlee.org/2018/02/08/ubuntu-a-centralized-apt-package-cache-using-squid-deb-proxy/

RUN apt-get -qq update && \
    apt-get install -y -qq --no-install-recommends \
        build-essential \
        python-dev \
        python-pip \
        libxml2-dev \
        libxslt-dev \
        libffi-dev \
        libpq-dev \
        python-setuptools \
        # Install squid-deb-proxy
        squid-deb-proxy

RUN pip3 install peewee==2.10.2 tornado==4.3 pypi-server
ENV DB=sqlite:///tmp/pypiserver.db
ENV ADDRESS=0.0.0.0

COPY entrypoint.py /usr/local/bin/entrypoint.py
COPY squid-deb-proxy.conf /etc/squid-deb-proxy/squid-deb-proxy.conf
RUN chmod a+x /usr/local/bin/entrypoint.py

ENTRYPOINT ["/usr/local/bin/entrypoint.py"]