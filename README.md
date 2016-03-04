# docker-kubernetes-code-lab

## docker points
* docker share base OS, if redis uses debian os, and if some other image also uses the same OS, then it shares the debian which is already downloaded and running.
* containers by default are stateless
* cgroups is the fundamental container linux tech contributed by google in 2008/9s
*

## kubernetes (kuber-nee-tees)
* container orchestor
*


## Install
* https://www.docker.com/docker-toolbox

## to create machine
docker-machine ls
docker-machine rm <container_name>
docker-machine create --help
docker-machine create -d virtualbox <machine_name>
docker-machine ls

## to set local env variables
docker-machine env local --shell bash
this will return a set of export statement; execute those export statements

## important docker commands
docker
* build - build docker image
* create - create new container
* log - log should never be inside a container
* cp - to cp files between container and local filesystem
* export - export a container filesystem as a tar archive
* history - history of docker image
* login - login to other container registry
* ps - list container
* pull - pull image from registry
* push - push image to registry
* stats
* search - search docker repo
* volume - manage docker volume
* kill - kill container
* docker version

## search for an image for a tool in docker repo

```shell
docker search redis
docker searcg mysql
```

* Search for image in - https://hub.docker.com/explore/
* Look up for official image and refer the documentation for setup. Ex: https://hub.docker.com/_/redis/
* __Note: there is always an official image in the docker repo__


## to pull & run docker image
* to pull image - docker pull redis
* to check for the pull - ```docker images```
* to run docker image - ```docker run redis```
* to directly download and run container
  ```
  docker run -d -P nginx
  ```
* to check the running of docker image -
  ```
  docker run -d redis
  docker ps
  <compare the hash, it should match>
  ```
* __each time one execute docker run <image_name>, the image starts to run__. Run redis 5 times, and check; there will be 5 redis processes running.
* to inspect a process
  ```
  docker inspect e3175bdbe123
  ```
* to kill docker process
  ```
  docker kill aa2fd2110a29
  ```
* to expose port
  * 2 options - '-P' to expose automatically for container; '-p' to expose  container manually
    ```
    docker run -d -P redis
    docker ps
    <check for something similar '0.0.0.0:32768->6379/tcp'>
    ```
* to check docker machine ip - docker ip local
* get the ip and hit with port in the web-browser. ex: http://192.168.99.100:32770/
* to run command inside running conatainer (suggested to do this only in dev & test)
  ```
  docker exec -it <container_id> /bin/bash
  ```
    OR
  ```
  docker-machine start local (or) docker-machine ssh local
  docker ps
  option 1. docker run -it nginx bash (where nginx is the image name)
  option 2. docker exec -i -t 5f81bba39231 bash (where has is the container id)
  ```


## to build docker container
* for java spring boot micro service container, one may use __spotify maven plugin__ to create docker container

## create kubernetes cluster
* may use google cloud web GUI OR refer doc to create locally
* deploy container to kubernetes cluster
* scale up/down the instances
* to load balance 'kubectl expose --type=LoadBalancer', create an internal ip which will be single point of access, which inturn load balance between various instances
* informational links
  * https://youtu.be/7vZ9dRKRMyc!
  * https://github.com/saturnism/spring-boot-docker
  *
* more documentation to setup kubernetes cluster in google cloud - bit.ly/gdgboston-k8s-lab
  * config zone & region for the cluster
  * create a cluster container for ui with number of nodes needed
  * check the nodes 'kubectl get nodes'
  * 
