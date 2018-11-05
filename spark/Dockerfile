FROM vidi0312/scala:2.11.12
ENV SPARK_VERSION 2.3.1
ENV HADOOP_VERSION 2.7
ADD https://mirrors.tuna.tsinghua.edu.cn/apache/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz /
RUN (cd / && gunzip < spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz)|(cd /opt && tar -xvf -)
RUN mv /opt/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION} /opt/spark
RUN rm spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz
ENV SPARK_HOME /opt/spark
ENV PATH $SPARK_HOME:$SPARK_HOME/bin:$SPARK_HOME/sbin:$PATH
ENTRYPOINT ["/opt/spark/bin/spark-class"]
