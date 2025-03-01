# Build stage
FROM maven:3.8.4-openjdk-8 AS build-stage
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn package -DskipTests

# Run stage
FROM openjdk:8-jre-slim
WORKDIR /app
COPY --from=build-stage /app/target/users-api-0.0.1-SNAPSHOT.jar ./users-api.jar
EXPOSE 8083
CMD ["java", "-jar", "users-api.jar"]
