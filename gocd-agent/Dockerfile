FROM java:openjdk-7-jdk

ENV GOCD_VERSION 15.1.0-1863
ENV GOCD_DISTR go-agent.deb

# Install go.cd agent
RUN gpg --keyserver pgp.mit.edu --recv-keys 9149B0A6173454C7 \
    && curl -fSL "http://dl.bintray.com/gocd/gocd-deb/go-agent-$GOCD_VERSION.deb" -o $GOCD_DISTR \
    && curl -fSL "http://dl.bintray.com/gocd/gocd-deb/go-agent-$GOCD_VERSION.deb.asc" -o $GOCD_DISTR.asc \
    && gpg --verify $GOCD_DISTR.asc \
    && dpkg -i $GOCD_DISTR \
    && rm $GOCD_DISTR \
    && rm $GOCD_DISTR.asc

RUN mkdir /home/go \
    && usermod -d /home/go go

VOLUME /var/lib/go-agent

COPY docker-entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]

EXPOSE 8153 8154
CMD ["go-agent"]
