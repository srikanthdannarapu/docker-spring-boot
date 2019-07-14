##### docker-spring-boot

1. Install Docker desktop

https://hub.docker.com/editions/community/docker-ce-desktop-windows

2. Create a `Dockerfile` for creating a docker image from the Spring Boot Application
`FROM openjdk:8
ADD target/todo-app.jar todo-app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/todo-app.jar"]`

3. Navigate to project root folder from cmd

cd C:\SRIKANT\workspace2\docker

4. docker build -t todo-app.jar .

5. docker run -p 9000:9000 todo-app.jar

6. Troubleshooting

If you get this error

docker: Error response from daemon: driver failed programming external connectivity on endpoint festive_jones (c9ca5db563637a5b84a1b5ce2842d7222bdbe01518c7a5753ac4a1827d51bfe6): Error starting userland proxy: mkdir /port/tcp:0.0.0.0:9000:tcp:172.17.0.2:8080: input/output error.
uncheck 
Then, turn off "Start Docker desktop when you log in" in the docker setting.
Finally, start the docker manually (you don't have to restart).

refer https://github.com/docker/compose/issues/3277


6. on cmd 
```
- docker login 

- Give credentials

- docker image ls

- docker tag todo-app.jar srikanth1545/todo-app.jar
- docker push srikanth1545/todo-app.jar

- docker image will be pushed to repo on docker hub (https://hub.docker.com/r/srikanth1545/todo-app.jar)
- docker pull srikanth1545/todo-app.jar
- docker run -p 9000:9000 todo-app.jar

```
#### Some docker commands to play around

```
   docker run srikanth1545/todo-app.jar:latest
   docker run -p 5000:9000 todo-app.jar:latest
   clear
   docker run -p 8761:8761 springcloud/eureka
   clear
   docker run -d -p 5000:9000 srikanth1545/todo-app.jar:latest
   docker run -d -p 8761:8761 springcloud/eureka
   docker images
   docker containers 
   docker containers ls
   docker container
   docker container ls
   docker container ls -l
   docker container ls -l
   docker container ls
   docker container ls -a
   clear
   docker container ls -a
   docker container start fed549e69e9d
   docker container ls
   docker container stop tender_ardinghelli
   docker container ls
   docker container ls -a
   clear
   docker container ls -a
   docker container start c165f459e7d7
   docker container stop 151a77679241
   docker container start c165f459e7d7
   docker container logs c165f459e7d7
   docker container logs c165f459e7d7
   docker container logs c165f459e7d7
   docker container logs c165f459e7d7
   docker container ls
   docker container ls -a
   docker container rm fed549e69e9d
   docker container ls -a
   docker container prune
   docker container ls -a
   docker container inspect 0967ba7aa180
   docker images
   docker image history f8049a029560
   clear
   docker images
   docker image history srikanth1545/todo-app.jar
   docker image history srikanth1545/todo-app.jar:latest
   docker images
   docker image remove f8049a029560
   docker image remove 3094afcbdf12
   docker container stop c165f459e7d7
   docker image remove 3094afcbdf12
   docker container rm c165f459e7d7
   docker image remove 3094afcbdf12
   docker images
   docker containers ls
   docker container ls
   docker container ls -a
```

#### Hello World URLS

- http://localhost:9000/hello-world

```txt
Hello World
```

- http://localhost:9000/hello-world-bean

```json
{"message":"Hello World - Changed"}
```

- http://localhost:9000/hello-world/path-variable/Srikanth

```json
{"message":"Hello World, Srikanth"}
```


#### Todo JPA Resource URLs

- GET - http://localhost:9000/jpa/users/Srikanth/todos

```
[
  {
    "id": 10001,
    "username": "Srikanth",
    "description": "Learn JPA",
    "targetDate": "2019-06-27T06:30:30.696+0000",
    "done": false
  },
  {
    "id": 10002,
    "username": "Srikanth",
    "description": "Learn Data JPA",
    "targetDate": "2019-06-27T06:30:30.700+0000",
    "done": false
  },
  {
    "id": 10003,
    "username": "Srikanth",
    "description": "Learn Microservices",
    "targetDate": "2019-06-27T06:30:30.701+0000",
    "done": false
  }
]
```

##### Retrieve a specific todo

- GET - http://localhost:9000/jpa/users/Srikanth/todos/10001

```
{
  "id": 10001,
  "username": "Srikanth",
  "description": "Learn JPA",
  "targetDate": "2019-06-27T06:30:30.696+0000",
  "done": false
}
```

##### Creating a new todo

- POST to http://localhost:9000/jpa/users/Srikanth/todos with BODY of Request given below

```
{
  "username": "Srikanth",
  "description": "Learn to Drive a Car",
  "targetDate": "2030-11-09T10:49:23.566+0000",
  "done": false
}
```

##### Updating a new todo

- http://localhost:9000/jpa/users/Srikanth/todos/10001 with BODY of Request given below

```
{
  "id": 10001,
  "username": "Srikanth",
  "description": "Learn to Drive a Car",
  "targetDate": "2045-11-09T10:49:23.566+0000",
  "done": false
}
```

##### Delete todo

- DELETE to http://localhost:9000/jpa/users/Srikanth/todos/10001


#### H2 Console

- http://localhost:9000/h2-console
- Use `jdbc:h2:mem:testdb` as JDBC URL 