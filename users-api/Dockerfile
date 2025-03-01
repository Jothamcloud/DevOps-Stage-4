FROM eclipse-temurin:17-jdk
WORKDIR /app

COPY target/users-api.jar users-api.jar

ARG SERVER_PORT
ARG JWT_SECRET
ENV SERVER_PORT=8083
ENV JWT_SECRET=myfancysecret

EXPOSE 8083
CMD ["java", "-jar", "users-api.jar"]