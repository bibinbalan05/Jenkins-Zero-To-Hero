# Build Stage
FROM maven:3.8.6-openjdk-11 AS builder
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# Run Stage
FROM adoptopenjdk/openjdk11:alpine-jre
WORKDIR /opt/app
COPY --from=builder /app/target/spring-boot-web.jar app.jar

ENTRYPOINT ["java","-jar","app.jar"]
