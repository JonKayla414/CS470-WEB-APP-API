# LAFS-API and LAFS-WEB with Docker

This is was published to document my docker learning experience with repositories from [AngularTemplates/learn-angular-from-scratch](https://github.com/AngularTemplates/learn-angular-from-scratch-step-by-step) and [AnglularTemplates/learn-how-to-build-a-mean-stack-application](https://github.com/AngularTemplates/learn-how-to-build-a-mean-stack-application)


## Getting started
**Download the Prerequisites**
 - [ ] [Docker](https://www.docker.com/products/docker-desktop/)
 
 - [ ] Follow the tutorials linked above for lafs-web and lafs-api.

 

## Docker

 1. Create a default MongoDb Docker image : `docker pull mongo`
 
 2.  Run the docker image:  `docker run -d -p 27017-27019:27017-27019 --name mongodb mongo`
**Once you the repo and submodules:** 
*note you must ensure you are in lafs-web*


 3.  Build you docker image for lafs-web: `docker build -t node-lafs-web .`
 
4. Run your container: ` docker run -p 4200:4200 -d node-lafs-web`
 *note you must ensure you are in lafs-api*
 
 5.  Build you docker image for lafs-api: `docker build -t node-lafs-api .`
 6.   Run your container: ` docker run -p 3000:3000 -d node-lafs-api` 
 
 *(This will most likely exit with 1; or you will not be able to access your webapplication at localhost:3000 this is becayse you must make a bridge for the container to see mongodb and your network)*
 

7.  create a bridge network: `docker network create --driver bridge lafs-net `
8. Create your docker-compose yml file for each lafs-web and lafs-api. Bring up the docker containers in the respective directories: `docker-compose up`

 


#### Useful comands: 

 - View the list of installed docker image:  `docker images`
 
 - Execute commands with the running container: `docker exec -it [name of container] bash` 
  *note thhat that 'it' means it will run interactively ; the input/output will be reflected on your local terminal. 'bash' is the name of the command to execute.*
  - Show the list of network in docker: `docker network list`
  - Show the list of all Docker containers running: `docker ps -a`
	 

