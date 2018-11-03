Docker Commands
================

This Repository contain the cheatsheet for all the docker commands

## 1. Search an Image at Docker Hub
  To search an existing image at registry.hub.docker.com/
  ```
  $ docker search <image_name>
  $ docker search ubuntu
  ```

## 2. Launch a Container From Image Name(#launch-container-image)

  When You launch a container It eill give You a hexadecimal string, The 12 digits of that hexadecimal string is

  + To launch a Container from the Latest Version of Image
  ```
  $ docker run <option_name> <image_name>
  ```
  
**For eg: By default the docker run the command in the foreground You can use -d option to run it in background**
  ```
    $ docker run -d <image_name>
    $ docker run -d ubuntu
  ```
    
+ To launch a specific Version of the image:
  ```
    $ docker run -d <option_name> <image_name>:<vesion_number>
  ```
  
## 3. List all the container or Running Image

This command will list following information **Container ID, Image, command, Created, Ports,  Names(Friendly_name)**

  ```
    $ docker ps
  ```

## 4. List Complete information of the Container
 
   ```
      $ docker inspect <friendly_name | container_id >
   ```
   
  
## 5. List Logs the background container printed on std out or std err

To view what was the output that a container that docker run as background, This is same as running the docker container in Foreground

   ```
      $ docker logs <friendly_name | container_id >
   ```
   ---
   
  **Note:** Docker Container are Sanboxed, It means the host directly processes can't directly access the services running in docker. If a service running in Docker container need to be accessed by a process not running in a container, then the port needs to be exposed via the Host. This can be done either in the Dockerfile or the way as shown in [2](#launch-container-image)
)

