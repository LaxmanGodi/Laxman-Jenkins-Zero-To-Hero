# Updated to use Java 17 (Temurin), which is required for Spring Boot 3+
FROM eclipse-temurin:17-jre-alpine

# The artifact path
ARG artifact=target/spring-boot-web.jar

WORKDIR /opt/app

# It is good practice to add a non-root user for security
RUN addgroup -S spring && adduser -S spring -G spring
USER spring:spring

# Copy the JAR file built in the previous stage
COPY ${artifact} app.jar

# Run the application
ENTRYPOINT ["java","-jar","app.jar"]
