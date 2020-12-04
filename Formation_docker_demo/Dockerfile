FROM maven:3.6.0-jdk-11-slim AS build

COPY src /home/demo/src
COPY pom.xml /home/demo

RUN mvn -f /home/demo/pom.xml clean package


FROM openjdk:11-jre-slim

COPY --from=build /home/demo/target/demo-0.0.1-SNAPSHOT.jar /usr/local/lib/demo.jar

EXPOSE 8080

ENTRYPOINT ["java","-jar","/usr/local/lib/demo.jar"]