FROM openjdk:11.0.11-jre-slim
#FROM java:openjdk-8-jdk

ENV spark_ver 3.1.2

RUN apt-get update && apt-get install -y wget && rm -rf /var/lib/apt/lists/*

# Get Spark from US Apache mirror.
RUN mkdir -p /opt && \
    cd /opt && \
    wget https://downloads.apache.org/spark/spark-${spark_ver}/spark-${spark_ver}-bin-hadoop3.2.tgz && \
    tar xzf "spark-${spark_ver}-bin-hadoop3.2.tgz" && \
    ln -s spark-${spark_ver}-bin-hadoop3.2 spark && \
    echo Spark ${spark_ver} installed in /opt


ADD start-common.sh start-worker.sh start-master.sh /
RUN chmod +x /start-common.sh /start-master.sh /start-worker.sh
ENV PATH $PATH:/opt/spark/bin

