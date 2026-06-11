# STAGE 1: Build (contains Maven, source code, JDK)
FROM maven:3.9-eclipse-temurin-21 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# STAGE 2: Runtime (only contains JRE and your compiled JAR)
FROM eclipse-temurin:21-jre-alpine
# Update packages to fix the OS vulnerabilities Trivy found
RUN apk update && apk upgrade --no-cache
WORKDIR /opt/app
# Copy ONLY the resulting JAR from the build stage
COPY --from=build /app/target/*.jar app.jar
USER spring:spring
ENTRYPOINT ["java", "-jar", "app.jar"]
