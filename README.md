
# Architecture's of Containers and VM's
![Alt Text](https://github.com/GadagojuShiva/docker-examples/blob/main/Infra.jpg)

# What is Container

- Container are the packages or bundles that are combinations of application, application dependencies and system dependencies.

- Containers are lightweight because they skip the full operating system and, instead, use a minimal base image with essential system components. They share the host operating system's kernel and libraries to operate efficiently.
# Folders in the container

```bash 
    /bin    --> Holds binary executable files such as commands like 'ls' and 'cp.'
    /sbin   --> Contains system binary executable files like 'init'
    /etc    --> Stores configuration files.
    /var    --> Holds variable files like log files.
    /root   --> This is the home directory for the root user.
    /lib    --> Contains libraries used by executable files.
    /usr    --> contains user files and utilities
```

# Files and Folders Utilized by a Container from the Host Operating System

```bash 
    Hostfile            --> Files on the host system accessed or mounted by the container.
    control Group       --> A Linux kernel feature managing resource usage of processes; used by containers for resource allocation.
    Networking Stack    --> Shared network capabilities between the host and containers, enabling communication.
    System Calls        --> Mechanism for containers to interact with the host's kernel for various operations.
    Namespaces          --> Provide isolation in containers; e.g., PID namespace isolates process IDs for distinct views.
```

# Docker 

- Docker is a containerization platform that enables the creation of images, running containers, and pushing them to public registries.


# Architecture's of Docker
![Alt Text](https://github.com/GadagojuShiva/docker-examples/blob/main/docker.jpg)

# Terminology of Docker
```bash
Docker client       --> The tool you use to control Docker through commands.
Docker Demon        --> The background service managing Docker containers.
Docker file         --> A set of instructions in a file to build a Docker image.
Docker Image        --> A lightweight, standalone package containing everything to run software.
Docker Container    --> A running instance of a Docker image, like a virtual computer for an application.
Registry            --> A registry is a centralized repository for storing and sharing Docker container images.
```

# Docker Life Cycle

![Alt Text](https://github.com/GadagojuShiva/docker-examples/blob/main/Copy%20of%20Infra.jpg)

# Docker Multi-Stage Builds

- A multi-stage build is a process that allows you to break the steps in building a Docker image into multiple stages.
- Building application is in different stage and running application is in different stage
    ```
    #############################################
    # Stage - 1
    #############################################
    FROM node:12.13.0-alpine as build
    WORKDIR /app
    COPY package*.json ./
    RUN npm install
    COPY . .
    RUN npm run build
    #############################################
    # Stage - 2
    #############################################
    FROM nginx
    EXPOSE 3000
    COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
    COPY --from=build /app/build /usr/share/nginx/html
    CMD ["nginx", "-g", "daemon off;"]
    ```
# Distroless images
- Images contain only your application and its runtime dependencies. They do not contain package managers, shells or any other programs you would expect to find in a standard Linux distribution.
  
# Bind Mounts and Volumes  

- Let's say you have a Docker container running a web server, and it generates log files to track activity. If, for some reason, the container stops unexpectedly, the log files stored within the container could be lost. To prevent this, Docker offers solutions like bind mounts and volumes.

- With a bind mount, you can connect a folder on your computer (host) directly to the container. This way, even if the container stops, the log files are safely stored on your computer. Volumes work similarly but offer more flexibility, allowing you to manage and back up data independently of the container's lifecycle. These features ensure that your important log files persist, making it easier to analyze and troubleshoot issues, even if the container goes down unexpectedly.
-  **Bind mounts**
      - Bind mounts in Docker create a direct link between a folder on the host OS and a corresponding location in a container. This connection ensures real-time synchronization, allowing changes in either the container or host to immediately reflect in the other.

      - The main goal of bind mounts is to guarantee data persistence and availability beyond the container's lifespan. When a folder is bound, modifications made inside the container are mirrored on the host, and vice versa. This two-way syncing facilitates smooth data sharing between the container and the host.

      - A key application of bind mounts is safeguarding essential files, like log files, generated or updated during a container's operation. By binding the log directory to a host folder, you secure log data even if the container stops or is deleted. This proves valuable for debugging, auditing, and maintaining a historical log record.
  
-  **Volumes** 
      - Volumes in Docker serve as logical partitions for data storage and are managed through the command-line interface (CLI). They provide a flexible and persistent way to handle data in containers
  
## Volume Commands
```bash
# To create a volume:
docker volume create my_volume

# To list volumes:
docker volume ls

# Mounting volumes to a container:
docker run -d --mount source=my_volume, target=/path/in/container my_image

# To describe a volume:
docker volume inspect my_volume

# Deleting a volume:
docker volume rm my_volume

```
# Networking in the Docker

- Networking in the Docker allows containers to communicate with each other and with the host system.
- We have Three types of Networking in the Docker:
  - **Bridge network**  - Is the default network in the docker which uses docker0  which create vauth to communicate
  - **Host network**    - All containers uses the same host network
  - **Overlay Network** -  Every host ip is same 
# Networking Commands
```bash
# To list networks:
docker network ls

# To create a network:
docker network create my_network

# Assigning a network to a container:
docker run -d --name my_container --network=my_network my_image

```

