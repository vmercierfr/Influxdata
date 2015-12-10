FROM ubuntu:14.04

MAINTAINER Vincent Mercier <vmercier@gmail.com>

# Install wget
RUN apt-get update \
	&& apt-get install -y wget \
	&& apt-get clean \
	&& rm -rf /var/lib/apt/lists/*

# Install chronograf
WORKDIR /tmp
RUN wget https://s3.amazonaws.com/get.influxdb.org/chronograf/chronograf_0.4.0_amd64.deb \
	&& dpkg -i chronograf_0.4.0_amd64.deb \
	&& rm chronograf_0.4.0_amd64.deb

# Configure chronograf
ADD config.toml /opt/chronograf/config.toml

# Launch chronograf
EXPOSE 80
CMD ["/opt/chronograf/chronograf", "-config=/opt/chronograf/config.toml"]