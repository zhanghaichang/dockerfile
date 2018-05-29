FROM jdk-1.8.172

RUN curl -o apache-tomcat-8.5.31.tar.gz http://mirrors.shu.edu.cn/apache/tomcat/tomcat-8/v8.5.31/bin/apache-tomcat-8.5.31.tar.gz && \
  tar -xzvf apache-tomcat-8.5.31.tar.gz && rm -rf apache-tomcat-8.5.31.tar.gz apache-tomcat-8.5.31/webapps/* &&\
  echo -ne "apache-tomcat-8.5.31 image. (`uname -rsv`)\n" >> /home/x/apache-tomcat-8.5.31/logs/catalina.out
WORKDIR /home/x/apache-tomcat-8.5.31
COPY server.xml ./conf/server.xml
ENV CATALINA_OPTS "-Xms1g -Xmx1g -verbose:gc -XX:+PrintGCDetails -XX:+PrintGCDateStamps -XX:+PrintGCTimeStamps -XX:ParallelGCThreads=2 -XX:ConcGCThreads=2"
CMD ["/home/x/apache-tomcat-8.5.31/bin/catalina.sh","run"]
