FROM ubuntu:14.04

MAINTAINER Vincent Mercier <vmercier@gmail.com>

# Install wget
RUN apt-get update \
	&& apt-get install -y wget \
	&& apt-get clean \
	&& rm -rf /var/lib/apt/lists/*

# Install telegraf
WORKDIR /tmp
RUN wget http://get.influxdb.org/telegraf/telegraf_0.2.4_amd64.deb \
	&& dpkg -i telegraf_0.2.4_amd64.deb \
	&& rm telegraf_0.2.4_amd64.deb

# Configure telegraf
ADD telegraf.conf /etc/opt/telegraf/telegraf.conf

# Launch telegraf
CMD ["/opt/telegraf/telegraf", "-config", "/etc/opt/telegraf/telegraf.conf", "-debug"]