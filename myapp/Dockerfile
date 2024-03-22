FROM maven:3.5-jdk-8-alpine as builder

COPY src /usr/src/myapp/src
COPY ./myapp/pom.xml /usr/src/myapp

RUN mvn -f /usr/src/myapp/pom.xml clean package

# FROM java:8
FROM openjdk:8

COPY --from=builder /usr/src/myapp/target/myapp-1.0.1-SNAPSHOT.jar /usr/app/myapp-1.0.1-SNAPSHOT.jar

ENTRYPOINT ["java", "-cp", "/usr/app/myapp-1.0.1-SNAPSHOT.jar", "com.myapp.App"]