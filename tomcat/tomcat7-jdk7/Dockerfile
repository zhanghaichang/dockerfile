FROM 172.18.161.165:8888/base/centos7-oracle-jdk-1.7:v1.0.0

MAINTAINER zhanghaichang <zhang.hc@topcheer.com>

RUN curl -o apache-tomcat-7.0.93.tar.gz http://mirrors.hust.edu.cn/apache/tomcat/tomcat-7/v7.0.93/bin/apache-tomcat-7.0.93.tar.gz && \
    tar -xzvf apache-tomcat-7.0.93.tar.gz && rm -rf apache-tomcat-7.0.93.tar.gz && \
    echo -ne "apache-tomcat-7.0.93 image. (`uname -rsv`)\n" >> /home/x/apache-tomcat-7.0.93/logs/catalina.out
  
WORKDIR /home/x/apache-tomcat-7.0.93

CMD ["/bin/bash"]
