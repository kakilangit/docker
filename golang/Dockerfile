FROM ubuntu:trusty
MAINTAINER kakilangit <theguywhodrinkscoffeeandcodes@gmail.com>

ENV DEBIAN_FRONTEND noninteractive
ENV GOVERSION 1.5.3
ENV GOOS linux
ENV GOARCH amd64
ENV GOPATH /gopath
ENV GOROOT /go
ENV GOBIN /go/bin
ENV PATH $PATH:/$GOBIN

RUN apt-get update && apt-get upgrade -y && apt-get install -y gcc nano wget imagemagick libmagickcore-dev git

RUN wget -c https://storage.googleapis.com/golang/go$GOVERSION.$GOOS-$GOARCH.tar.gz && \
	tar -xvf go$GOVERSION.$GOOS-$GOARCH.tar.gz && \
	rm -rf go$GOVERSION.$GOOS-$GOARCH.tar.gz

RUN mkdir -p "$GOPATH"

WORKDIR $GOPATH
