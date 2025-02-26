# 🐳 [Introduction to Docker](https://app.datacamp.com/learn/courses/introduction-to-docker)

Docker is a tool used to develop, run, and ship containers. It’s an essential part of every data professional’s toolbelt, helping to create robust, secure, and scalable applications or workflows.
In this course, you’ll become a Docker pro, gaining hands-on experience using Docker CLI.

Learn the Docker basics and understand how to create and manage containers using Dockerfiles and instructions. You’ll learn the Docker terminology and get hands-on experience with Docker commands using the Docker Command Line Interface.

As you progress, you’ll learn how to create and manage Docker containers using Dockerfiles and Dockerfile instructions. To wrap up, you’ll learn Docker image security best practices to make your images safe and secure.

----------------------

✅ [Using Docker Containers](https://github.com/janaom/datacamp-professional-data-engineer-in-python/blob/main/introduction-to-docker/README.md#using-docker-containers)

✅ [Writing Your Own Docker Images](https://github.com/janaom/datacamp-professional-data-engineer-in-python/blob/main/introduction-to-docker/README.md#working-with-docker-containers)

✅ Creating Secure Docker Images

---------------------------

# Using Docker Containers

You'll go from starting and stopping your first container to seeing how to clean your environment by removing all containers and images. You'll see how to debug issues by running commands inside a container or executing bash commands in a container interactively. All of this is done using the Docker Command Line Interface.

---------------------------------------

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


## Solution

![image](https://github.com/user-attachments/assets/a32493f8-6c58-4c44-b1ba-0eaf805dbb55)

## Exercise

Cleaning up containers

You were able to find the issue with your colleague's container and help him fix it. Before you return to your project, you want to clean up the container you just started to help your colleague.

    Using the terminal, enter the command to stop the colleague_project container.

    Now that the container is stopped use the terminal to remove the container.

## Solution

![image](https://github.com/user-attachments/assets/eb25e5f3-75f8-47c8-9c39-4f751e82aef8)

# Managing local docker images

In practice, images are either custom-made or downloaded from Docker Hub. Docker Hub is a registry of community-made Docker images. In other words, it's a website from which we can download thousands of pre-made images for all kinds of use cases. For any common use-case, we will find an image on Docker Hub. 

Downloading an image from Docker Hub is called pulling an image.

![image](https://github.com/user-attachments/assets/5736ce31-e073-40cb-830b-ffec61a2b832)

![image](https://github.com/user-attachments/assets/6617be62-7edb-4397-a6f4-51bf4abe1554)

Now that we know how to pull images, we need a way to view the images we have available on our machine.

![image](https://github.com/user-attachments/assets/a8434715-4595-4f75-9b2f-d7ed6a9098df)

Docker only has a limited amount of space it can use on our disk. Previously we saw how to remove containers using docker container rm. Similarly, we can use docker image rm to clear space for more containers and images. A container is a running image; a side effect of this is that you can only delete an image once there are no more containers based on it. If we try to delete an image for which we still have a container on our system, we'll get the warning you can see at the bottom of the slide. This error message also includes the container's id based on the image we're trying to remove. We can use the docker container rm command to remove the container, after which we can remove the image.

![image](https://github.com/user-attachments/assets/8cf961dd-14b8-430a-b90e-ecb63a0aeda9)

It's common to have multiple containers based on a single image, which can make it a tedious task to one by one remove all containers before you can remove an image. To more easily clear all stopped containers, we can use docker container prune.

![image](https://github.com/user-attachments/assets/67e10704-1815-4d86-bca6-7e6d1ef477c8)

Then we can use docker image prune dash a to remove all unused images. The a flag, which stands for all, makes it so that unused containers are removed and not only dangling images.

![image](https://github.com/user-attachments/assets/797fe854-70c7-4985-a68f-b7ced28c7edd)

A dangling image is an image that no longer has a name because the name has been re-used for another image. This frequently occurs when creating our own images. For example, if we create an image called testsql, but we find a mistake and change our image slightly, the previous testsql image will then become dangling as our new fixed image now has the testsql name.

![image](https://github.com/user-attachments/assets/45dfd8fb-3e24-45e4-9498-43d96b2380da)

![image](https://github.com/user-attachments/assets/dd032183-4c79-4cf4-9970-96907de65696)

## Exercise

Pulling a specific tag

You were helping a colleague by looking at an issue they were having with installing some of their tools on the ubuntu image. You couldn't reproduce the issues so far, and just realized you might be trying on a different version of Ubuntu.

    Using the terminal, enter the command to see all images available on your machine.

    Seems like you are not using the same version as your colleague, who is using the 22.04 tag of ubuntu. Pull the right version, 22.04, of the ubuntu image.

## Solution

![image](https://github.com/user-attachments/assets/259858bf-3038-4f4f-a939-2b60c1ad72e2)

## Exercise

Cleaning up images

The project you were working on is done. You had to use and try several docker containers and images and would like to clear up some space on your system before starting your next project. You remember using the ubuntu image last and know you won't need it for your next project.

    Using the terminal, enter the command to remove the ubuntu image.

    The ubuntu image failed to remove since it still has a container using it. To be sure you can clean up your images, remove all stopped containers.

    Now that all stopped containers are removed, also remove all unused images.


## Solution

![image](https://github.com/user-attachments/assets/4725954a-8a51-4d46-a308-92d9509e451f)


# Writing Your Own Docker Images

Once you are able to manage images and containers, it's time to know how to share images with colleagues or your entire company and to understand how to create your own. Now, you'll build your own images using Dockerfiles. Dockerfiles are text files that include everything needed for Docker to build an image. You'll learn how to create images and will get an introduction to all the essential Dockerfile instructions like FROM, RUN, COPY, and more. By the end of this chapter, you'll have insight into how Docker makes images and be able to create optimized Docker images from scratch.

----------------------

In the previous lesson, we learned about the official Docker images registry and how we can pull images from it. This is just one way images are distributed. Now, we will learn how to share images with just a few people or a broader community. Either by sending docker images like we would send any other file or using a Docker registry server.

First, we'll have a look at private Docker registry servers. The Docker organization maintains the official Docker images registry. Other Docker registries work the same way but are under the control of another person or group. This means there are no guarantees that the images will work or are safe to use. Images from any registry other than the one from the official Docker organization are easily recognizable because their name starts with the URL of the private Docker registry they come from. 

![image](https://github.com/user-attachments/assets/494f045a-5512-4074-9987-c34eefb8f28e)

Now that we know how to pull images from a custom registry, let's look at how to upload or push an image to a Docker registry. 

![image](https://github.com/user-attachments/assets/90aeecc8-5d4b-47ad-91ca-28817c74e872)

While the Docker official images can be pulled without authentication, anybody creating a private Docker registry can make it private and require authentication. The standard way to secure private Docker registries requires users to log in. We do this with the Docker login command followed by the private registry we want to authenticate for. 

![image](https://github.com/user-attachments/assets/4fe0524b-7cf4-4ac9-81ed-fae42bee6e08)

If, instead of using a Docker registry, we want to send a Docker image to just a few people, it can be easier to send the image as a file. Use the save command to save a Docker image to a file. This will create a minimized file which we can then share like any other file. We can pass the desired filename to the save command using the minus o flag. To load the file, we use the load command, passing the filename using the minus i flag.

![image](https://github.com/user-attachments/assets/f134b2a9-9779-4901-9eab-68a44d9020c9)

![image](https://github.com/user-attachments/assets/bed481f1-4c33-4a66-ab66-a89f0fb90bde)


## Exercise

Sharing your work using a Docker registry

Your company is developing a new spam filter method. You think you've found a good method and would like to share your results with your colleague in a way that allows them to verify your results. You've decided that using a Docker image with all your code and datasets is the right approach. You've already created this image on your local machine and called it spam:v1. The next step is to push this image to your company's registry docker.mycompany.com so that your colleagues can build upon your work.

    Using the terminal, enter the command to tag the spam:v1 container so it can be pushed to docker.mycompany.com.

    Using the terminal, enter the command to push the docker.mycompany.com/spam:v1 image to the docker.mycompany.com registry.


## Solution

![image](https://github.com/user-attachments/assets/3aa1cf87-415f-4cb2-9755-b9897091777d)


## Exercise

Saving an image to a file

After you pushed your image to the company's registry, you got a lot of feedback from your colleagues. You addressed the most important feedback and would like to share your new Docker image, spam:v2, with just a few colleagues before you share it with the entire company again. Save your new Docker image to a file called spam_updated.tar so you can email it to your colleagues Alice and Bob.

    Using the terminal, enter the command to save spam:v2 to a file called spam_updated.tar.

## Solution

![image](https://github.com/user-attachments/assets/769ebe28-7f56-4e5f-96c0-64ef96587dc2)


## Exercise

Receiving Docker Images

Your company is still working on that new spam filter! Your colleague Bob made possible improvements to your work and sent you a tar file. Another colleague, Alice, has pushed her version to the company's dockerhub, docker.mycompany.com. It's now up to you to run both containers and find out which runs fastest.

