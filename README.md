
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
```

# Docker Life Cycle

![Alt Text](https://github.com/GadagojuShiva/docker-examples/blob/main/Copy%20of%20Infra.jpg)

