# DockerCommands

Image : It is a set of bytes. or a file having memory.

Container : When Image is running.

one image can contain multiple projects.

==============================================
> Run Docker in command prompt
1. ```docker run <image-repository-url>```
Example ```docker run in28min/todo-rest-api-h2:1.0.0.RELEASE```

> Once the ```<containerport>``` is discovered by running command 1 host that port to your local machine port by using following command.
2.```docker run -p <localport>:<containerport> <image-repository-url>```
Example ```docker run -p 8282:5000 in28min/todo-rest-api-h2:1.0.0.RELEASE```

> If we want to run the image in background instead of command prompt then we use following command to detach it from command prompt.
3. ```docker run -p <localport>:<containerport> -d <image-repository-url>```
Example ``` docker run -p 8282:5000 -d in28min/todo-rest-api-h2:1.0.0.RELEASE```

> After running above command we get an image hash key. To see the logs of the project run the below command by putting first four characters of the hash key.
4. ``` docker logs <first-four-characters-id>```
Example ```docker logs a04w```

> To Link the logs in the command prompt use the below command
5. ```docker logs -f <first-four-characters-id>```
Example ```docker logs -f a04w```

> 6. To check what containers are running.
Example:  ```docker container ls```

> 7. Shows the running and stopped containers.
Example ``` docker container ls -a  ```  

#### Note: We can run multiple spring boot applications in docker like we do in normal IDE.

> 8. To check how many images are on the machine.
Example ``` docker images ```

9. ```docker container stop <first-four-characters-id>```
Example ``` docker container stop a09w ```

> To pull something from docker-repository
10.  ``` docker pull <docker-repository>```
Example ``` docker pull mysql ```


> To search any image having a word in it.
11.  ``` docker search <word> ```
Example ```  docker search mysql ```

> 12. To see a history of docker image.
	```  docker image history <image-id> ```
Example ```  docker image history a2141 ```

> To see the complete details of an image
13.  ```	  docker image inspect <image-id> ```
Example ``` docker image inspect a2141 ```

> To Remove a docker image from local machine.
14.  ```  	  docker image remove <image-id> ``` (To see image ids run. ```docker image ls```) 
Example ``` docker image remove a2141 ```


> To Pause a running image(container).
15. ``` docker container pause <container-id>```
Example ```  docker container pause as31 ```


> To UnPause a running image(container).
15.   ``` 	  docker container unpause <container-id>```
Example ```  docker container unpause as31 ```


> To see the complete details of container
16.  	```docker image inspect <container-id>``` To see container ids run. ```docker container ls```
Example ```  docker image inspect as31 ```

> 17.To remove all stopped containers 
Example ```  docker container prune ```

> 18. To see the logs of a specific container.
  ```docker container logs -f <container-id>``` To see container ids run. ```docker container ls```
Example:  ```docker container logs -f q2w1```

> 19. To stop a specific container. This is a normal shutdown after shutting other services down.
```       docker container stop <container-id> ``` To see container ids run. ```docker container ls```
Example  ``` docker container stop q2w1```

> 20. To stop a specific container. This is a imediate shutdown without shutting other services down.
         ``` docker container kill <container-id>```
Example ```  docker container kill q2w1 ```

> Whenever we restart the docker and we want the image to run automatically when we restart the docker.
we use below command.Even if it is closed manually when we restart the docker it runs because it has restart policy defined.
21.	 ``` docker run -p <localport>:<containerport> -d --restart=always <image-repository-url> ```
Example ```  docker run -p 8282:5000 -d --restart=always in28min/todo-rest-api-h2:1.0.0.RELEASE```

> 22.   To see what are the jars or files running in the container.
	```  docker top <container-id> ```   To see container ids run. ```docker container ls```
Example  ```docker top 2qw2```

> 23.   To check the CPU% used and memory consumed by container.
Example ```docker stats```

> To assign a container a specific amount of cpu and memory limit use below command
24.	```  docker run -p <localport>:<containerport> -m <number>m --cpu-quota <number> -d <image-repository-url>```
Example ```  docker run -p 8282:5000 -m 512m --cpu-quota 50000 -d in28min/todo-rest-api-h2:1.0.0.RELEASE ```(It uses 512mb and 50% cpu).
	  
	  cpu-quota (5000 => 5%)


> 25. To see how many images and containers are on the local machine. use below command.
Example. ```docker system df```

## Note

### The Dockerfile content	
<code>
FROM openjdk:8   ==> defines jdk version                                                         
EXPOSE 8080      ==> defines the port                                                            
ADD target/spring-boot-app.jar spring-boot-app.jar    ==> The jar name of the application        
ENTRYPOINT ["java","-jar","/spring-boot-app.jar"] </code>                                               

> To make image of spring boot application run the above Dockerfile by using below commands.

1. ``` docker build -t <spring-boot-application-jar-name> <root>``` which is a dot
```docker build -t spring-boot-app.jar . ```

2.        ```docker run -p <localport>:<containerport> -d <image-repository-url>```
Example:  ```docker run -p 8282:5000 -d in28min/todo-rest-api-h2:1.0.0.RELEASE```






