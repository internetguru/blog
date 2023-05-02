---
title: How to Setup Custom Evaluation for Internet Guru Academy
date: 2023-04-29 07:47:00
copyright_author: Pavel Petrzela
copyright_author_href: https://www.linkedin.com/in/pavelpetrzela/
cover: /images/77879d7d-7d6d-4fad-ad4a-204511798574.jpeg
categories: academy
tags:
  - academy
  - evaluate
  - tutorial
keywords:
  - Internet Guru Academy
  - docker
  - bash
  - cli
  - github
---

# How to Setup Custom Evaluation for Internet Guru Academy

TODO: desc / outline

## Section 1: Prerequisites

Before diving into the process of setting up custom evaluation for the Internet Guru Academy, it is essential to ensure that you have a GitLab project ready for distribution to your students.

{% note info %}
This project should contain all the necessary materials, including basic code, resources, and instructions, to allow students to successfully complete their assignment. See [how to setup Internet Guru Academy GitLab project](#TODO).
{% endnote %}

## Section 2: Docker Image

To set up a custom evaluation system for the Internet Guru Academy, you will need a Docker image that will act as the base environment for your students' projects.

{% note warning %}
It's important to note that your chosen image should be compatible with `arm64` architecture.
{% endnote %}

There are three main approaches to obtaining a suitable Docker image. Whathever approach you choose you will end up with Docker image name, e.g. `internetguru/academy-java:latest`.

TODO usage desc

```yml
variables:
  - ACADEMY_DOCKER_IMAGE: "internetguru/academy-java:latest"
```

### Using an existing image

You can choose to use a pre-built Docker image available on the [Docker Hub](https://hub.docker.com/), which may already contain the required tools and packages for your course. This approach saves time and allows you to utilize a well-maintained and trusted image.

Be sure to select an image that closely aligns with your course's needs, technological stack, and is compatible with arm64 architecture.

![test](/images/academy-custom-evaluation/docker-hub-search.png)

If your course has specific requirements or you prefer to have more control over the environment, you can create your own custom Docker image.

### Create your own image Automatically on GitLab

Our GitLab offers an integrated Container Registry that allows you to create, store, and manage Docker images directly within your project. By using a GitLab CI/CD pipeline, you can automate the process of building and deploying your custom image.

We recommend using the following simple approach to create your Docker image on GitLab.

 1. Create a separate project specifically for the Docker image.
 1. Add a Dockerfile to the project. See [how to prepare a Dockerfile](/docker-hub-multi-architecture-docker-image#Step-1-Prepare-Your-Dockerfile).
 1. Add a `gitlab-ci.yml` file to the project. Include our `build-docker.yml` that will automatically build the Docker image for you.

     ```yaml
     include:
       - 'https://raw.githubusercontent.com/internetguru/academy/dev/build-docker.yml'
     ```
 1. TODO: After that you can use docker image as `registry.[gitlab-url]/[group]/[repo]:latest`.

### Create your own image Using Docker Hub

Alternatively, you can {% post_link docker-hub-multi-architecture-docker-image 'build your own Docker image using Docker Hub' %}. This process also involves writing a Dockerfile.

{% note info %}
This way is recomended for TODO...
{% endnote %}

## Section 3: Writing Evaluation Script

Once you have prepared the Docker image for your course, the next step is to create an evaluation script that will assess students' work.

TODO desc: syntax bash, automatically runned in CI, generating badges

TODO structure

 - predefined scripts in academy repo or specific in `.academy/[script]`
 - `pre-evaluate_${ACADEMY_LANG}`
 - `evaluate_${ACADEMY_LANG}`
 - `post-evaluate_${ACADEMY_LANG}`

 - available variables

### Badges

TODO

 - for connection with Dashboard
 - for `README.md`
 ^ describe how to use it (meta job)
 - `badge_generate` function with params

### IO tests

TODO desc

TODO: run_io_tests function
 - You can use `run_io_tests` function to perform simple IO tests.
 - Example: `run_io_tests "java ${WORKING_DIR}/@RELATIVE_PATH@"`
 - IO test variables `FOLDER_NAME`, `RELATIVE_PATH`, all `ACADEMY_*`, all [predefined GitLab `CI_*` variables](https://docs.gitlab.com/ee/ci/variables/predefined_variables.html)
 - stdin, stdout, optarg (not implemented), sc, errout

TODO: Directory structure for `/src/SumClass.java` class IO tests:

```
/
└── iotest/src/SumClass.java
    ├── foo.stdin
    ├── foo.stdout
    ├── foo.errout
    ├── bar.stdout
    ├── hello.optarg
    ├── hello.sc
    ├── world.errout
    └── …
```

## Section 4: Get it All Together

TODO summary with complex example

TODO example

 - Project `/java/intro` structure:

```plaintext
 /
 ├── iotest/Greeting.java
 │  ├── 1.stdin
 │  ├── 1.stdout
 │  ├── 2.stdin
 │  ├── 2.stdout
 │  ├── 3.stdin
 │  └── 3.stdout
 ├── .gitignore
 ├── .gitlab-ci.yml
 ├── Greeting.java
 └── README.md
```

- Content of the `.gitlab-ci.yml`:

```yaml
include:
  - $ACADEMY_INCLUDE

variables:
  ACADEMY_DOCKER_IMAGE: "internetguru/academy-java:latest"
  ACADEMY_EVALUATE: "always"
  ACADEMY_LANG: "java"
  ACADEMY_EDITABLE: "*.java"
```

