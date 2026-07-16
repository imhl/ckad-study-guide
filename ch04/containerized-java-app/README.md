# Building the Docker Image

The Docker image contains two stages.

One stage comprises a Java Development Kit (JDK 21) image, and compiles the application into a JAR file. This stage obviates you needing to install a JDK environment locally and building the app yourself.

The other stage holds a Java Runtime Environment (JRE 21) image. This stage copies the compiled JAR from the build stage and runs the application.

To build the image, run the following command:

```
$ docker build -t java-hello-world:1.0.0 .
```