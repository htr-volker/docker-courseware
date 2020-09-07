## Networking

### Overview

- This modules introduces the concept of networking Docker containers
- For containers to be able to communicate with one another, they need to be placed on the same network
- By the end of this module, you should understand:
    - Why we use networks for Docker containers
    - The different types of networks in Docker
    - The main features of **bridged networks**
    - How to create a bridged network and connect containers to it to allow them to communicate

### Use Case

- By default, containers cannot communicate directly with one another
    - They are instead attached to the Docker **host** network, which connects the container to the host machine's network (say a private network or the internet)
- This is fine for monolithic applications, but poses an issue for microservice applications
    - e.g. if you have a frontend container and a backend container, where the frontend handles the incoming network traffic and calls the backend to make database queries
- Instead, we must create our own **networks**

### Network Types

- There are four network types in Docker
    - Host network
        - Interfaces containers with wider networks
        - Ports get published to the host
        - Diagram
    - Bridged network
        - Used for connecting containers together on a single host
        - More information in the bridged network section
        - Diagram
    - Overlay network
        - Allows for network connectivity across multiple host machines (or **nodes**)
        - Used by Docker Swarm
        - Diagram
    - Macvlan network
        - Some legacy tools for monitoring network traffic require *physical networks* to interface with the network
        - However, networks in Docker are *virtual networks*
        - Macvlan networks are designed to simulate this *physical network* structure, giving your containers MAC addresses
        - Doesn't need a diagram
- The main type we focus on in this module is **bridged networks**

### Bridged Networks

- Bridged networks are used to connect containers together on the same machine
- The main features of bridged networks are:
    - Isolated networks
    - Automatic DNS resolution
    - Connect/Disconnect containers easily

### Managing Networks

- CLI commands
    - This can stay the same as it is right now

### Tutorial

- Two containers: NGINX and a static Python app
    - Python app should be in an image you can pull down from docker hub
    - NGINX will reverse proxy redirect http traffic to the python app on 5000
    - Change the configuration of the NGINX container by exec-ing in rather than using a bind mount (because bind mounts are introduced in a later module)

### Exercises

1. Get the static Flask app in the Trio Task working with NGINX as a reverse proxy
2. Get the database Flask app in the Trio Task wokring with NGINX **and** a MySQL container