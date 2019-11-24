FROM java:8

MAINTAINER flagship 124267254@qq.com

VOLUME /tmp

ADD eureka-consumer-1.0-SNAPSHOT.jar app.jar
RUN bash -c 'touch /app.jar'

EXPOSE 8070

ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]