FROM concourse/concourse

LABEL maintainer="Nate Catelli <ncatelli@packetfire.org>"
LABEL description="Containerized version of a concourse worker running docker."

VOLUME /var/lib/docker

RUN apt-get update -y && \
    apt-get install curl -yq && \
    curl -sSL https://get.docker.com/ | sh && \
    apt-get clean
