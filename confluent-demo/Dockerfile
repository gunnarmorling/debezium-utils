FROM confluentinc/cp-kafka-connect-base:3.2.2

MAINTAINER Debezium Community

ENV DEBEZIUM_VERSION=0.5.1 \
    MAVEN_CENTRAL="https://repo1.maven.org/maven2" \
    DEBEZIUM_PLUGINS_DIR="/usr/share/java/kafka-connect-debezium"

RUN mkdir $DEBEZIUM_PLUGINS_DIR

#
# Download MySQL connector, verify the contents, and then install into the `$KAFKA_CONNECT_PLUGINS_DIR/debezium` directory...
#
RUN curl -fSL -o /tmp/plugin.tar.gz \
        $MAVEN_CENTRAL/io/debezium/debezium-connector-mysql/$DEBEZIUM_VERSION/debezium-connector-mysql-$DEBEZIUM_VERSION-plugin.tar.gz &&\
    echo "683e13f1a31650418567cf44e5a6802c  /tmp/plugin.tar.gz" | md5sum -c - &&\
    tar -xzf /tmp/plugin.tar.gz -C $DEBEZIUM_PLUGINS_DIR --strip 1 &&\
    rm -f /tmp/plugin.tar.gz

#
# Download MongoDB connector, verify the contents, and then install ...
#
RUN curl -fSL -o /tmp/plugin.tar.gz \
                 $MAVEN_CENTRAL/io/debezium/debezium-connector-mongodb/$DEBEZIUM_VERSION/debezium-connector-mongodb-$DEBEZIUM_VERSION-plugin.tar.gz &&\
    echo "3e6d905e00ebc5bfbb376b02a3fd302b  /tmp/plugin.tar.gz" | md5sum -c - &&\
    tar -xzf /tmp/plugin.tar.gz -C $DEBEZIUM_PLUGINS_DIR --strip 1 &&\
    rm -f /tmp/plugin.tar.gz    


#
# Download PostgreSQL connector, verify the contents, and then install ...
#
RUN curl -fSL -o /tmp/plugin.tar.gz \
                 $MAVEN_CENTRAL/io/debezium/debezium-connector-postgres/$DEBEZIUM_VERSION/debezium-connector-postgres-$DEBEZIUM_VERSION-plugin.tar.gz &&\
    echo "3933dd58ee3a0b5dd2e56d2c657b7561  /tmp/plugin.tar.gz" | md5sum -c - &&\
    tar -xzf /tmp/plugin.tar.gz -C $DEBEZIUM_PLUGINS_DIR --strip 1 &&\
    rm -f /tmp/plugin.tar.gz    


