---
title: Creating Multi-Architecture Docker Images
date: 2023-04-29 07:47:00
copyright_author: Pavel Petrzela
cover: /images/3360cdd0-bc7e-44c2-8ce9-fd8a8d60492b.jpeg
categories: academy
keywords:
  - academy
  - docker
  - tutorial
tags:
  - Internet Guru Academy
  - docker
  - image
  - arm64
  - buildx
  - docker hub
---

# Creating Multi-Architecture Docker Images

Creating a Docker image that supports both arm64 and amd64 architectures can be achieved through the use of Docker Buildx, a CLI plugin that extends the Docker command with the full support of the features provided by Moby BuildKit. Follow the steps below to create a multi-architecture Docker image.

## Step 1: Install Docker Desktop

First, ensure that you have Docker Desktop installed on your machine. If you haven't, you can download it from the [official Docker website](https://www.docker.com/products/docker-desktop/) and follow the installation instructions for your operating system.

## Step 2: Enable Docker Buildx

Docker Buildx is included in Docker Desktop starting from version 19.03. If you have an older version, you may need to install the Buildx plugin manually. Check the Buildx documentation for [installation instructions](https://github.com/docker/buildx#installing).

## Step 3: Prepare Your Dockerfile

Create a Dockerfile in your project directory, specifying the base image, tools, packages, and configurations required for your course. Make sure that the base image you choose has support for both `arm64` and `amd64` architectures. We recommend to use Internet Guru Academy minimal base image:

```
FROM internetguru/academy:latest
```

Continue adding the necessary instructions to set up your environment according to your course requirements.

## Step4: Create a Builder Instance

Open a terminal and run the following command to create a new builder instance with multi-architecture support:

```
docker buildx create --name mybuilder
```

Then, switch to the new builder instance:

```
docker buildx use mybuilder
```

## Step 5: Build and Push the Multi-Architecture Image

Now, you can build the Docker image for multiple architectures by specifying the `--platform` option with the desired architectures:

```
docker buildx build --platform linux/amd64,linux/arm64 -t your-dockerhub-username/your-image-name:tag --push .
```

Replace `your-dockerhub-username`, `your-image-name`, and `tag` with your own Docker Hub username, the name of your image, and the desired tag, respectively. You can use `:latest` tag.

This command will build and push the multi-architecture Docker image to your Docker Hub account, making it available for your students to use.

Keep in mind that the build process for multiple architectures might take longer than building for a single architecture. Once the process is complete, you can verify the supported architectures by visiting your image's page on Docker Hub or by using the `docker manifest inspect` command.

## Step 6: Retrieve the Docker Image Name for Use in gitlab-ci.yml

Once your multi-architecture Docker image has been successfully built and pushed to Docker Hub, you'll need the image name to configure your `gitlab-ci.yml` file. The image name should follow this format:

```
your-dockerhub-username/your-image-name:tag
```

Replace `your-dockerhub-username`, `your-image-name`, and `tag` with your Docker Hub username, the name of your image, and the desired tag, respectively. For example `internetguru/academy-java:latest`.

