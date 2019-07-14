FROM openjdk:8-jdk-alpine
EXPOSE 8080
ADD target/todo-app.jar todo-app.jar
ENTRYPOINT ["java", "-jar", "/todo-app.jar" ]