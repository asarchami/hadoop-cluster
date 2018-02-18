FROM openjdk:8-alpine
MAINTAINER Ali Sarchami "ali.sarchami@gmail.com"

ENV HADOOP_VERSION 2.9.0
ENV HADOOP_URL http://apache.mirrors.lucidnetworks.net/hadoop/common/hadoop-$HADOOP_VERSION/hadoop-$HADOOP_VERSION.tar.gz
ENV HADOOP_PREFIX=/opt/hadoop-$HADOOP_VERSION
ENV HADOOP_CONF_DIR=/etc/hadoop
ENV MULTIHOMED_NETWORK=1
ENV USER=root
ENV PATH $HADOOP_PREFIX/bin/:$PATH

RUN apk update && \
    apk add curl bash && \
    set -x && \
    curl -fSL "$HADOOP_URL" -o /tmp/hadoop.tar.gz && \
    # curl -fSL "$HADOOP_URL.asc" -o /tmp/hadoop.tar.gz.asc && \
    # gpg --verify /tmp/hadoop.tar.gz.asc && \
    mkdir -p /opt && \
    tar -xzf /tmp/hadoop.tar.gz -C /opt/ &&\
    rm /tmp/hadoop.* && \
    ln -s /opt/hadoop-$HADOOP_VERSION/etc/hadoop /etc/hadoop && \
    cp /etc/hadoop/mapred-site.xml.template /etc/hadoop/mapred-site.xml && \
    mkdir /opt/hadoop-$HADOOP_VERSION/logs && \
    mkdir /hadoop-data


ADD entrypoint.sh /entrypoint.sh
RUN chmod a+x /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]
