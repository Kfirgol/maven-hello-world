FROM maven:3.5-jdk-8-alpine as builder 

COPY src /usr/src/myapp/src 
COPY pom.xml /usr/src/myapp

RUN mvn -f /usr/src/myapp/pom.xml clean package 

FROM openjdk:8 

ARG VERSION
ENV VERSION ${VERSION}

COPY --from=builder /usr/src/myapp/target/myapp-$VERSION.jar /usr/app/myapp-$VERSION.jar 

ENTRYPOINT java -cp /usr/app/myapp-$VERSION.jar com.myapp.App
