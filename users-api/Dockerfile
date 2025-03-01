# Java Spring Boot Users API
FROM maven:3.8.6-openjdk-11 AS builder
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn package -DskipTests

FROM openjdk:8-jre-slim
WORKDIR /app
COPY --from=builder /app/target/*.jar ./users-api.jar
EXPOSE 8083
CMD ["java", "-jar", "users-api.jar"]