# This stage compiles the java application, saving the .jar file to /app/target.
# This avoids you having to install a JDK locally and building the .jar yourself.
FROM azul/zulu-openjdk:21 AS build
WORKDIR /app
COPY . .
RUN ./mvnw package spring-boot:repackage

# This stage copies the .jar file from the `build` stage above to the /app dir,
# to be executed when the container starts. This multi-stage approach means the
# final image only contains the compiled application; none of the other source
# files in this repo.
FROM azul/zulu-openjdk:21-jre
WORKDIR /app
COPY --from=build /app/target/java-hello-world-0.0.1.jar java-hello-world.jar
ENTRYPOINT ["java", "-jar", "/app/java-hello-world.jar"]
EXPOSE 8080
