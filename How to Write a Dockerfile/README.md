
How to write a Dockerfile?
==========================

To Build a Docker Image from Scratch to run some services, You need a **Dockerfile**. 

**Dockerfile: A Dockerfile is a text file that contains all commands written *in order* needed to build a given age**

Now Let's just proceed to write the Docker File.

Every Docker image starts from a **Base Image**. The **Base image is generally that Image which include the platform dependencies required by your application**. Various instuction that are written to build an image are written below:

1. **FROM** creates a layer from the image mentioned after, It is the must and first instruction of the Dockerfile
```
FROM <image_name>{:<version>} 
```
Then other commands can be any of the following ad desired by your application.

2. **COPY** instructions copies the content of the directory you mentioned as *source_directory* into a particular location inside the container mentioned as *destination_directory*.

```
COPY <source_directory> <destination_directory>
```

3. **ADD** instructions also copies the content of the directory you mentioned as content of the directory you mentioned as *source* into a particular location inside the container mentioned as *destination_directory*.
```
ADD <source> <destination_directory>
```

**Note:** The `ADD` instruction and `COPY` instructions seems similar and work similar but the difference being is that the **source** in the `ADD` instruction can be directory as well as URL but the in the `COPY` instruction **source** can only be a directory and `ADD` instructions does different is another amazing thing if the source is some compressed file and it decompress it and store it there. For more information Visit: [What is the difference between the copy and add commands in Dockerfile?](https://stackoverflow.com/questions/24958140/what-is-the-difference-between-the-copy-and-add-commands-in-a-dockerfile)


4. **RUN** instructions is generally used to run system command such as to chage the directory or create the directory or to install something like apt-get install

```
RUN pip3 install package_name
RUN mkdir my_directory
RUN ['ls', '-l']
```
  
 5. **CMD** instruction provides the default command for a container to execute 
```
CMD ["executable", "arg1", "arg2"...]
CMD ["arg1", "arg2"...] form
CMD command arg1 arg2
```
  
  **NOTE:** RUN and CMD sometimes seems quite similar to begineer but it's quite different from each other in the way they are executed. *RUN* instructions are **executed during the building of images** and it **can range from 0 to as desired**. and the **state of the image is committed after each RUN** command and *CMD* instructions is the instruction that is **executed as default command when you launch or run the built image with the command** [`docker run <option_name> <image_name>`](https://github.com/this-is-r-gaurav/dockerCommands#3-launch-a-container-from-image-name) CMD instruction can be override while executing the [`docker run <option_name> <image_name>`](https://github.com/this-is-r-gaurav/dockerCommands#3-launch-a-container-from-image-name) command.

For more information visit [What is the difference between RUN and CMD in a Dockerfile - Stackoverflow ](https://stackoverflow.com/questions/37461868/whats-the-difference-between-run-and-cmd-in-a-docker-file-and-when-should-i-use) and also this article [Docker RUN vs CMD vs ENTRYPOINT](http://goinbigdata.com/docker-run-vs-cmd-vs-entrypoint/)


6. **WORKDIR** By Default all the instruction that are executed in a Dockerfile are executed during [`docker build`](https://github.com/this-is-r-gaurav/dockerCommands#3-launch-a-container-from-image-name) command is executed in root directory of base image but after that some time you need to be in the project root directory. 
```
WORKDIR <container_dest_dir>
```

To execute the commands associated with project and it is not favorable to use cd command within RUN instruction like this way 
```
RUN cd project_dir && pip3 install -r requirements.txt
RUN cd project_dir && python3 manage.py runserver
```
This task can be optimized the way shown below by setting up the `project_dir` as `WORKDIR` this instruction will commit the project_dir as working directory for any upcoming instruction.
```
WORKDIR project_dir
RUN pip3 install -r requirements.txt
RUN python3 manage.py runserver
```

7. **EXPOSE** EXPOSE instruction expose a port of docker image when it is run as container to the systom so that container can be used to comminucate with system, otherwise docker container is a separate standalone environment that only shares the [kernel](https://en.wikipedia.org/wiki/Kernel_(operating_system)) of the host machine 
```
EXPOSE <port>
EXPOSE <port1> <port2> <port3>
EXPOSE <port1>-<portN>
```

8. **ONBUILD OTHER_DOCKER_INSTRUCTION** ONBUILD is a sub instruction that is used with other DOCKER instruction to optimize the building process. The instruction which is prefixed with ONBUILD instruction, is executed only when the image currently building is used as BASE IMAGE for other Docker Image. 
