# kafka Dockerfile
FROM openjdk:8-jre-slim

ENV KAFKA_CONF_DIR=/config
ARG KAFKA_NAME=kafka_2.11-2.3.0
COPY ./${KAFKA_NAME}.tgz /


# unzip kafka and create config dir
RUN set -eux; \
    tar -xzf ${KAFKA_NAME}.tgz; \
    rm ${KAFKA_NAME}.tgz; \
    mkdir -p "$KAFKA_CONF_DIR"

WORKDIR $KAFKA_NAME
ENV PATH=$PATH:/$KAFKA_NAME/bin

COPY ./server.properties $KAFKA_CONF_DIR
COPY docker-entrypoint.sh /

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["kafka-server-start.sh", "/config/server.properties"]