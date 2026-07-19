FROM azul/zulu-openjdk:21 AS build
WORKDIR /app
COPY . .
RUN ./mvnw package spring-boot:repackage

FROM azul/zulu-openjdk:21-jre
WORKDIR /app
COPY --from=build /app/target/java-hello-world-0.0.1.jar java-hello-world.jar
ENTRYPOINT ["java", "-jar", "/app/java-hello-world.jar"]
EXPOSE 8080
