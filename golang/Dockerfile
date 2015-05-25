FROM ubuntu:trusty
MAINTAINER kakilangit <theguywhodrinkscoffeeandcodes@gmail.com>

ENV DEBIAN_FRONTEND noninteractive
ENV GOOS linux
ENV GOARCH amd64
ENV GOPATH /gopath
ENV GOROOT /go
ENV GOBIN /go/bin
ENV PATH $PATH:/$GOBIN

RUN apt-get update && apt-get upgrade -y && apt-get install -y gcc nano wget imagemagick libmagickcore-dev git

RUN wget -c https://storage.googleapis.com/golang/go1.4.2.linux-amd64.tar.gz && \
	tar -xvf go1.4.2.linux-amd64.tar.gz && \
	rm -rf go1.4.2.linux-amd64.tar.gz

RUN mkdir -p /gopath &&\
	go get -v github.com/ziutek/mymysql/thrsafe &&\
	go get -v github.com/ziutek/mymysql/autorc &&\
	go get -v github.com/ziutek/mymysql/godrv  &&\
	go get -v github.com/PuerkitoBio/goquery &&\
	go get -v github.com/bradfitz/gomemcache/memcache &&\
	go get -v github.com/mailgun/mailgun-go &&\
	go get -v github.com/stathat/go &&\
	go get -v github.com/yvasiyarov/gorelic &&\
	go get -v github.com/quirkey/magick
