FROM maven:latest as build-stage
WORKDIR /app
COPY projeto-maven .
RUN mvn clean
RUN mvn package

FROM openjdk:11 as run-stage
WORKDIR /java
ARG JAR_FILE_NAME=springapp.jar
ENV JAR_NAME=$JAR_FILE_NAME
COPY --from=build-stage /app/target/$JAR_FILE_NAME .
ENTRYPOINT java -jar $JAR_NAME