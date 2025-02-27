# Use Java Runtime Environment (JRE 8) as the base image
FROM openjdk:8-jre

# Set the working directory inside the container
WORKDIR /app

# Copy the compiled JAR file into the container
COPY target/users-api-0.0.1-SNAPSHOT.jar /app/users-api.jar

# Expose the port the service runs on
EXPOSE 8083

# Run the Users API microservice
CMD ["java", "-jar", "/app/users-api.jar"]
