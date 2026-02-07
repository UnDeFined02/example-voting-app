FROM maven:3.5-jdk-8-alpine AS build

WORKDIR /code

COPY . .

RUN mvn package -DskipTests


FROM eclipse-temurin:8-jre-alpine AS run

WORKDIR /app

COPY --from=build /code/target/*.jar worker.jar

CMD ["java", "-jar", "worker.jar"]
