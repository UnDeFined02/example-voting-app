FROM maven:3.5-jdk-8-alpine AS build

WORKDIR /code
COPY . .
RUN mvn clean package -DskipTests

FROM eclipse-temurin:8-jre-alpine

WORKDIR /app
COPY --from=build /code/target/*jar-with-dependencies.jar worker.jar

CMD ["java","-jar","worker.jar"]
