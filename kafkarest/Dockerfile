FROM ubuntu:18.04
RUN mkdir -p /root/install
RUN apt-get update

WORKDIR /root/install

ENV DEBIAN_FRONTEND noninteractive
ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64

RUN apt-get install openjdk-8-jdk -y
RUN apt-get install wget -y
RUN apt-get install vim -y

# confluent-community 설치
RUN wget http://packages.confluent.io/archive/6.1/confluent-community-6.1.1.tar.gz
RUN tar -zxvf confluent-community-6.1.1.tar.gz
RUN mv confluent-6.1.1 /usr/local/confluent

# kafka-rest 설정파일 복사
COPY config/kafka-rest.properties /usr/local/confluent/etc/kafka-rest/kafka-rest.properties
RUN sed -i 's/\r//g' /usr/local/confluent/etc/kafka-rest/kafka-rest.properties

# kakfa-rest 실행
CMD /usr/local/confluent/bin/kafka-rest-start /usr/local/confluent/etc/kafka-rest/kafka-rest.properties

