# Prerequisites
This tutorial assumes that you have:
- Installed Docker on your personal system
- Familiarized yourself with the Jetson Nano
- Have a general understanding of ROS2.

# Goals

### What is Docker?
### What is a Docker image?  
### What is a Dockerfile?  
### What is a Docker container?  
### Docker architecture
### How can we use Docker on a robot?

# Guide

## What is Docker?
"Docker lets you run code in a container, a virtualized world where all of the code dependencies are in place. Within a container the code is isolated from the rest of the host machine." - __Stereolabs__, _Getting Started with Docker and ZED SDK_

Essentially, installing things on machines is a pain, and managing dependencies between different packages is even more of a pain. Docker helps us avoid that by running applications in separate containers.



## What is a Docker image?
In order to run a container, one must first have a rough template of what should be in the container. For example, if you want the container to run a Ubuntu system with Python 3.8 installed, you would first obtain an image that acts as a template for the container. The image can come from _registries_, where anyone can _pull_ Docker images. After obtaining a Docker image, one could run it right away as a container, or one could customize it for their own purposes adding more dependencies to the image. 

## What is a Dockerfile?
Think of Dockerfile as a piece of code. A Dockerfile can be built into an Docker image just as code can be compiled into an executable. Dockerfiles can be used to create customized images based on other people's Dockerfiles. For example, you can have ```FROM ubuntu:18.04``` in the Dockerfile, specifying that the built image will be based an existing Ubuntu 18.04 image. After specifying the base image, you can add more installations by specifying it in the Dokerfile. Once the Dockerfile is written, it needs to be built into an image.

## What is a Docker container?
A Docker container is a runnable instance of an image. This is similar to how one can have multiple instances of a Class. In each container, the environment is relatively isolated from other containers and the host machine, meaning that its installed software and file system is mostly independent from each other. For instance, you can have three containers running on an Ubuntu 20.04 image, and three other containers running on an Ubuntu 18.04 image. And it would work just fine. 

## Docker architecture
Docker uses a client-server architecture:  

![Docker client-server](https://user-images.githubusercontent.com/59701038/134352545-4d983d71-715d-40bd-aef3-d6ce2315b41e.png)

Typically, the client and the server (known as the daemon) runs on your local machine. The client communicates with the daemon via Docker API requests, and the daemon handles the requests by managing Docker objects such as images and containers. A Docker registries hosts people's Docker images and Dockerfiles online, so anyone can _pull_ them for their own purposes.

## How can we use Docker on a robot?

At a high level, One could run a single, or multiple docker containers containing ROS packages.

## Docker image cross-compilation

Typically, your personal machine runs on the x86_64 architecture. However, the Jetson Nano runs on the more power-efficient aarch64 (ARM) architecture. In order to build a Dockerfile, the system must be running the same architecture as the target machine. It is possible to build Dockerfiles on the Jetson directly, however this is _very_ slow. We can do better by setting up ARM emulation on a x86 system and build the Dockerfile on the more powerful machine. 

![Docker cross-compile workflow](https://user-images.githubusercontent.com/59701038/134417794-b417a743-4ffe-4003-9daa-5e25067e7652.jpg)

This this workflow, developers will first code on their local machines. Once the developer wants to deploy the application, they will build the Dockerfile into a new Docker image that contains the new code using the ARM emulator. Once built, the new image can be _pushed_ to a registry. On the Jetson side, the user can _pull_ the updated Docker image and run it as a containerized app. 

# Exercise 

# Resources
[Docker Overview](https://docs.docker.com/get-started/overview/)  
[PackBionics DockerHub](https://hub.docker.com/orgs/packbionics/repositories)  
[Good Example of Using Docker for ROS](https://github.com/rnanosaur/nanosaur)  
[Docker cross-compilation example, from Stereolabs](https://www.stereolabs.com/docs/docker/building-arm-container-on-x86/)
