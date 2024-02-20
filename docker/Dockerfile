FROM ubuntu:22.04

ARG STREAMA_VERSION=1.10.5
ARG JAVA_VERSION=8

RUN apt-get -y update && apt-get -y upgrade

RUN apt-get -y install \
    curl \
    openjdk-${JAVA_VERSION}-jre

WORKDIR /streama 

# Replace with building from source
RUN curl -Lo /streama/streamaserver.jar "https://github.com/streamaserver/streama/releases/download/v${STREAMA_VERSION}/streama-${STREAMA_VERSION}.jar"

RUN useradd -m streama
RUN chown -R streama:streama /streama

USER streama

ENV THEMOVIEDB_API_KEY=""

CMD ["java", "-jar", "/streama/streamaserver.jar"]
