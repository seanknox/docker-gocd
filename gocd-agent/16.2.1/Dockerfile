FROM ubuntu:14.04

ENV GOCD_VERSION 16.2.1-3027
ENV GOCD_DISTR go-agent.deb

RUN apt-get update \
    && apt-get -y install -y openjdk-7-jdk curl unzip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install go.cd agent
RUN curl -fSL "https://download.go.cd/binaries/$GOCD_VERSION/deb/go-agent-$GOCD_VERSION.deb" -o $GOCD_DISTR \
    && dpkg -i $GOCD_DISTR \
    && rm $GOCD_DISTR

RUN mkdir /home/go \
    && usermod -d /home/go go

VOLUME /var/lib/go-agent

COPY docker-entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]

CMD ["go-agent"]
