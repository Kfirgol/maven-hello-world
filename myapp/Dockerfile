FROM maven:3.5-jdk-8-alpine as builder

# WORKDIR ./myapp
RUN whoami
COPY src /usr/src/myapp/src
COPY pom.xml /usr/src/myapp

RUN mvn -f /usr/src/myapp/pom.xml clean package

# FROM java:8
FROM openjdk:8

COPY --from=builder /usr/src/myapp/target/myapp-$VERSION.jar /usr/app/myapp-$VERSION.jar

ENTRYPOINT ["java", "-cp", "/usr/app/myapp-$VERSION.jar", "com.myapp.App"]