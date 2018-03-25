FROM alpine:3.7

LABEL description='Key generation sidecar for concourse-ci'
LABEL maintainer='Nate Catelli <ncatelli@packetfire.org>'

ENV KEY_DIR='/data'

COPY start.sh /usr/local/bin/start.sh
RUN chmod +x /usr/local/bin/start.sh && \
    apk add --no-cache openssh

VOLUME ${KEY_DIR}
WORKDIR ${KEY_DIR}

CMD ["/usr/local/bin/start.sh"]
