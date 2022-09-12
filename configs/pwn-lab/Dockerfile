FROM tinylab/cloud-ubuntu-cinnamon:20220714
MAINTAINER Wu Zhangjin <wuzhangjin@gmail.com>

RUN echo '#! /bin/sh\n\
env DEBIAN_FRONTEND=noninteractive apt-get autoremove -y\n\
apt-get clean\n\
find /var/lib/apt/lists -type f -delete\n\
find /var/cache -type f -delete\n\
find /var/log -type f -delete\n\
exit 0\n\
' > /cleanup && chmod +x /cleanup

RUN apt-get -y update 
RUN apt-get -y install python3-pip \
	&& pip install pqi \
	&& pqi use tuna

RUN apt-get -y install --no-install-recommends \
	wget \
	curl \
	gcc \
	g++ \
	git \
	openssh-client \
	python-capstone \
	vim \
	gedit \
	gedit-plugins \
	gdb \
	autoconf \
	automake \
	libtool \
	&& /cleanup

RUN apt-get update
RUN apt-get -y install --no-install-recommends \
	ruby \
	&& /cleanup

EXPOSE 5900 22

WORKDIR /labs/

ENTRYPOINT ["/tools/lab/run"]
