FROM ubuntu:focal
MAINTAINER liuguanliang<sensei.liu@qq.com>

ENV TZ=Asia/Shanghai
ENV LANG='en_US.UTF-8' LANGUAGE='en_US:en' LC_ALL='C'
ARG JDK_SHA256=725aba257da4bca14959060fea3faf59005eafdc2d5ccc3cb745403c5b60fb27
ARG JDK_NAME=zulu11.68.17-ca-jdk11.0.21-linux_x64

RUN apt-get -qq update && \
    apt-get -qq -y --no-install-recommends install locales curl tzdata && \
    echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen && \
    locale-gen en_US.UTF-8 && \
    ln -snf /usr/share/zoneinfo/${TZ} /etc/localtime && \
    echo ${TZ} > /etc/timezone && \
    curl -fskSOL https://cdn.azul.com/zulu/bin/${JDK_NAME}.tar.gz && \
    echo "${JDK_SHA256} ${JDK_NAME}.tar.gz" | sha256sum --strict --check && \
    mkdir /opt/jdk && \
    tar -zxf ${JDK_NAME}.tar.gz -C /opt/jdk && \
    apt-get -qq -y purge --auto-remove curl && \
    rm -rf /var/lib/apt/lists/* /opt/jdk/${JDK_NAME}/src.zip ${JDK_NAME}.tar.gz

ENV PATH="/opt/jdk/${JDK_NAME}/bin:$PATH"
