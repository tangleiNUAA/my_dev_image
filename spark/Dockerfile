FROM vidi0312/scala:2.11.12
ENV SPARK_VERSION 2.3.1
ADD https://mirrors.tuna.tsinghua.edu.cn/apache/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop2.7.tgz /
RUN (cd / && gunzip < spark-2.3.1-bin-hadoop2.7.tgz)|(cd /opt && tar -xvf -)
RUN mv /opt/spark-2.3.1-bin-hadoop2.7 /opt/spark
RUN rm spark-2.3.1-bin-hadoop2.7.tgz
ENV SPARK_HOME /opt/spark
ENV PATH $SPARK_HOME:$SPARK_HOME/bin:$SPARK_HOME/sbin:$PATH
ENTRYPOINT ["/opt/spark/bin/spark-class"]
