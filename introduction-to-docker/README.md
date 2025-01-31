# 🐳 [Introduction to Docker](https://app.datacamp.com/learn/courses/introduction-to-docker)

Docker is a tool used to develop, run, and ship containers. It’s an essential part of every data professional’s toolbelt, helping to create robust, secure, and scalable applications or workflows.
In this course, you’ll become a Docker pro, gaining hands-on experience using Docker CLI.

Learn the Docker basics and understand how to create and manage containers using Dockerfiles and instructions. You’ll learn the Docker terminology and get hands-on experience with Docker commands using the Docker Command Line Interface.

As you progress, you’ll learn how to create and manage Docker containers using Dockerfiles and Dockerfile instructions. To wrap up, you’ll learn Docker image security best practices to make your images safe and secure.

----------------------

✅  Using Docker Containers

✅ Writing Your Own Docker Images

✅ Creating Secure Docker Images

---------------------------

# Using Docker Containers

The Docker command line interface or CLI allows us to send instructions to the Docker daemon, which manages containers and images. The basic command is docker. To start a container, we need an image, which acts as a blueprint defining what will be available in the container. For example, the ubuntu image contains the full Ubuntu OS. When we start a container from this image, we get a running instance of Ubuntu that we can interact with via a shell. 

![image](https://github.com/user-attachments/assets/0365ca6f-b893-40bf-9427-fd96d532e3e5)

If we want to start a container from an image, we can use the docker run command, followed by the image-name. To start the hello-world image, we would use docker run hello world. By default, Docker starts a container and shows you its output while it's running. When we run a hello-world container, it prints an explanation of how the container works and then stops. 

![image](https://github.com/user-attachments/assets/9637f000-f751-432a-9b70-75051aa1cdee)

When an image is created, the creator can choose what happens when a container is started from the image. For example, the creators of the hello-world image chose to print out text and then make the container stop itself. Another example is the Ubuntu image. When starting an Ubuntu container, it will start and then shut down immediately without printing any output. Its creators decided it didn't make sense to output anything specific by default. 

![image](https://github.com/user-attachments/assets/3785d9b2-a1a5-4629-bc6d-28d48c24c176)

Instead, the Ubuntu image is intended to be used with the dash it flag. Using 'docker run dash it' followed by an image-name, we can start a container and simultaneously get an interactive shell in this container. If we do this with the Ubuntu image, we get a new shell inside the new container. The shell gives us access to a clean Ubuntu environment isolated from our host machine because it runs inside the container. Once we want to exit the container, we simply use the exit command, which returns us to the host machine and then stops the container. 

![image](https://github.com/user-attachments/assets/131964eb-3dce-42c5-b780-e3974662ab12)

We saw a container that just prints text and one that makes more sense to use interactively. A third type of container processes data or can be interacted with in some way externally, for example, a container with a database like Postgres. These are run using Docker run dash d, for detached, followed by the image-name. These containers run in the background without printing their output to our shell. 

![image](https://github.com/user-attachments/assets/65810e8d-2658-4384-812b-d12e9a835e7b)

The docker ps command allows us to see any running containers. The first column contains the container-id, uniquely identifying each container. The' docker stop' command can be used to stop containers we no longer need. 

![image](https://github.com/user-attachments/assets/19c0e49f-3596-4284-a08f-2c63dbc741e5)

![image](https://github.com/user-attachments/assets/fa0fcd00-327b-4bcb-8ef3-e95ad543e54f)

