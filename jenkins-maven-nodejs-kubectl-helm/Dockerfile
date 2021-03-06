FROM jenkinsci/jnlp-slave

USER root

# Maven
RUN curl -fsSL https://archive.apache.org/dist/maven/maven-3/3.5.4/binaries/apache-maven-3.5.4-bin.tar.gz | tar xzf - -C /usr/share \
  && mv /usr/share/apache-maven-3.5.4 /usr/share/maven \
  && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

ENV MAVEN_VERSION=${MAVEN_VERSION} \
    M2_HOME=/usr/share/maven \
    maven.home=$M2_HOME \
    M2=$M2_HOME/bin \
    PATH=$M2:$PATH

COPY settings.xml $M2_HOME/conf/settings.xml

# Install Docker
RUN apt-get -qq update && \
    apt-get -qq -y install curl && \
    curl -sSL https://get.docker.com/ | sh
    
RUN rm -rf /etc/localtime && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo 'Asia/Shanghai' > /etc/timezone
    
# install node v10
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash - \
    && apt-get install -y nodejs \
    && node --version

# setting npm global path
ENV PATH $PATH:/home/jenkins/.npm-global/bin
RUN mkdir ~/.npm-global  \
    && npm config set prefix '~/.npm-global' \
	  && npm config set registry http://172.18.161.165:8081/repository/npm-all/
  

# Install kubectl and helm
RUN curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl && \
    chmod +x ./kubectl && \
    mv ./kubectl /usr/local/bin/kubectl && \
    curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get | bash
