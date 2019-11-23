# Spring Cloud 实践学习案例

> 转载请标明出处：https://windmt.com/tags/Spring-Cloud/ 本文出自 [Yibo's blog](https://windmt.com)

Spring Cloud 实践学习案例，由浅入深一步一步学习 Spring Cloud，是 Spring Cloud 初学者及核心技术巩固的最佳实践。

## Docker 支持

> 如果使用 Docker for Mac 请先参考 https://windmt.com/2019/08/30/docker-for-mac-network/

创建 network

```shell script
docker network create micro-service
```

### Eureka Server

服务注册基本上每次都要用到，为了方便我做了一个 Dockerfile。
使用以下命令可以直接拉取使用镜像：

```shell script
docker run --rm --name eureka-server --network micro-service -p 8761:8761 haoyizebo/eureka-server:latest
```

### Producer

```shell script
docker run --rm --name eureka-producer --network micro-service -p 8080:8080 haoyizebo/eureka-producer:latest
```

### 制作镜像命令
```shell script
docker build -t flagship/eureka-consumer:1.0-SNAPSHOT .
```
```shell script
docker run --rm --name eureka-consumer --network micro-service -d -p 8070:8070 flagship/eureka-consumer:1.0-SNAPSHOT
```
