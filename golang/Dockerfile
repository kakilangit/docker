FROM alpine:3.3
MAINTAINER kakilangit <theguywhodrinkscoffeeandcodes@gmail.com>

RUN apk add --update go git bash && rm -rf /var/cache/apk/*

ENV GOVERSION 1.5.3
ENV GOOS linux
ENV GOARCH amd64
ENV GOROOT /usr/lib/go
ENV GOPATH /gopath
ENV GOBIN $GOPATH/bin
ENV PATH $PATH:$GOROOT/bin:$GOPATH/bin
