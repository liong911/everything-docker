# everything-docker

提供腾讯云环境的基础镜像和构建环境镜像

> 底层基础镜像采用ubuntu:focal

# dockerfile

## JDK

> jdk安装目录：/opt/jdk/

### zulu-jdk8

```bash
docker pull ccr.ccs.tencentyun.com/everything/zulu-jdk8
```

### zulu-jdk11

```bash
docker pull ccr.ccs.tencentyun.com/everything/zulu-jdk11
```

## build-tool构建工具

> jdk安装目录：/opt/jdk/ \
> maven安装目录：/opt/maven/ \
> node安装目录：/opt/node/ 

### jdk8+maven+node16

```bash
docker pull ccr.ccs.tencentyun.com/everything/build-tool:jdk8-maven-node16
```
