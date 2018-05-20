# CI/CD Automation Process 
(Under Development)Includes Scripts for CI/CD using Jenkins, Docker and GitHub in AWS(Amazon Web Services) EC2 Cloud Infrastructure.

First I am running the whole webapp manually in docker containers, perform some scaling operations using Kubernetes. 
After that I will Automate the whole process and make a CI/CD environment for my webapp(WorkHub) using Jenkins-pipeline with Docker, Kubernetes and Git.

## 1. Manual steps for running WorkHub in Docker Containers 

The workhub web-app from my repo is converted inot docker image and it is uploaded in DockerHub.
The link to DockerHub repository is:
   https://hub.docker.com/r/manilpuri9/workhub/ 

1. Run pull command in your server: 
 *  docker pull manilpuri9/workhub      

2. Run the downloaded image as:

*   docker run -it -p 80:5000 workhub:v1
   I.   Go inside the container
      * docker exec -it <containerID> bash
   II.  Run the app.py file inside Workhub folder
      * python app.py

Upto here the server is running without the database. Just to check if our server is serving properly.
Go to your browser and type localhost. You must be able to see the homepage of WorkHub.

And here is the image of database:
https://hub.docker.com/r/manilpuri9/database/
3. Run pull command in your server:
* docker pull manilpuri9/database

If you pull mysql:v2.1 all the configration are done previously so you can skip to step 7

* docker pull manilpuri9/mysql:v2.1  


4. Run the downloaded image as:
 docker run --name sql -e MYSQL_ROOT_PASSWORD=my-secret-pw -v <path of your mysqldumpfile.sql>:/root/ -it mysql
 In my case:
*   docker run --name sql -e MYSQL_ROOT_PASSWORD=my-secret-pw -v /home/manil/Documents/git/WorkHub/:/root/ -it mysql
5. Go inside the container
*   docker exec -it <containerID> bash
6.  Create a database using mysql as:
*   mysql -u root -p myflaskapp < workhubdatadump.sql

7. Stop and remove the running docker container that we created on step 1
*  docker stop <containerID>
*  docker rm <containerID>

8. Start it again but this time we link it to the running database container that we ran in step 5
*  docker run --link sql:mysql -it -p 80:5000 -v /home/manil/Documents/git/WorkHub:/root/ manilpuri9/workhub:v1

###### At this point you must have a running webapp Workhub in your machine at port 80. Go to the browser and type localhost

## 2. Running my portfolio site in Docker Swarm & Kubernetes Cluster
   Now for High Availability and Horizontal Scaling, we will be running my 


