# CI/CD Automation Process 
(Under Development)Includes Scripts for CI/CD using Jenkins, Docker and GitHub in AWS(Amazon Web Services) EC2 Cloud Infrastructure.

First I am running the whole webapp manually in docker containers, perform some scaling operations using Kubernetes. 
After that I will Automate the whole process and make a CI/CD environment for my webapp(WorkHub) using Jenkins-pipeline with Docker, Kubernetes and Git.

## 1. Manual steps for running WorkHub in Docker Containers 

### WorkHub Server Docker image
The workhub web-app from my repo is converted inot docker image and it is uploaded in DockerHub.
The link to DockerHub repository is:
*.    https://hub.docker.com/r/manilpuri9/workhub/  .*

1. Run pull command in your server: 
*    docker pull manilpuri9/workhub      *

2. Run the downloaded image as:

*    docker run -it -p 80:5000 workhub:v1 *

Upto here the server is running without the database.
And here is the image of database:
https://hub.docker.com/r/manilpuri9/database/
1. Run pull command in your server:

* docker pull manilpuri9/database  *

2. Run the downloaded image as:



