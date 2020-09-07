## Bind Mounts

## Overview

- Bind mounts are a basic way to share files from a folder between the host machine and a container
- They are best suited for when you have one file or one directory that you need to share from your host machine's file system to the container
- By the end of this module, you should understand:
    - Why we use bind mounts
    - When a bind mount is most appropriate
    - How to use a bind mount

## Use Case

- NGINX is an application with a number of different functionalities:
    - Static web server
    - Reverse proxy
    - Load balancer
- It uses a configuration file called nginx.conf to define its functionality
- To configure an NGINX container, we have two options based on what we've learnt so far:
    - Use `docker exec -it [CONTAINER_NAME] bash` to execute a command to change the configuration file
        - This is long-winded and time consuming
    - Create a Dockerfile that uses the NGINX image as its base layer, then use `COPY` to copy the .conf file into the image
        - This will require you two create a whole new image on your host machine that is almost identical to the original NGINX image, with only the one file changed
        - Essentially result in duplicate image files
- What if we could instead run the NGINX image as normal, but copy in just the one file into the container at runtime?

## Bind Mounts

- Bind mounts are an old feature in Docker that allow you to copy a single file or directory into a container
- They are best suited for containers where you only want to make minor changes to the functionality of your contianers
- They are **not** well suited for when you need to make significant changes to the file structure of your container
    - You should consider building a new image with a Dockerfile or using a volume

### Command
(ignore the --volume flag for this section)

- You can perform a bind mount using the --mount flag when running the `docker run` command
    - Options:
        - source
        - target
        - destination
        - type
        - readonly

## Tutorial

- Current tutorial is fine - bind mounting a .conf file into NGINX

## Exercises

1. Trio task: bind mount the nginx.conf file onto the NGINX container and run the NGINX container and the Flask app together (either the static or database app). Run `curl localhost` -- you should see the web page from the flask app.