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

# How to evaluate with Internet Guru Academy

This project should contain all the necessary materials, including basic code, resources, and instructions, to allow students to successfully complete their assignment.

## Prerequisites

- [Academy assignment](academy-assignments)
- [Academy compliant docker image](academy-docker-images)

## Writing Evaluation Script

Once you have prepared the Docker image for your course, the next step is to create an evaluation script that will assess students' work.

TODO desc: syntax bash, automatically runned in CI job, generating badges for Dashboard, mark output of specific file for dashboard

TODO structure

 - predefined scripts in academy repo or specific in `.academy/[script]`
 - `pre-evaluate_${ACADEMY_LANG}`
   - define default badges (example)
   - define folders, variables, ...
 - `evaluate_${ACADEMY_LANG}`
   - using CHANGED_FILES you can loop over files, e.g.
     ```sh
     for file in "${CHANGED_FILES[@]}"; do
       echo "Evaluating '${file}'"
       check_x "${file}"
       # process ${file} evaluation
     done
     ```
   - process evaluation, use run_io_tests function
   - generate badges
   - marks for Dashboard
   %% file start ${fileName} %%
   %% file end ${fileName} %%
 - `post-evaluate_${ACADEMY_LANG}`

 - available variables

### Badges

TODO desc: Using shields.io to generate svg badges. Extending svg to support link and title.

 - for connection with Dashboard
 - for `README.md`
 ^ describe how to use it (from meta job output)
 - `badge_generate` function with params
   - `label` (required)
   - `value` (required)
   - `color` see [Shields.io Colors section](https://shields.io#colors)
   - `file name`
   - `link`
   - `title`

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

## Get it All Together

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

