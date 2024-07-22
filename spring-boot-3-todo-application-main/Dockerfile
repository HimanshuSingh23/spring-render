# FROM maven:3.8.5-openjdk-17 AS build
# WORKDIR /app
# COPY . .
# RUN mvn clean package -DskipTests
#
# # Stage 2: Package the application into a smaller image
# FROM openjdk:17.0.1-jdk-slim
# COPY --from=build /app/target/spring-boot-3-todo-application-0.0.1-SNAPSHOT.jar spring-boot-3-todo-application.jar
# EXPOSE 8080
# ENTRYPOINT ["java","-jar","spring-boot-3-todo-application.jar"]


# Stage 1: Build the application
FROM maven:3.8.6-openjdk-17 AS build

# Set the working directory
WORKDIR /app

# Copy the pom.xml and download dependencies
COPY pom.xml .
RUN mvn dependency:go-offline

# Copy the rest of the application code
COPY src ./src

# Package the application
RUN mvn clean package -DskipTests

# Stage 2: Create a smaller image with the packaged application
FROM openjdk:17-jdk-slim

# Set the working directory
WORKDIR /app

# Copy the JAR file from the build stage
COPY --from=build /app/target/your-app-name.jar app.jar

# Expose the port that the application runs on
EXPOSE 8080

# Command to run the JAR file
ENTRYPOINT ["java", "-jar", "app.jar"]