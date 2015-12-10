FROM ubuntu:14.04

MAINTAINER Vincent Mercier <vmercier@gmail.com>

# Install wget
RUN apt-get update \
	&& apt-get install -y wget \
	&& apt-get clean \
	&& rm -rf /var/lib/apt/lists/*

# Install influxdb
WORKDIR /tmp/
RUN wget http://influxdb.s3.amazonaws.com/influxdb_0.9.6_amd64.deb \
	&& dpkg -i influxdb_0.9.6_amd64.deb \
	&& rm influxdb_0.9.6_amd64.deb

# Configure influxdb
#RUN mkdir /etc/influxdb/
RUN /usr/bin/influxd config > /etc/influxdb/influxdb.generated.conf

# Start influxdb
EXPOSE 8086
CMD ["/usr/bin/influxd", "-config", "/etc/influxdb/influxdb.generated.conf"]
