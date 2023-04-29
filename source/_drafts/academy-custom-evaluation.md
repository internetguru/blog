---
title: How to Setup Custom Evaluation for Internet Guru Academy
date: 2023-04-29 07:47:00
copyright_author: Pavel Petrzela
cover: /images/77879d7d-7d6d-4fad-ad4a-204511798574.jpeg
categories: academy
keywords:
  - academy
  - evaluate
  - tutorial
tags:
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

This project should contain all the necessary materials, including basic code, resources, and instructions, to allow students to successfully complete their assignment.

See [How to Setup GitLab Project for Internet Guru Academy](#TODO).

## Section 2: Docker Image

To set up a custom evaluation system for the Internet Guru Academy, you will need a Docker image that will act as the base environment for your students' projects. It's important to note that your chosen image should be compatible with arm64 architecture. There are two main approaches to obtaining a suitable Docker image.

### Use an existing image

You can choose to use a pre-built Docker image available on the [Docker Hub](https://hub.docker.com/), which may already contain the required tools and packages for your course. This approach saves time and allows you to utilize a well-maintained and trusted image.

Be sure to select an image that closely aligns with your course's needs, technological stack, and is compatible with arm64 architecture.

If your course has specific requirements or you prefer to have more control over the environment, you can create your own custom Docker image. There are two ways to accomplish this.

### Create your own image Automatically on GitLab

Our GitLab offers an integrated Container Registry that allows you to create, store, and manage Docker images directly within your project. By using a GitLab CI/CD pipeline, you can automate the process of building and deploying your custom image. We recommend using the following simple approach to create your Docker image on GitLab.

 - Create a separate project specifically for the Docker image.
 - Add a Dockerfile to the project (refer to [this tutorial](https://docs.docker.com/engine/reference/builder/) on how to create a Dockerfile).
 - Create a `gitlab-ci.yml` file in the project and including `https://raw.githubusercontent.com/internetguru/academy/dev/build-docker.yml`. This file will automatically build the Docker image for you.

### Create your own image Using Docker Hub

Alternatively, you can [build your own Docker image using Docker Hub](#TODO). This process involves writing a Dockerfile that specifies the base image, tools, packages, and configurations required for your course, while making sure it's compatible with arm64. Once your Dockerfile is complete, you can build the image and push it to your Docker Hub account.

## Writing Evaluation Script

Once you have prepared the Docker image for your course, the next step is to create an evaluation script that will assess your students' work. This script can include a combination of input/output (IO) tests, project-specific tests, and utilize available variables to effectively evaluate the assignments.

TODO: pre-evaluate_${ACADEMY_LANG}
TODO: evaluate_${ACADEMY_LANG}
TODO: post-evaluate_${ACADEMY_LANG}
TODO: to show results in Dashboard generate badges.. how..
TODO: evailable variables

### IO tests

Input/output tests are essential to verify that a student's code can handle various inputs and produce the expected outputs. These tests should be designed to cover a range of scenarios, including edge cases, to ensure that the code is robust and performs well in different situations.

TODO: document run_io_tests
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


### Project-specific tests

In addition to generic IO tests, you may need to create project-specific tests to assess the unique requirements of individual assignments. These tests can include checking the correctness of algorithms, validating the use of specific libraries or APIs, or evaluating the performance of the code under certain conditions. Design these tests to target the key learning objectives of each project, ensuring that students have successfully grasped the intended concepts.


