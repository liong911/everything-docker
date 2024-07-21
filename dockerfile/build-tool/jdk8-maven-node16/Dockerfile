FROM ccr.ccs.tencentyun.com/everything/zulu-jdk8
MAINTAINER liuguanliang<sensei.liu@qq.com>

ARG MAVEN_SHA256=17811e108701af5985bf5167abbd47c06e92c6c6bd1c13a1a1c095c9b4ecc32a
ARG MAVEN_NAME=apache-maven-3.8.8
ARG NODE_SHA256=c9193e6c414891694759febe846f4f023bf48410a6924a8b1520c46565859665
ARG NODE_NAME=node-v16.20.2-linux-x64

RUN apt-get -qq update && \
    apt-get -qq -y --no-install-recommends install curl && \
    curl -fskSOL https://repo.maven.apache.org/maven2/org/apache/maven/apache-maven/3.8.8/${MAVEN_NAME}-bin.tar.gz && \
    echo "${MAVEN_SHA256} ${MAVEN_NAME}-bin.tar.gz" | sha256sum --strict --check && \
    mkdir /opt/maven && \
    tar -zxf ${MAVEN_NAME}-bin.tar.gz -C /opt/maven && \
    curl -fskSOL https://nodejs.org/download/release/v16.20.2/${NODE_NAME}.tar.gz && \
    mkdir /opt/node && \
    tar -zxf ${NODE_NAME}.tar.gz -C /opt/node && \
    apt-get -qq -y purge --auto-remove curl && \
    rm -rf /var/lib/apt/lists/* ${MAVEN_NAME}-bin.tar.gz ${NODE_NAME}.tar.gz 
COPY .dockerfile/build-tool/jdk8-maven-node16/settings.xml /opt/maven/${MAVEN_NAME}/conf

ENV M2_HOME=/root/.m2
ENV NODE_HOME=/opt/node/${NODE_NAME}
ENV PATH="/opt/maven/${MAVEN_NAME}/bin:$NODE_HOME/bin:$PATH"
