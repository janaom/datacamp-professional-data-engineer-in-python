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


## Exercise

An interactive container

Another bug has popped up in the data ingestion pipeline; this time, however, you got some pointers on where the issue might be. Your colleagues tell you the application cannot start inside its Ubuntu container. To debug the issue you want to start an Ubuntu container and try to run the application yourself to find out what's going wrong.

Select the right combination of commands to:

    Run an ubuntu container and get an interactive shell inside of the container.
    Close the container to go back to the host after you got an interactive shell in the container and found the issue with the pipeline.

You can use the shell to try out the possible commands.

## Solution

![image](https://github.com/user-attachments/assets/80e6251b-4b90-4072-a6ac-9494720a8f2f)

# Working with Docker containers

When there are only a few containers, it's easy to find them in the list that docker ps returns. However, if you're working with lots of containers, it can quickly become challenging to identify the right one.  To solve this, the docker run command has a name flag that allows us to name a container. The name then shows up in the last column of the docker ps output. 

![image](https://github.com/user-attachments/assets/66bbab16-5ff6-4c06-bba8-65474dd0070d)

When using docker ps with so many containers that even naming them doesn't allow us to find them. We can use docker ps with the f, for filter flag to find a specific container. This will show you only the details of containers with the name you specified in the filter. 

![image](https://github.com/user-attachments/assets/e2213411-caaa-4320-927d-3683ad92d5cc)

Now that we know how to find our running containers, it will also be useful to see their output, for example, to debug any issues. To look at the output a container has generated, we can use the docker logs command followed by the container id. Most containers quickly generate a lot of output, so you will often have to scroll through the result of docker logs to find what you're looking for. 

![image](https://github.com/user-attachments/assets/f100c453-421d-4f69-bae2-e77c3eb671ab)

If instead, you want to follow the logs your container is generating in real-time, you can use docker logs together with the f, for follow, flag. You will see any logs the container generates live. Even though docker ps also has a f flag, the docker ps flag allows us to filter. When working with docker logs instead, the f flag has another effect, allowing us to follow a container its logs. After using docker logs, you will see the output of a running container until either the end of the logs or until you press control plus c to exit the log view. 

![image](https://github.com/user-attachments/assets/ec07f94c-f1c8-474d-a22c-ab0827459b86)

Previously, we learned how to stop containers. However, a stopped container is not fully gone; the stopped container still exists and is occupying some space on our hard drive. To fully remove an already stopped container, for example, because we want to reuse its name, we use docker container rm followed by the container-id to remove the container. 

![image](https://github.com/user-attachments/assets/e08896b4-a335-4f6f-a3ff-b24cc35e97f1)

![image](https://github.com/user-attachments/assets/551498c1-6ea6-4d5d-9db0-14ae0d3336f5)

## Exercise

Helping a colleague

You're working on a project of your own and have quite a few containers running when your colleague asks you to debug an issue he's having. You've got some time to help your colleague, but you want to make sure you can find his container among all the ones you already have running.


    Using the terminal, enter the command to run the my_project image detached from your shell while giving it the colleague_project name.
    To run an image in detached mode use the -d flag, without using this flag the image will run connected to your shell making it unusable. If this happens you can refresh the page.

    The container should be running now. Make sure it is by filtering the running containers using the name colleague_project you gave the container.

    Now that you're sure the container is running look at the logs using the container's name, colleague_project.




![image](https://github.com/user-attachments/assets/a32493f8-6c58-4c44-b1ba-0eaf805dbb55)

## Exercise

Cleaning up containers

You were able to find the issue with your colleague's container and help him fix it. Before you return to your project, you want to clean up the container you just started to help your colleague.

    Using the terminal, enter the command to stop the colleague_project container.

    Now that the container is stopped use the terminal to remove the container.

