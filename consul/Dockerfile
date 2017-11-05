FROM alpine:3.6
MAINTAINER Aris Prawisudatama <soedomoto@gmail.com>

RUN apk upgrade --update

# Install essential
RUN apk add --no-cache alpine-sdk

# Supervisor
COPY supervisor/supervisord.conf /etc/supervisor/supervisord.conf
EXPOSE 9001

# Consul
ENV CONSUL_HOME /opt/consul
ENV CONSUL_VERSION 0.8.3
ENV CONSUL_SHA256 171cf4074bfca3b1e46112105738985783f19c47f4408377241b868affa9d445

RUN mkdir -p ${CONSUL_HOME}/conf \
  && mkdir -p ${CONSUL_HOME}/data \
  && mkdir -p ${CONSUL_HOME}/logs

RUN curl --insecure --location \
  https://releases.hashicorp.com/consul/${CONSUL_VERSION}/consul_${CONSUL_VERSION}_linux_amd64.zip \
  > /tmp/consul.zip

RUN cd /bin \
 && unzip /tmp/consul.zip \
 && chmod +x /bin/consul \
 && rm /tmp/consul.zip

EXPOSE 8300 8301 8301/udp 8302 8302/udp 8400 8500 8600 8600/udp

COPY consul/* ${CONSUL_HOME}/conf/
COPY supervisor/conf.d/* /etc/supervisor/conf.d/

# Set entrypoint
# ENTRYPOINT /bin/consul

# Remove unused
RUN apk del --purge alpine-sdk supervisor
