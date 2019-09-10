FROM redis:5.0

EXPOSE 6379

COPY redis.conf /etc/redis/

WORKDIR /etc/redis

CMD ["redis-server"]
