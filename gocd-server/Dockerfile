FROM java:openjdk-7-jdk

ENV GOCD_VERSION 15.1.0-1863
ENV GOCD_DISTR go-server.deb

# Install go.cd server
RUN gpg --keyserver pgp.mit.edu --recv-keys 9149B0A6173454C7 \
    && curl -fSL "http://dl.bintray.com/gocd/gocd-deb/go-server-$GOCD_VERSION.deb" -o $GOCD_DISTR \
    && curl -fSL "http://dl.bintray.com/gocd/gocd-deb/go-server-$GOCD_VERSION.deb.asc" -o $GOCD_DISTR.asc \
    && gpg --verify $GOCD_DISTR.asc \
    && dpkg -i $GOCD_DISTR \
    && rm $GOCD_DISTR \
    && rm $GOCD_DISTR.asc

VOLUME /var/lib/go-server

COPY docker-entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]

EXPOSE 8153 8154
CMD ["go-server"]
