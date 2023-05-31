#
# Build stage
#
FROM maven:3.9-eclipse-temurin-11-alpine AS build
COPY src /home/app/src
COPY pom.xml /home/app
RUN mvn -f /home/app/pom.xml clean package

#
# Package stage
#
FROM openjdk:18-alpine
COPY --from=build /home/app/target/cicd-0.0.1-SNAPSHOT.jar /usr/local/lib/cicd.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/usr/local/lib/cicd.jar"]