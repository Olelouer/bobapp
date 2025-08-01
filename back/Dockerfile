FROM maven:3.9-eclipse-temurin-11 AS build
WORKDIR /workspace
COPY pom.xml .
COPY src ./src
RUN mvn -B -f pom.xml clean package -DskipTests

FROM eclipse-temurin:11-jre-focal
WORKDIR /app
COPY --from=build /workspace/target/*.jar app.jar
EXPOSE 8080
USER 1001
ENTRYPOINT ["java", "-jar","app.jar"]
