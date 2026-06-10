# Use Java 17 (Temurin), required for Spring Boot 3+
FROM eclipse-temurin:17-jre-alpine

# The artifact path
ARG artifact=target/spring-boot-web.jar

WORKDIR /opt/app

# Create non-root user
RUN addgroup -S spring && adduser -S spring -G spring

# Copy the JAR file and explicitly assign ownership to the 'spring' user
# This prevents 'Permission Denied' errors when the container starts
COPY --chown=spring:spring ${artifact} app.jar

# Run the application as the non-root user
USER spring:spring

ENTRYPOINT ["java","-jar","app.jar"]
