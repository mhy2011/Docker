# Dockerfile for apache kafka

FROM openjdk:latest

LABEL auther="mahaiyuan"
LABEL description="docker for kafka"

# set work dir
WORKDIR /root

# copy kafka file to docker image
COPY ./kafka_2.12-2.2.0.tgz .
COPY ./server.properties .
COPY ./docker-entrypoint.sh .

RUN tar -xzvf kafka_2.12-2.2.0.tgz; \
    mv kafka_2.12-2.2.0 kafka; \
    rm -f kafka_2.12-2.2.0.tgz

EXPOSE 9092

CMD ["/root/docker-entrypoint.sh"]