# Docker-practise-using-springboot
This is a basic Spring Boot application that runs inside a Docker containe

## ☕ JDK Environment

This Docker image uses **OpenJDK 17** on a lightweight Debian base image.

**Base image used in Dockerfile:**
```dockerfile
FROM openjdk:17-jdk-slim
To verify JDK version inside container:
Run:

bash
Copy
Edit
docker ps       # to get container ID
docker exec -it <container_id> java -version

🛠️ 1. Build your Spring Boot app JAR

bash
Copy
Edit
mvn clean package
(or ./mvnw clean package if using wrapper)
👉 This creates something like target/myapp-0.0.1-SNAPSHOT.jar.

🛠️ 2. Create a Dockerfile (in your project root)
Example:

dockerfile
Copy
Edit
FROM openjdk:17-jdk-slim
COPY target/myapp-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
🛠️ 3. Build Docker Image
Run in your project folder:

bash
Copy
Edit
docker build -t my-sb-app:latest .
✅ -t my-sb-app:latest gives it a name and tag
✅ . means build context is current folder

🛠️ 4. Run Docker Container

bash
Copy
Edit
docker run -p 8080:8080 my-sb-app:latest
✅ Maps host port 8080 → container port 8080
✅ Runs your Spring Boot app inside the container

🎯 At this point:
✅ Your image is built locally.
✅ Your app runs in a container on http://localhost:8080.
