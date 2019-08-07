FROM redis:latest

EXPOSE 6379

COPY redis.conf /etc/redis/redis.conf

WORKDIR /etc/redis

ENTRYPOINT ["redis-server"]
