FROM alpine:3.3
MAINTAINER kakilangit <theguywhodrinkscoffeeandcodes@gmail.com>

ENV GOVERSION 1.6
ENV GOOS linux
ENV GOARCH amd64
ENV GOROOT /usr/lib/go
ENV GOPATH /gopath
ENV GOBIN $GOPATH/bin
ENV PATH $PATH:$GOROOT/bin:$GOPATH/bin

RUN apk add --update git bash go && rm -rf /var/cache/apk/* && mkdir -p /gopath/{pkg,src,bin}
  #&& wget -c https://storage.googleapis.com/golang/go${GOVERSION}.${GOOS}-${GOARCH}.tar.gz \
  #&& tar -zxvf go${GOVERSION}.${GOOS}-${GOARCH}.tar.gz -C /usr/lib \
  #&& rm -rf /var/cache/apk/* go${GOVERSION}.${GOOS}-${GOARCH}.tar.gz
