# Docker
Learning Docker

# What is Docker?
Is a Social Platfrom for you to find and share containers(not vm)

# What is Container?
container is a running instance of an image
Contains the environment/dependencies to run your code

## List running containers:
```
sudo docker ps 
```
![image](https://user-images.githubusercontent.com/51336081/187316194-904b38f5-fadb-4079-9550-20fbd6666da8.png)

## Pull Container:
```
sudo docker run nginx:latest
```
##Run container in detached mode:
to run container in background without waiting for input
```
sudo docker run -d nginx:latest
```

## stop container:
```
sudo docker stop <container_id>
```
## exposing port: port mapping from host ---to---> container:
```
sudo docker run -d -p 8080:80 nginx:latest
```
this will run run the container on port 8080
![image](https://user-images.githubusercontent.com/51336081/187317192-5e51f3c8-4a9f-42a2-b7c4-67e3546ce202.png)
## Exposing multiple ports:
![image](https://user-images.githubusercontent.com/51336081/187318648-f830b3e7-e113-44bc-90e2-146f8661fb1f.png)

view the running containers:
```
sudo docker ps
```
![image](https://user-images.githubusercontent.com/51336081/187318771-cd87f6b3-9b1d-4e8f-99b7-30315bde9fe1.png)

![image](https://user-images.githubusercontent.com/51336081/187317667-b8546026-6d07-48c4-9645-ba0d6b86fdc0.png)

![image](https://user-images.githubusercontent.com/51336081/187317680-52ab9dfc-b4ef-4527-9ad5-40a88d6a006c.png)

## List all containers active and stoped:
```
sudo docker ps -a
```
![image](https://user-images.githubusercontent.com/51336081/187319161-120fec28-db70-4c8c-b737-5b4cb796a5b9.png)

## remove container

stop != remove
to remove:
```
docker rm <id>
```

## Naming Container
```
sudo docker run --name mongo -d nginx:latest
```

## How to share data between the host and container or between containers
Using **Volumes**
1-create directory in host to be shared with container
```
mkdir webApp
```
2-create html file(must be named index.html to override the nginx one)
```
touch index.html
```
3-open it and start editing then save it ctrl+s:
```
<html>
<h1>Hello, i am nginx!</h1>
</html>
```
4-create container with volum
```
sudo docker run --name website -v $(pwd):/usr/share/nginx/html -d -p 8080:80 nginx:latest
```
we can make it read only be from the prespective of the container
```
sudo docker run --name website -v $(pwd)/usr/share/nginx/html:ro -d -p 8080:80 nginx:latest
```
5-open browser and navigate to localhost:8080

![image](https://user-images.githubusercontent.com/51336081/187367230-07621171-8217-4075-9487-cd506b1ffdd9.png)

**Then any changes in the current dir takes place in the container and vise-versa in case on not read-only**

## Execute Commands inside the container
```
docker exec -it <contaner_name> bash 
```
