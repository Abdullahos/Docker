# Docker
Learning Docker

# What is Docker?
Is a Social Platfrom for you to find and share containers(not vm)

# What is Container?
container is a running instance of an image
Contains the environment/dependencies to run your code

## List running containers:

sudo docker ps 
![image](https://user-images.githubusercontent.com/51336081/187316194-904b38f5-fadb-4079-9550-20fbd6666da8.png)

## Pull Container:

sudo docker run nginx:latest

##Run container in detached mode:
to run container in background without waiting for input
sudo docker run -d nginx:latest

## stop container
sudo docker stop <container_id>

## port mapping from host ---to---> container

sudo docker run -d -p 8080:80 nginx:latest
this will run run the container on port 8080
![image](https://user-images.githubusercontent.com/51336081/187317192-5e51f3c8-4a9f-42a2-b7c4-67e3546ce202.png)

