# FROM openjdk:17-jdk-alpine AS build
# WORKDIR /workspace/app
#
# COPY mvnw .
# COPY .mvn .mvn
# COPY pom.xml .
# COPY src src
#
# RUN ./mvnw install
#
#
# FROM openjdk:17-jdk-alpine
# #VOLUME /tmp
# ARG JAR_FILE=/workspace/app/target/*.jar
# COPY --from=build ${JAR_FILE} web-server.jar
# EXPOSE 8080
# ENTRYPOINT ["java", "-jar", "/web-server.jar"]


FROM maven:3.8.5-openjdk-17 AS build
COPY ..
RUN mvn clean package -DskipTests

FROM openjdk:17.0.1-jdk-slim
COPY --from=build /target/spring-boot-3-todo-application-0.0.1-SNAPSHOT.jar spring-boot-3-todo-application.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","spring-boot-3-todo-application.jar"]

# Stage 1: Build the application
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