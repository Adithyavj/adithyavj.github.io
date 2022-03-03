---
title: Deploying a static website to Docker
author: Adithya Vijay
date: 2022-02-18 15:30:00 +0550
categories: [Blogging, deployment]
tags: [web development deployment docker]     # TAG names should always be lowercase
---

### Introduction
Most of us are familiar with virtual machines, you have an entire operating system and all the necessary programs (basically a full computer), but it's virtual.
Docker is even smaller, it doesn't replicate the entire computer, just parts of it and our required OS as layers. We can install our site into a docker container. The advantage of using docker is that we can pass around this container with the OS, the website installed, and everything already configured for the website to run properly.
This enables us to scale up a website quickly. Instead of deploying it to multiple locations, we can create multiple identical copies of our docker container and load balance between the different containers. It's also easy to deploy it to cloud services.

### Getting Started
To get started,
1. [install](https://www.docker.com/get-started) docker desktop on your computer. 
2. Now go to [DockerHub](https://hub.docker.com/) and search for *httpd*
3. From the tag section filter for *alpine*. **httpd:alpine** provides a complete linux OS with a web server. We will use this container to package up our website so that we can deploy an image of our site.
4. Provided you are using VSCode as your text editor, you can install the docker extension for ease of working with dockerfiles.
5. Create a new file in your root directory called **dockerfile** (no extensions). The contents of the file will be the following:
    ```
        FROM httpd:alpine
        COPY ./ /usr/local/apache2/htdocs/
    ```
    So, what does this do? First provide the location we are building from. In our case *httpd:alpine*, then copy the html, css, and other necessary files from our filepath to the path specified for httpd which is */usr/local/apache2/htdocs/*
6. Next, we need to create a docker image for our website
    - To build our image from the dockerfile run the following command in the terminal
        ```
            docker build -t <name-of-the-docker-image> .
        ```
    - After building, to check if the image is created, run
        ```
            docker images
        ```
    - An image is like a read-only image of our application, if we need to run an image, we need a container
        ```
            docker run --name <container-name> -p 8080:80 <name-of-image-to-run-off-of>
        ```
        // 8080 - in our system container will run in this port <br/>
        // 80 - http port in the apache server
7. Now goto localhost:8081 and we will have our website up and running.

### Basic Commands

#### Image
```
- docker build -t name:tag .        // build a new image
- docker images                     // show all images
- docker image history imageid      // to see the history of image 
- docker rmi imageid                // to remove image
```
#### Container
```
- docker ps -a                      // show all containers
- docker stop conatinerid           // to stop a running container
- docker start containerid          // to start a container
- docker rm containerid             // removes the container
```