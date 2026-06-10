# STAGE 1: Build
FROM maven:3.9-eclipse-temurin-21 AS build
WORKDIR /app
# Copies everything in the current directory (including pom.xml)
COPY . .
RUN mvn clean package

# STAGE 2: Runtime
FROM eclipse-temurin:21-jre-alpine AS runtime
WORKDIR /opt/app
# Copy the built jar from the build stage
COPY --from=build /app/target/*.jar app.jar
USER spring:spring
ENTRYPOINT ["java", "-jar", "app.jar"]
