---
date: 2020-10-23T09:48
---

# Containerization

In this tutorial, we explore containerization using Docker and Kubernetes. To demonstrate, we'll create an API to return details of the TFL train lines in London. The API will be served on a Python flask server and packed into a Docker container which will be deployed using Kubernetes. 

### 1. Create a flask API

First, create a python flask app which returns details about the TFL trains. You can see an example in the `trains/app.py` file in this directory. This application serves a very basic API with details on London's TFL trains.

### 2. Package the application into a Docker container

#### 2.1 Setup the Dockerfile


Next, we want to package the application into a container using a `Dockerfile`. The finished `Dockerfile` will look as follows:

```
FROM python:3.7-alpine

COPY . /app

WORKDIR /app

RUN pip install -r requirements.txt

EXPOSE 5000
CMD ["python", "app.py"]
```

Let's break down each line in turn to describe what is happening....
In the first line we declare a __parent image__ which is the image our own image is based on. Each subsequent declaration in the `Dockerfile` modifies this image. In our example, we use a version of Alpine Linux as our base image. Alpine Linux is a lightweight Linux distribution which makes it ideal for our container. 

```
FROM python:3.7-alpine
```

Next we copy all of the files from the current host directory into the container's app directory. 

```
COPY . /app
```

We change our working directory to the app directory. And then we tell Docker to install the Python packages needed for the `app.py`

```
WORKDIR /app

RUN pip install -r requirements.txt
```

Next we tell the container to listen on a specific network port at runtime. The default is TCP but you can also specify UDP. Note that the EXPOSE instruction does not actually publish the port. This instruction is there for documentation purposes. To actually publish the port, you need to use the `-p` flag on the `docker run` command.

```
EXPOSE 5000
```

Finally, we run the app:

```
CMD ["python", "app.py"]
```

#### 2.2 Run the docker container locally

You might want to run the Dockerfile on your own machine to verify that it is working correctly. To do that, we `docker build` and then `docker run`:

You can build the Dockerfile as follows. The `-t` or `tag` allows you to tag the image with a name.

`docker build -t slemasne/trains .`

Then run the image to create a container which runs our application. The '-p' flag maps port 5000 on localhost in the host to port 5000 in the docker container. 

`docker run -p 5000:5000 slemasne/trains`

You can also run the command with a '-d' detached flag to run the container in the background:

`docker run -d -p 5000:5000 slemasne/trains`

The application can be accessed on our localhost:

`http://localhost:5000/trains`


