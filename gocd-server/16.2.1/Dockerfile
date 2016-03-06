FROM ubuntu:14.04

ENV GOCD_VERSION 16.2.1-3027
ENV GOCD_DISTR go-server.deb

RUN apt-get update \
    && apt-get -y install -y openjdk-7-jdk curl unzip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install go.cd server
RUN curl -fSL "https://download.go.cd/binaries/$GOCD_VERSION/deb/go-server-$GOCD_VERSION.deb" -o $GOCD_DISTR \
    && dpkg -i $GOCD_DISTR \
    && rm $GOCD_DISTR

VOLUME /var/lib/go-server

COPY docker-entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]

EXPOSE 8153 8154
CMD ["go-server"]
