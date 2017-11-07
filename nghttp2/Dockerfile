FROM alpine:3.6
MAINTAINER Aris Prawisudatama <soedomoto@gmail.com>

RUN apk upgrade --update

# Install essential
RUN apk add --no-cache alpine-sdk

# Install nghttp2
RUN apk add --no-cache nghttp2
COPY nghttpx.conf /etc/nghttpx.conf
COPY start-nghttpx.sh /usr/bin/start-nghttpx.sh
RUN chmod +x /usr/bin/start-nghttpx.sh

EXPOSE 3000 80

# Remove unused
RUN apk del --purge alpine-sdk

CMD ["/usr/bin/start-nghttpx.sh"]
