# Swarm Ingress

## Overview
- As containers in a swarm are created and run across multiple nodes in a Swarm, there needs to be a way for network traffic to be balanced across containers and nodes
- This module discusses how Docker Swarm uses a routing mesh to balance and redirect its incoming traffic (ingress) across containers within a cluster
- It also illustrates how to use a load balancer to balance traffic across multiple nodes, making use of each of their address space

## Network Mesh
- When a service is created, its containers are distributed evenly across nodes in a cluster
- If a container within one service needs to communicate with another in order to function (such as a frontend service making an API call to a backend service), it is highly likely that the other container will be on another node
- Similarly, if there are many replicas of a web application's frontend application within a Swarm, incoming networking traffic should be making use of all of these replicas, regardless of which machine the request is being routed to
- Swarm's *network mesh* or *routing mesh* creates a network that connects all containers in a Swarm across nodes and balances ingress traffic across each of them
- Within each node is a load balancer, which can balance traffic across any container within the cluster - this means that you could make an HTTP request to a worker node and have your request redirected to a container on the manager node, and vice versa, or another worker node!

## Load Balancing Across Nodes
- Swarm balances traffic across containers within the cluster, but can't balance requests across each node's network namespace
- To achieve this, we need a separate load balancer
- NGINX is a popular web server tool with multiple functionalities, including as a reverse proxy and as a load balancer
- Its functionality can be configured through editing its `nginx.conf` file
- Below is a configuration for load balancing across two nodes in a Swarm for a basic web server
    - Show the code block
- Let's break it down
    - upstream
        - This section handles the load balancing
        - We are effectively grouping together the nodes in our swarm - we specify the private IP addresses
        - We can then refer to any of these IP addresses using the name of the upstream
    - server
        - Here we are specifying a proxy pass that will redirect incoming traffic at a particular location to the upstream (group of IP addresses)
- Benefits of our external load balancer
    - Makes use of each of our nodes' network namespaces while the user only has to utilise one, so no one machine is having to process incoming requests
    - Allows us to keep our cluster entirely disconnected from the internet, making the Swarm much more secure

## Tutorial
- Rework the exercise into a tutorial

## Exercise
- Get the following into a Swarm cluster with an NGINX load balancer
    - 1 Manager and 1 Worker running the Duo Task servives, 2 replicas for each service
    - 2 Managers and 2 Workers running the Trio Task in services, 5 replicas for each service and a volume to persist the database contents
