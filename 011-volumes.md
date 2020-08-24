## Volumes

### Overview

- This module introduces the concept of volumes
- Containers are *ephemeral*, meaning that they are designed to be spun up and ripped down quickly and easily
    - They are not designed to persist data/environments
    - However, there are certain instances where we want to persist our data
- Volumes are 

### Use Case

- MySQL database can be hosted using a container
- When you create entries into the database, they will be stored in the container
- However, if the container is deleted for whatever reason, all of its data is lost
- This could be catastrophic to our web applications, and also prevents us from easily migrating our containers across environments
- What if we could store this information in another location outside of the container?

### Volumes

- Volumes are Docker-managed storage locations that can be mounted onto our containers
- Diagram here
- Features/benefits of volumes:
    - Persistence of data
    - Share data between containers
    - Completed managed by Docker
    - Can store volumes on remote hosts

### Managing Volumes

- Creating a volume
- Listing volumes
- Removing volumes
- Inspecting volumes
- Volumes can be accessed on the file system at /var/lib/docker/volumes (read-only files, not recommended that you try edit these as they are designed to be managed by Docker)

### Mounting Volumes

- Volume flag
    - `docker run --volume my-volume:/usr/share/nginx/html`
- If Docker can't find the name of the volume in its volume list, it will create one for you

### Bind Mounts vs Volumes

- Volumes are the preferred method for persisting data in Docker
    - Bind mounts have limited functionality
    - There are still some good use cases for them, however
- Good use cases for volumes include:
    - Sharing data across multiple containers
    - When the host machine is not guaranteed to have a given directory or file structure
    - When you want to store container data on a remote host
    - When you need to back up, restore or migrate data from one Docker host to another
- Good use cases for bind mounts include:
    - Sharing configuration files from the host machine to a container
    - Sharing build artefacts between the development environment and the container
        - e.g. if you want to quickly run a Java application in a container, you can just mount the .jar file into an appropriate container
    - When file/directory structure of the bind mount's source is guaranteed to be consistent with what the container requires

### Volume Drivers

- Not covered in the academy, but it's worth knowing about them
- By default, volumes are associated with the **local** driver - this configuration means that the volume can be accessed from the local machine
- If you wanted the volume to be mountable from a remote host, you would have to use a different driver

### Tutorial

- NGINX volume tutorial is good

### Exercise

- Run a MySQL container and add some data to it. Persist the data with a volume. Destroy the container and run up another with the volume mounted to it. Check to if the data has been persisted.
- Persist the database in your trio task