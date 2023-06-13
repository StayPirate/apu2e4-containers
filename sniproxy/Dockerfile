FROM alpine:latest

RUN apk add --no-cache sniproxy

WORKDIR /etc/sniproxy

EXPOSE 80
EXPOSE 443

CMD ["/usr/sbin/sniproxy","-c","/etc/sniproxy/sniproxy.conf","-f"]
