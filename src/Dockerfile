FROM ubuntu:latest AS build

RUN apt-get update
RUN apt-get install openjdk-17-jdk -y
WORKDIR /app
COPY spring-verzel-plus/pom.xml /app/
COPY spring-verzel-plus/ /app/

RUN apt-get install maven -y
RUN mvn clean install

FROM openjdk:17

EXPOSE 8080

COPY  --from=build /target/verzel-plus-0.0.1-SNAPSHOT.jar app.jar

ENTRYPOINT [ "java", "-jar", "app.jar"]