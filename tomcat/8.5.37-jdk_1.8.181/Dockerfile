FROM zhanghaichang/jdk-1.8.172

RUN curl -o apache-tomcat-8.5.37.tar.gz http://mirrors.shu.edu.cn/apache/tomcat/tomcat-8/v8.5.37/bin/apache-tomcat-8.5.37.tar.gz && \
  tar -xzvf apache-tomcat-8.5.37.tar.gz &&\
  echo -ne "apache-tomcat-8.5.37 image. (`uname -rsv`)\n" >> /home/x/apache-tomcat-8.5.37/logs/catalina.out
WORKDIR /home/x/apache-tomcat-8.5.37
CMD ["/home/x/apache-tomcat-8.5.37/bin/catalina.sh","run"]
