# Docker 101

Tags: Ubuntu

# Introduction

Welcome to our beginner's guide to Docker! If you're new to Docker and wondering what all the buzz is about, you've come to the right place. Docker is like a magic box that makes it easy to package up your apps and run them anywhere. In this blog post, we'll walk you through the basics of Docker, from installing it on your computer to creating your first containers. By the end, you'll see how Docker can simplify your development process and make your life a whole lot easier. Let's get started!

# 0. **Prerequisites**

- 64-bit kernel and CPU support for virtualization.
- KVM virtualization support (Check out my previous [blog](https://blog.debjotyms.com/kernel-based-virtualization))
- At least 4 GB of RAM.
- At least 4 GB of RAM.

Go to this official blog for more info.

[Install Docker Desktop on Linux](https://docs.docker.com/desktop/install/linux-install/#system-requirements)

# 1. Install Dockers Ubuntu

There are actually multiple ways to install Docker in your Ubuntu machine. Here I will install using the apt repository. To do that, you have to copy paste this command directly run on your terminal.

### 1.1: Set up Docker’s repository

If you set up Docker's package repository, you will be able to receive updates to Docker Desktop through the system's package manager (APT in this case). Setting up the repository ensures that you have access to the latest versions of Docker Desktop and any updates or patches provided by Docker.

```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled.png?raw=true)

### 1.2: Install the Docker Package

Write this command to install **Docker CE** (Community Edition), **Docker CE CLI** (Command Line Interface), **Containerd** (an industry-standard container runtime), **Docker Buildx plugin** (for building multi-platform Docker images), and **Docker Compose plugin**.

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%201.png?raw=true)

### 1.3: Run `hello-world`

The "hello-world" Docker image is a very basic image used primarily for testing and demonstration purposes. When you run the "hello-world" image as a container, it simply prints a message to the console, confirming that your Docker installation is working correctly.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%202.png?raw=true)

When we learn a programming language for the first time, we print `Hello, world!` This image is also the first thing users try after installing Docker to verify that everything is set up properly. It's also commonly used in tutorials and documentation to demonstrate how to run a Docker container.

# 2. Basic Docker Commands

We have successfully installed Docker. Now I will show some very basic Docker commands and their outputs.

### 2.1: Searching for Images (`docker search`):

This command allows you to search for Docker images by keyword. It queries the Docker Hub registry by default but can also be configured to search other registries. The results display relevant images along with their descriptions, ratings, and other metadata.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%203.png?raw=true)

### 2.2: Pulling an Image (`docker pull`):

This command fetches Docker images from a registry, such as Docker Hub or a private registry. It downloads the specified image or images to your local machine, making them available for use in creating and running containers. If you don’t mention any version, it will download the latest version by default. Here I am pulling the Ubuntu image from Docker Hub.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%204.png?raw=true)

### 2.3: Show Existing Images (`docker images`):

The `docker images` command is used to list all the Docker images that are currently downloaded or available locally on your system. It provides information such as the `repository`, `tag`, `image ID`, `creation date` and `size` for each image.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%205.png?raw=true)

### 2.4: Run a Container (`docker run`):

This command creates and starts a new Docker container based on a specified image. It can also configure various aspects of the container, such as networking, storage, and runtime behavior. Running a container is akin to launching an application or process within an isolated environment.

Here I am creating and running an Ubuntu container in an **Interactive** mode using `-it` with the command.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%206.png?raw=true)

You can also run in **Detached** mode. When you run a container in detached mode (`-d`), it means that the container will run in the background, detached from your current terminal session. This allows you to continue using your terminal for other tasks while the container runs independently.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%207.png?raw=true)

### 2.5: List of all the Created Containers (`docker ps -a`)

The **`docker ps -a`** command is used to list all Docker containers, both running and stopped. It provides a comprehensive view of all containers that have been created on your system, regardless of their current status.

When you run **`docker ps -a`**, you'll typically see output similar to the following:

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%208.png?raw=true)

### 2.6: List of all Running Containers (`docker ps`)

The `docker ps` command is used to list all the currently running Docker containers. It displays information such as the container ID, the image used to create the container, the command being executed in the container, the container's status, and more. Here `ps` means **Process Status.**

When you run `docker ps`, you'll typically see output similar to the following:

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%209.png?raw=true)

### 2.7: Restart a Container (`docker stop` & `docker start`)

To restart a container, you need the `Container ID`. You can get the id using the `docker ps` command. Copy that id and use the `docker stop` command to stop the container from running. 

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2010.png?raw=true)

Use the `docker start` command using the same id to start the container again.

### 2.8: Build an Image using Dockerfile

Before creating a Dockerfile, first we have to know what a Dockerfile actually is. It is basically a text file with instructions to building a Docker image. It essentially acts like a recipe, outlining the steps needed to create a self-contained software package that can run on any system with Docker installed.

**2.8.1: Create a Dockerfile and add instruction to it:**

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2011.png?raw=true)

After writing instructions inside the Docker file, we have to build it using `sudo docker build -t debimg:1.0 .`

**2.8.2: Show Existing Images**

Now if you see the images, you will find the newly created image named `debimg` (for me) in the image list.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2012.png?raw=true)

**2.8.3: Create a Container of that Image**

Now, if you create a container using that Image Id of `debimg` image, the command will execute as we had written inside the docker file.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2013.png?raw=true)

### 2.9: **Committing Changes to an Image (`docker commit`)**:

After making changes to a container, such as installing software or modifying files, this command creates a new image containing those changes. It effectively takes a snapshot of the container's filesystem and configuration at the current state. The resulting image can then be used to create new containers with the same configuration.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2014.png?raw=true)

### 2.10: **Removing a Container (`docker rm`)**:

`docker rm` is used to remove one or more **stopped** containers from your system. When you no longer need a container, you can use this command to clean up disk space and resources. It permanently deletes the specified containers, freeing up resources for other uses.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2015.png?raw=true)

### 2.11: **Removing an Image (`docker rmi`)**:

`docker rmi` is used to remove one or more Docker images from your local machine. It deletes the specified images, along with all their associated layers and metadata, freeing up disk space. This command is useful for cleaning up unused or outdated images to conserve storage resources.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2016.png?raw=true)

# 3. Create a Docker Image using Dockerfile

Before creating a Dockerfile, first we have to know what a Dockerfile actually is. It is basically a text file with instructions to building a Docker image. It essentially acts like a recipe, outlining the steps needed to create a self-contained software package that can run on any system with Docker installed.

### **3.1: Create a Dockerfile and add instruction to it:**

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2011.png?raw=true)

After writing instructions inside the Docker file, we have to build it using `sudo docker build -t debimg:1.0 .`

### **3.2: Show Existing Images**

Now if you see the images, you will find the newly created image named `debimg` (for me) in the image list.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2012.png?raw=true)

### **3.3: Create a Container of that Image**

Now, if you create a container using that Image Id of `debimg` image, the command will execute as we had written inside the docker file.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2013.png?raw=true)

# 4. Run a container as a single task, show outputs, and show the status of all containers.

### 4.1: Execute the command `sudo docker images` to see what images are available on your local machine:

After running the command, you will get a list of all the images are on your device.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2017.png?raw=true)

### 4.2: Run an Image

Here I will run the Ubuntu image from here using the `sudo docker run -it ubuntu` to run the Ubuntu image in interactive mode.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2018.png?raw=true)

### 4.3: She the condition of the container

Run the command `sudo docker ps -a` to see the condition of the container.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2019.png?raw=true)

# 5. Run a container in iterative mode and install different packages in the container.

### 5.1: Run Ubuntu Image:

Here I will run the Ubuntu image from here using the `sudo docker run -it ubuntu` to run the Ubuntu image in interactive mode.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2020.png?raw=true)

### 5.2: Install `cmatrix`

here `cmatrix` is not installed. So now, I will install `cmatrix` here.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2021.png?raw=true)

### 5.3: Run `cmatrix`

Now run `cmatrix`:

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2022.png?raw=true)

# 6: Database Container Management: Logging, Interaction, and SQL Query Showcase

### 6.1: Run SQL Command in the Background

Execute the command `docker run -d --name mysql_container -e MYSQL_ROOT_PASSWORD=password mysql:latest` to run MySQL docker container in the background. `-d` here is used to run it in the background. I don’t have any MySQL image on my device. So, first it will pull it from `DockerHub` and then run.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2023.png?raw=true)

### 6.2: Show Logs of the Running Container

To show logs of a running container in Docker, you can use the **`docker logs`** command followed by the container ID or name. Here's the general syntax:

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2024.png?raw=true)

### 6.3: Launch MySQL Container in Interactive Mode

The command **`docker exec -it mysql_container bash`** lets you open up and interact with a Docker container called `mysql_container` as if it were a regular computer. 

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2025.png?raw=true)

### 6.4: Launch MySQL Client

After running the MySQL docker in interactive mode, run the following command to launch the SQL client and run some SQL Queries:

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2026.png?raw=true)

# 7. Push your own image to Docker Hub

Pushing your Docker image to Docker Hub is like uploading a photo to the internet. First, make sure your Docker image is ready. Then, log in to Docker Hub on your computer. Next, tag your image with your Docker Hub username and the name you want. Now, push your image to Docker Hub with a simple command. Finally, check Docker Hub to see your image live for everyone to use. That's it! Here is the step-by-step process with explanation:

### 7.1: Create an Account on Docker Hub

I am not going to explain it here. I think you can do it by your own. It’s super easy.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2027.png?raw=true)

### 7.2: Choose Which Image You Want to

In the 3rd section of this blog, I had created an image named `debimg`. Which is basically a modified image of the `ubuntu` image. I will push that image into Docker Hub.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2028.png?raw=true)

### 7.3: Assign a New Tag

The **`docker tag`** command is used to assign a new name and/or a new tag to an existing Docker image. This command is particularly useful when you want to prepare an image for publishing to a Docker registry like Docker Hub.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2029.png?raw=true)

### 7.4:  Sign in to your Docker Account through CLI

Next, you'll need to sign in to your Docker account using the command line. To do this, you might require something called a Personal Access Token (PAT). You can generate a PAT from your Docker account's security settings. Instead of using a regular password, you'll use this PAT to authenticate. It's like having a special key to unlock your account when using the command line.

**7.4.1: Generate a PAT**

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2029.png?raw=true)

**7.4.2: Sign in to Docker from CLI:**

Use the previously generated PAT as the password to sign in.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2030.png?raw=true)

### **7.5: Push the Image**

`docker tag my_image myusername/my_repo:latest` use this format while pushing.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2031.png?raw=true)

### 7.6: Check on Docker Hub

After the image has been successfully pushed, check your Docker Hub repository section to verify whether or not the image is showing there.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2032.png?raw=true)

# 8. Make Your Own Private Registry

### 8.1: Install docker `compose` and `apache2-utils`

Before setting up the Docker Registry, ensure that the necessary packages are installed on your system. In this case, you need **`docker-compose`** and **`apache2-utils`**. These packages can be installed using the package manager appropriate for your system (e.g., **`apt`** for Debian-based systems like Ubuntu).

```bash
sudo apt install docker-compose apache2-utils
```

### 8.2: Run Docker Registry as a Container

You can run the Docker Registry as a container using the following command:

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2033.png?raw=true)

### 8.3: Tag and Push into Private Repository

After the Docker Registry container is up and running, you need to tag and push Docker images to it. Tagging an image associates it with a repository in the registry, while pushing uploads the image to the registry. In the provided example, the **`test_ubuntu`** image is tagged with **`localhost:5000/test_ubuntu`** and then pushed to the local Docker Registry using these commands.

```bash
docker tag test_ubuntu localhost:5000/test_ubuntu
docker push localhost:5000/test_ubuntu
```

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2034.png?raw=true)

# 9. Create a Dockized Website

Here are the steps to create a small website with minimal functionality (a simple HTML button that opens a static image) inside a Docker container and then run it on your host machine:

### **9.1: Create a Directory for Your Project**

First, let's create a directory to organize our project files. We'll name it `docker_website` for clarity. This directory will contain all the files related to our Dockized website.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2035.png?raw=true)

### 9.2: Create Necessary Files

In this step, we'll create the HTML file for our website and an image file that the HTML file will reference.

HTML File (**`index.html`**)

We'll create a basic HTML file with a button that, when clicked, opens a static image.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2036.png?raw=true)

Image File (**`image.jpg`**)

We'll also need an image file for the button to open. You can use any image you like, just name it **`image.jpg`** and place it in the same directory as the HTML file.

### 9.3: Create a Dockerfile

A Dockerfile is a text file that contains instructions for building a Docker image. In our case, we'll use the official Nginx image as our base image and copy our HTML and image files into it.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2037.png?raw=true)

This Dockerfile specifies that we'll use the **`nginx:alpine`** image as our base, and then copy all the files from the current directory (**`.`**) into the **`/usr/share/nginx/html`** directory inside the container.

### 9.4: Build the Docker Image

With our Dockerfile in place, we can now build our Docker image using the **`docker build`** command. We'll tag our image with the name **`docker_website`**.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2038.png?raw=true)

### 9.5: Run the Docker Container

Now that we have our Docker image built, we can run it as a Docker container. We'll use the **`docker run`** command to do this. We'll also map port **`8080`** on our host machine to port **`80`** inside the container, where Nginx is listening by default.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2039.png?raw=true)

The **`-d`** flag tells Docker to run the container in detached mode (in the background), and the **`-p`** flag maps port **`8080`** on the host to port **`80`** on the container.

### 9.6: Access the Website

Finally, we can access our website by opening a web browser and navigating to **`http://localhost:8080`**. You should see the welcome message and a button. Clicking the button should open the image in a new tab.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2040.png?raw=true)

That's it! You've successfully created a simple website with minimal functionality inside a Docker container and accessed it from your host machine. Feel free to customize and extend this example to suit your needs. Happy coding!

# 10. Migrate Container

### 10.1: Push Container Image to Docker Hub

The first step is to upload your container image to Docker Hub. Ensure you have an account on Docker Hub and login using the `docker login` command in your terminal or command prompt. Next, tag your existing container image with your Docker Hub username and repository name and push:

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2041.png?raw=true)

### 10.2: Pull the Container on Another Machine

On the machine where you want to migrate the container, ensure you have Docker installed. Log in to Docker Hub using **`docker login`**. Once logged in, pull the container image from Docker Hub using:

```php
docker pull <docker_hub_username>/<repository_name>:<tag>
```

This command fetches the container image from Docker Hub to your local machine, making it ready for deployment.

### 10.3: Run Container on the New Machine

After containerizing the Image, we'll use the **`docker run`** command to do this. We'll also map port **`8080`** on our host machine to port **`80`** inside the container, where Nginx is listening by default.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2039.png?raw=true)

The **`-d`** flag tells Docker to run the container in detached mode (in the background), and the **`-p`** flag maps port **`8080`** on the host to port **`80`** on the container.

### 10.4: Access the Website

Finally, we can access our website by opening a web browser and navigating to **`http://localhost:8080`**. You should see the welcome message and a button. Clicking the button should open the image in a new tab.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Docker%20101/Untitled%2040.png?raw=true)