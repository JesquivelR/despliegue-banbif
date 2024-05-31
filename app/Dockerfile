# Etapa 1: construcción de la app
FROM maven:3.8.1-openjdk-17-slim AS build
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline
COPY src ./src
RUN mvn clean package -DskipTests

# Etapa 2: creación de la imagen para ejecutar la aplicación
FROM openjdk:17.0.1-jdk-slim
WORKDIR /app
COPY --from=build /app/target/helloworld-latest.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]

