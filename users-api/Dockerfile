FROM maven:3.8.6-openjdk-11 AS build

WORKDIR /app

# Copy pom.xml
COPY users-api/pom.xml .

# Download dependencies (this layer can be cached)
RUN mvn dependency:go-offline -B

# Copy source code
COPY users-api/src ./src

# Build the application
RUN mvn package -DskipTests

# Final stage
FROM openjdk:11-jre-slim

WORKDIR /app

# Copy JAR from build stage
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8083

CMD ["java", "-jar", "app.jar"]