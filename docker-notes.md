Delegate criticism:
- tutorial should be more stuctured and less mechanical
- you can go through a tutorial with just copy and paste and without more explaination
- little bit more structured
- a lot of modules have tutorials and no exercises
- Cloud Academy has better material - Ben Lambert and Logan Rakai
- docker stuff was alot more difficult
- A few grammatical errors/missing words in the courseware
- Struggling to understand new modules
- maybe more examples or tutorials on subjects that are known to be harder

My criticism:
- Too many exercises surrounding Jenkins in a container -- not something we want people to be using, seems a little pointless
- No discussion of how to run up a MySQL container, which is something we'd like them to be able to do

Suggestions:
- Use a running mini-project from day 1 of Docker to help them contextualise their learning in a working context
	- This could be the trio-task
- Diagrams -- show how imges are layered in a visual way
- Every time there is a Jenkins exercise

## Introduction
- It's fine

## Images
- Diagrams illustrating how images are layered

## Containers
- Diagram?
- Add section on setting environment variables

## Dockerfiles
- 

## Dockerfile Instructions
- Exercise: get the flask app in trio task to run in a container
	- Will have to create a new app.py (static.py) for a static web app
- Stretch goal: attempt to get the MySQL db in a container too -- look up the documentation online for MySQL image
	- Hint: take note of the environment variables you can assign
	- Hint: use 'docker exec -it [DB_CONTAINER_NAME] mysql' to log into the container
- Strechier goal: get your SFIA1 apps running in a container

## Dockerignore
- 

## Multi stage builds
- Read through the documentation for reference first: https://docs.docker.com/develop/develop-images/multistage-build/
- Structure:
	- Problem:
		- Some languages require compiling before you can execute code (e.g. Java)
		- It is beneficial to use the build tool (e.g. Maven) in a container to keep build environment consistent
		- However, once app is compiled, source code and build tool are useless to the actual execution of the app
		- This takes up space on the container, eating up resources (memory) and slowing down deployment of containers
	- Solution:
		- We can compile our code in a temporary container (Maven)
		- Copy executable files (e.g. .jar files) into the container with the runtime engine
		- Dump the build stage container
		- A nice diagram wouldn't go amiss here
	- Dockerfile syntax
		- Step by step on how to copy code from one container to another
		- Talk about how build stages increment from 0 by default
		- --from=[STAGE] flag for COPY
		- Naming build stages with AS (e.g. FROM maven:latest AS build-stage)
	- Tutorial
		- Add build stage name to dockerfile
		- Otherwise quite happy to keep the same
		- Free reign to edit as you see fit

## Networking
- Diagram showing how a bridged network connects containers (maybe also one for overlays)
- Exercise: get the MySQL container in the trio task up and running, change the flask app to run database.py. Get them to work together on the same network.

## Registries
- Diagram showing images being pulled down from registries if they don't exist on the host machine

## Bind Mounts
- Trim down some of the fat - only show them the --mount flag
	- Maybe show a quick link to the documentation on the volume flag
- Change this exercise - not sure to what yet, it currently makes no sense to me
	- I guess "Run up an NGINX container with the flask app in the trio task. Use a bind mount to attach the nginx.conf file to the NGINX Container. Read the .conf file -- what is it doing?"

## Volumes
- Diagram showing how volumes mount to containers
- Section on the main features of volumes:
	- Persist data across multiple containers
	- Completely managed by docker
	- Multiple containers can mount the same volume at the same time
- Exercise: persist the contents of the trio task MySQL container using a volume

## Docker Compose Intro
-

## Docker Compose CLI
- Is it worth doing CLI after configuration??

## Docker Compose Configuration
- Environment variable section
- Replicas section
- Exercise: write a docker-compose.yaml file for your trio task

## Docker Swarm
- Diagrams!!!!
- More benefits of Swarm -- contexualise why we do this

## Swarm CLI
- Tutorial: turn the exercise into a tutorial (preferably without Jenkins)
- Exercise: get the trio task flask app to run as a Swarm service

## Swarm Ingress
- Tutorial: turn exercise into tutorial
- Exercse: ???

## Swarm Stack
- Tutorial: take some inspiration from the exercise and adapt it into a tutorial
- Exercise: get your trio task running with a Swarm with 10 replicas of the flask application
	- Hint: should your NGINX container be part of the swarm??