
How to write a Dockerfile?
==========================

To Build a Docker Image from Scratch to run some services, You need a **Dockerfile**. 
**Dockerfile: A Dockerfile is a text file that contains all commands written *in order* needed to build a given age**

Now Let's just proceed to write the Docker File.

Every Docker image starts from a **Base Image**. The **Base image is generally that Image which include the platform dependencies required by your application**. The Firstline of any Dockerfile is the command written below

1. FROM creates a layer from the image mentioned after 
  ```
    FROM <image_name>{:<version>} 
  ```
