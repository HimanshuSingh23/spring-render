FROM maven:3.8.5-openjdk-17 AS build
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Stage 2: Package the application into a smaller image
FROM openjdk:17.0.1-jdk-slim
COPY --from=build /app/target/spring-boot-3-todo-application-0.0.1-SNAPSHOT.jar spring-boot-3-todo-application.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","spring-boot-3-todo-application.jar"]