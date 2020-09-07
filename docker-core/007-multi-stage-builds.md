## Multi stage builds

### Overview

- This module introduces you to the concept of multi-stage builds
- Multi-stage builds are a way of separating the build stage of an application from the execution stage
    - The application is compiled in one image
    - Build artefacts (executables) are copied to a second image
    - First image is dumped
- By the end of this module, you should know:
    - Why we use multi-stage builds
    - How to create a Dockerfile that uses a multi-stage build

### Use Case
- Problem
    - Some languages require compiling before you can execute code (e.g. Java)
    - It is beneficial to use the build tool (e.g. Maven) in a container to keep build environment consistent
    - However, once app is compiled, source code and build tool are useless to the actual execution of the app
    - This takes up space on the container, eating up resources (memory) and slowing down deployment of containers
    - What if we could build are app in one container, then copy over the build artefacts to another one?

### Multi-Stage Builds
- A way of splitting our builds into a build stage and an execution stage
- Diagram here
- We can compile our code using a temporary build tool image (Maven)
- Copy our build artefacts (e.g. .jar files) into the image with the runtime engine
- Dump the build stage container
- Benefits:
    - Application is built the same regardless of where it's built
    - Keeps container size down
    - Uses up fewer resources for our application's container
    - Speeds up deployment of our containers

### Dockerfile syntax
- Step by step on how to copy code from one container to another
- Talk about how build stages increment from 0 by default
- --from=[STAGE] flag for COPY
- Naming build stages with AS (e.g. FROM maven:latest AS build-stage)

### Tutorial
- Add build stage name to dockerfile
- Otherwise quite happy to keep the same
- Free reign to edit as you see fit