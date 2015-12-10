FROM ubuntu:14.04

MAINTAINER Vincent Mercier <vmercier@gmail.com>

# Install wget
RUN apt-get update \
	&& apt-get install -y wget \
	&& apt-get clean \
	&& rm -rf /var/lib/apt/lists/*

# Install telegraf
WORKDIR /tmp
RUN wget https://s3.amazonaws.com/influxdb/kapacitor_0.2.0-1_amd64.deb \
	&& dpkg -i kapacitor_0.2.0-1_amd64.deb \
	&& rm kapacitor_0.2.0-1_amd64.deb

# Configure kapacitor
ADD kapacitor.conf /etc/kapacitor.conf
#RUN kapacitord config > /etc/kapacitor.conf

# Launch telegraf
EXPOSE 9092
CMD ["/usr/bin/kapacitord", "-config", "/etc/kapacitor.conf"]