FROM redis:3.2.8

ARG REDIS_PASS
RUN echo $REDIS_PASS > /etc/pass
ENV REDIS_PASS qwerty

# install envsubst
RUN apt-get update \
  && apt-get install gettext-base -y \
  && rm -rf /var/lib/apt/lists/*

# add config template
ADD redis/redis.conf.template /etc/redis.conf.template

# generate config file
RUN envsubst < /etc/redis.conf.template > /etc/redis.conf

# mountable directories
VOLUME ["/data"]

# working directory
WORKDIR /data

# default command
CMD ["redis-server", "/etc/redis.conf"]

# expose ports
EXPOSE 6379
