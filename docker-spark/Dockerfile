#FROM sequenceiq/hadoop-docker:2.6.0
FROM visra-hadoop
MAINTAINER SequenceIQ

#support for Hadoop 2.6.0
#RUN curl -s http://d3kbcqa49mib13.cloudfront.net/spark-1.6.1-bin-hadoop2.6.tgz | tar -xz -C /usr/local/
RUN yum install -y epel-release --nogpgcheck  
RUN rm /var/lib/rpm/__db**
RUN yum install -y python34  
RUN curl -s https://www-eu.apache.org/dist/spark/spark-2.3.3/spark-2.3.3-bin-hadoop2.7.tgz  | tar -xz -C /usr/local
RUN cd /usr/local && ln -s spark-2.3.3-bin-hadoop2.7 spark
ENV SPARK_HOME /usr/local/spark
RUN mkdir $SPARK_HOME/yarn-remote-client
ADD yarn-remote-client $SPARK_HOME/yarn-remote-client
ENV PYSPARK_PYTHON /usr/bin/python3.4

# COMMENT
#RUN $BOOTSTRAP && $HADOOP_PREFIX/bin/hadoop dfsadmin -safemode leave && $HADOOP_PREFIX/bin/hdfs dfs -put $SPARK_HOME-2.3.3-bin-hadoop2.7/lib/spark


ENV YARN_CONF_DIR $HADOOP_PREFIX/etc/hadoop
ENV PATH $PATH:$SPARK_HOME/bin:$HADOOP_PREFIX/bin
# update boot script
COPY bootstrap.sh /etc/bootstrap.sh
RUN chown root.root /etc/bootstrap.sh
RUN chmod 700 /etc/bootstrap.sh

#install R
# RUN rpm -ivh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
# RUN yum -y install R

ENTRYPOINT ["/etc/bootstrap.sh"]
