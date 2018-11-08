Docker Commands
================

This Repository contain the cheatsheet for all the docker commands

## 1. Search an Image at Docker Hub
  To search an existing image at registry.hub.docker.com/
  ```
  $ docker search <image_name>
  $ docker search ubuntu
  ```
## 2. List all the images in Host Sysyem
This command will list following details of the images in the system 
  
  ```
      $ docker images
  ```
    
## 3. Launch a Container From Image Name

  When You launch a container It eill give You a hexadecimal string, The 12 digits of that hexadecimal string is Container Unique ID

  + To launch a Container from the Latest Version of Image
  ```
  $ docker run <option_name> <image_name>
  ```
  **Note** Various docker run flavor with various option

  ```
    $ # To launch an image in background -d option
    $
    $ docker run -d <image_name>
    $ docker run -d ubuntu
    
    $ # To Map Host Port To the Container Port - The port on the host is mapped to 0.0.0.0
    $
    $ docker run -p <host-port>:<container-port> <image_name>
    $
    $ # or To bind a particular Ip
    $
    $ docker run -p <ip_addr>:<host-port>:<container-port> <image_name>   
    $
    $ # or To bind random Port of Host Machine
    $
    $ docker run -p <container-port> <image_name>
 
    $ # To list port alloted
    $
    $ docker port -p <frinedly_name | container_id> <container_port>
    
    
    $ # To run Container with different name 
    $ docker run --name <different_name> <image_name>
    
    $ # container are designed to be build stateless, That is if You recreate a container the data will be removed 
    $ # You can bind the Host directory with Your Container directory (or volumes) This lets you persist your data
    $
    $ docker run -v <host-dir-path>:<container-dir-path>
    $ docker run -v $PWD:<container-dir-path>

  ```
    
+ To launch a specific Version of the image:
  
  ```
    $ docker run <option_name> <image_name>:<vesion_number>
  ```
  
## 4. List all the container or Running Image

This command will list following information **Container ID, Image, command, Created, Ports,  Names(Friendly_name)**

  ```
    $ docker ps
  ```

## 5. List Complete information of the Container
 
   ```
      $ docker inspect <friendly_name | container_id >
   ```
   
  
## 6. List Logs container printed on std out or std err

To view what was the output that a container that docker run as background, This is same as running the docker container in Foreground

   ```
      $ docker logs <friendly_name | container_id >
   ```
  ---
   
  **Note:** Docker Container are Sanboxed, It means the host directly processes can't directly access the services running in docker. If a service running in Docker container need to be accessed by a process not running in a container, then the port needs to be exposed via the Host. This can be done either in the Dockerfile or the way as shown in [2](#2-launch-a-container-from-image-name)
)

---
 ## 7. Docker Build Image
 
 Before reading this command read, [How to Write Dockerfile](https://github.com/this-is-r-gaurav/dockerCommands/tree/master/How%20to%20Write%20a%20Dockerfile)? You can create a Docker Image From a Dockerfile using this command 
 ```
      $ docker build -t <image_name>:<tag or version_number> <build_destination_folder>
```

 ## 8. Remove an image
 **Note:** You can remove an image only and only if the image has no referenced container, until you pass the forcefully command
 
  ```
    $ docker rmi <image_id | friendly_name>
  ```
 ## 9. Delete all Container
 **Note:** You can remove an image only and only if the image has no referenced container
 
  ```
    $ docker kill <image_id | friendly_name>
  ```
## 10. Remove Errored image and container

 
  ```
    $ docker system prune
  ```

