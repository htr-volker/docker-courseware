# Swarm Introduction

## Overview
    - 
    
## Container Orchestration
    - Using Docker CLI and Compose allows us to containerise our applications and deploy them on a machine fairly simply
    - Once we get to deploying in an actual production environment where we're potentially serving hundreds, thousands or millions of users, we're going to need a solution that can work at a much bigger scale
    - In order to deploy and manage our containers at scale, we need to use a container orchestration tool
    - Explanation of what container orchestration is and benefits:
        - Easily scale up/down containers
        - Replicate containers (redundancy)
        - Deploy containers across multiple machines (nodes)
        - Load balancing between containers
        - Dynamically relocate containers across nodes, say if a node dies
        - Rolling updates
## Docker Swarm
    - Docker's in-built orchestration tool
    - Big ol' diagram
    - Consists of:
        - Clusters
            - Manager Nodes
            - Worker Nodes
        - Ingress (routing mesh)
## Tutorial
    - This can stay largely the same
## Exercise
    - No exercise 
