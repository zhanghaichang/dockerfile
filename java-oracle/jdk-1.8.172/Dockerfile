FROM centos:7
WORKDIR /
ENV LANG en_US.utf8
ENV TIME_ZONE "Asia/Shanghai"
ENV JAVA_HOME "/jdk1.8.0_172"
ADD jdk-8u172-linux-x64.tar.gz .
RUN rm -f /etc/localtime && ln -sf /usr/share/zoneinfo/${TIME_ZONE} /etc/localtime \
    && echo -ne "centos:7 image. (`uname -rsv`)\n" >> /root/.built \
    && ln -s /jdk1.8.0_172/jre/bin/java /bin/java \
    && echo "export LC_ALL=en_US.utf8"  >>  /etc/profile
RUN adduser -s /bin/false -u 1000 x
WORKDIR /home/x
USER x
ENV PATH "${PATH}:/jdk1.8.0_172/bin/"
CMD ["/bin/bash"]
