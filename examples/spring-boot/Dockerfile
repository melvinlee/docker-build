
FROM maven:3.5-jdk-8 as BUILDER

COPY src /app/src
COPY pom.xml /app
RUN mvn -f /app/pom.xml clean package

FROM openjdk:8-jdk-alpine

COPY --from=BUILDER /app/target/gs-spring-boot-0.1.0.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]