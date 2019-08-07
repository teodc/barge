FROM mongo:latest

EXPOSE 27017

COPY mongod.conf /etc/mongo/mongod.conf

WORKDIR /etc/mongo

ENTRYPOINT ["mongod"]
