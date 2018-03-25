FROM alpine:3.7

ARG VERSION="3.9.2"

LABEL description='Command container for concourse fly cli'
LABEL maintainer='Nate Catelli <ncatelli@packetfire.org>'

VOLUME /root

ADD https://github.com/concourse/concourse/releases/download/v${VERSION}/fly_linux_amd64 /usr/local/bin/fly
RUN chmod +x /usr/local/bin/fly

ENTRYPOINT [ "/usr/local/bin/fly" ]
CMD [ "-h" ]
