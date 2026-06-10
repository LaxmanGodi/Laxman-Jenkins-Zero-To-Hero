# STAGE 1: Build (contains Maven, Git, etc.)
FROM maven:3.9-eclipse-temurin-21 AS build
WORKDIR /app
COPY . .
RUN mvn clean package

# STAGE 2: Runtime (The clean, secure image)
FROM eclipse-temurin:21-jre-alpine AS runtime
WORKDIR /opt/app
# We "call" or pull the artifact from the 'build' stage into this 'runtime' stage
COPY --from=build /app/target/*.jar app.jar
USER spring:spring
ENTRYPOINT ["java", "-jar", "app.jar"]
