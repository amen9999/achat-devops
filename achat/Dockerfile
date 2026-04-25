FROM openjdk:17-jdk-slim

WORKDIR /app

COPY achat-1.0.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]