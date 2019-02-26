FROM centos:7

MAINTAINER zhanghaichang <zhang.hc@topcheer.com>

WORKDIR /

ADD jdk-8u201-linux-x64.tar.gz .

ENV LANG=en_US.utf8 \
    TIME_ZONE="Asia/Shanghai" \
    JAVA_HOME="/jdk1.8.0_201" \
	PATH="${PATH}:/jdk1.8.0_201/bin/"
	
	
RUN rm -f /etc/localtime && ln -sf /usr/share/zoneinfo/${TIME_ZONE} /etc/localtime \
    && echo -ne "centos:7 image. (`uname -rsv`)\n" >> /root/.built \
    && ln -s /jdk1.8.0_201/jre/bin/java /bin/java \
    && echo "export LC_ALL=en_US.utf8"  >>  /etc/profile 
	
ADD http://nginx.org/download/nginx-1.14.0.tar.gz .

RUN yum install -y pcre-devel wget net-tools gcc zlib zlib-devel make openssl-devel \
	&& useradd -M -s /sbin/nologin nginx \
	&& tar -zxvf nginx-1.14.0.tar.gz \
	&& mkdir -p /usr/local/nginx \
	&& cd nginx-1.14.0 && ./configure --prefix=/usr/local/nginx --user=nginx --group=nginx --with-http_stub_status_module && make && make install \
	&& ln -s /usr/local/nginx/sbin/* /usr/local/sbin/

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
