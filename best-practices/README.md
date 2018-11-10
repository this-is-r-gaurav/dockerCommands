Some BEST Practices while writing Dockerfile
-----------------------------------------------

1. The installation of dependency required by your project must be performed before prior to copying the project directory and file to docker because while building an image, Docker uses cache while rebuilding an image. If no dependency has changed then the cache result can be used that saves lots of time while rebuilding an image. Two example of Dockerfile are shown below

### BAD PRACTICE

```
FROM python:3
RUN mkdir project_dir
WORKDIR project_dir
COPY . .
RUN pip3 install -r requirements.txt 
EXPOSE 8000
CMD ["python3", "manage.py", "runserver"]
```

### GOOD PRACTICE

```
FROM python:3
RUN mkdir project_dir
WORKDIR project_dir
COPY requirements.txt /project_dir/requirements.txt
RUN pip3 install -r requirements.txt 
COPY . .
EXPOSE 8000
CMD ["python3", "manage.py", "runserver"]
```

