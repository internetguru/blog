---
title: Creating Multi-Architecture Docker Images
date: 2023-04-29 07:47:00
copyright_author: Pavel Petrzela
copyright_author_href: https://www.linkedin.com/in/pavelpetrzela/
cover: /images/91e6ca16-8bd4-4797-8963-5d7dc57e6dd1.jpeg
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

Creating a [Docker](https://www.docker.com/) image that supports both arm64 and amd64 architectures can be achieved through the use of Docker Buildx, a CLI plugin that extends the Docker command with the full support of the features provided by [Moby BuildKit](https://github.com/moby/buildkit). Follow the steps below to create a multi-architecture Docker image.

## Step 1: Install Docker Desktop

First, ensure that you have Docker Desktop installed on your machine. If you haven't, you can download it from the [official Docker website](https://www.docker.com/products/docker-desktop/) and follow the installation instructions for your operating system.

{% note warning %}
Docker Buildx is included in Docker Desktop starting from version 19.03. If you have an older version, you may need to install the Buildx plugin manually. Check the Buildx documentation for [installation instructions](https://github.com/docker/buildx#installing).
{% endnote %}

## Step 2: Prepare Your Dockerfile

Create a Dockerfile in your project directory, specifying the base image, tools, packages, and configurations required for your course. Make sure that the base image you choose has support for both `arm64` and `amd64` architectures.

{% note info %}
We recommend to use Internet Guru Academy minimal base image for Dashboard purposes as you can see in the following example.
{% endnote %}

```dockerfile
FROM internetguru/academy:latest
```

Continue adding the necessary instructions to set up your environment according to your course requirements. For example for installing `python3` add:

```dockerfile
RUN apt-get update \
    && apt-get install -y python3  \
    && rm -rf /var/lib/apt/lists/*
```

{% note info %}
Read more about [Dockerfile best practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/).
{% endnote %}

## Step 3: Create a Builder Instance

Open a terminal and run the following command to create a new builder instance with multi-architecture support:

```bash
docker buildx create --name mybuilder
```

Then, switch to the new builder instance:

```bash
docker buildx use mybuilder
```

## Step 4: Build and Push the Multi-Architecture Image

Now, you can build the Docker image for multiple architectures by specifying the `--platform` option with the desired architectures:

```bash
docker buildx build --platform linux/amd64,linux/arm64 -t your-dockerhub-username/your-image-name:tag --push .
```

Replace `your-dockerhub-username`, `your-image-name`, and `tag` with your own Docker Hub username, the name of your image, and the desired tag, respectively. You can use `:latest` tag.

This command will build and push the multi-architecture Docker image to your Docker Hub account, making it available for your students to use.

{% note info %}
Once the process is complete, you can verify the supported architectures by visiting your image's page on Docker Hub or by using the `docker manifest inspect` command.
{% endnote %}

## Step 5: Retrieve the Docker Image Name for Use in gitlab-ci.yml

Once your multi-architecture Docker image has been successfully built and pushed to Docker Hub, you'll need the image name to configure your `gitlab-ci.yml` file. The image name should follow this format:

```
your-dockerhub-username/your-image-name:tag
```

Replace `your-dockerhub-username`, `your-image-name`, and `tag` with your Docker Hub username, the name of your image, and the desired tag, respectively. For example `internetguru/academy-java:latest`.

