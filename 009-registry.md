## Registry
(this module is fine and also marked for potential deletion)

### Overview

- This module introduces the concept of server-side registries
- Registries are applications that store images and allow them to be accessed remotely
- Docker Hub is the default registry, but you can create your own
- By the end of this module, you should understand:
    - What a registry is and why we use them
    - How to set up your own registry

### Use Case

- By default, images are pulled from Docker Hub
    - This is great because it means there's a vast community of Docker developers creating images that you can build your own from
- But what if you're containerising proprietary software internally for an organisation? Or an application not ready for production? You don't want everyone to be able to download your application
- The image needs to be accessed from multiple machines from within a private network
- What if we could create our own server-side registry that could be accessed remotely?

### Registries

- A registry is an application that stores images
- It's run up as a container built from the `registry` image
- The command to run your registry container is:
    - `docker run -d -p 5000:5000 --name registry registry`
    - Registries listen on port 5000

### Image Naming for Registries

- The syntax for an image is [HOST]/[AUTHOR]/[APPLICATION]:[TAG]
- If you don't define the [HOST] it will default to Docker Hub
- [HOST] is where you specify the registry location
- docker push [HOST_MACHINE]/[AUTHOR]/[APPLICATION]:[TAG]
    - e.g. docker push registry-vm:5000/htr-volker/flask-application:latest

### Benefits

- Private registry
- Faster download times
- Can execute web hooks to trigger deployments (outside of the scope of this module)

### Tutorial

- Existing tutorial is fine

### Exercise

- Might get rid of this one tbh?