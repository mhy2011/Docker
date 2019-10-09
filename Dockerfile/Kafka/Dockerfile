# kafka Dockerfile
FROM openjdk:8-jre-slim

ENV KAFKA_CONF_DIR=/config
COPY ./kafka_2.11-2.3.0.tgz /

ARG KAFKA_NAME=kafka_2.11-2.3.0

# Download Apache kafka
RUN set -eux; \
    tar -xzf kafka_2.11-2.3.0.tgz; \
    mkdir -p "$KAFKA_CONF_DIR"
	# cp "kafka_2.11-2.3.0/config/server.properties" "$KAFKA_CONF_DIR/"

COPY ./server.properties $KAFKA_CONF_DIR
WORKDIR $KAFKA_NAME
# VOLUME ["$KAFKA_DATA_DIR", "$KAFKA_DATA_LOG_DIR", "$KAFKA_LOG_DIR"]

# EXPOSE 2181 2888 3888

ENV PATH=$PATH:/$KAFKA_NAME/bin

RUN ls -lh /config; \
echo $PATH

# ENTRYPOINT ["/docker-entrypoint.sh"]
# CMD ["zkServer.sh", "start-foreground"]
# CMD ["kafka-server-start.sh" "/config/server.properties"]

COPY docker-entrypoint.sh /
ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["kafka-server-start.sh", "/config/server.properties"]
# CMD /kafka_2.11_2.3.0/bin/kafka-server-start.sh /config/server.properties