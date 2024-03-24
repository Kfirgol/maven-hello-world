# find better base image
FROM maven:3.5-jdk-8-alpine as builder 

COPY src /usr/src/myapp/src # find a way to remove src before next FROM statement
COPY pom.xml /usr/src/myapp

# understand if creating jar inside dockerfile can cause problems - maybe you want to keep the jar?
RUN mvn -f /usr/src/myapp/pom.xml clean package 

# FROM java:8
# find better base image
FROM openjdk:8 

ARG VERSION
ARG VERSION ${VERSION}

# understand this command
COPY --from=builder /usr/src/myapp/target/myapp-$VERSION.jar /usr/app/myapp-$VERSION.jar 

ENTRYPOINT ["java", "-cp", "/usr/app/myapp-$VERSION.jar", "com.myapp.App"] # figure out if this needs to be com.myapp.app.App