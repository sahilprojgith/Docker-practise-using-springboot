FROM openjdk:17-jdk-slim-bullseye
WORKDIR /app
COPY target/rest-demo.jar rest-demo.jar
EXPOSE 8080
CMD ["java", "-jar", "rest-demo.jar"]