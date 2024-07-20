FROM ubuntu:focal
MAINTAINER liuguanliang<sensei.liu@qq.com>

ENV TZ=Asia/Shanghai
ENV LANG='en_US.UTF-8' LANGUAGE='en_US:en' LC_ALL='C'
ARG JDK_SHA256=39dc809ef8e88eff49d2eaeb48580729888486d56d846559b719da9c545e2884
ARG JDK_NAME=zulu8.74.0.17-ca-jdk8.0.392-linux_x64

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
