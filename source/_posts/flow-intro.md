---
title: Maintain a branching model with Flow
date: 2023-04-05 09:14:00
coauthor: George Pavelka
tags:
    - flow
---

Software development is a continuous process. Maintaining a branching model can be demanding and time consuming. That's where Flow comes in. It's a command-line developer tool that automates tasks of maintaining and advancing a project on git branching models.

<!-- more -->

Flow helps to reduce human errors and streamlines your workflow. It allows you to focus on developing the software. Flow offers a wide range of features that have arisen from being used on projects of various sizes over years.

## Branching model automation

The Flow automation features simplify branching tasks by providing default actions and advising users on next steps. It supports parallel hotfixing and can create GitHub pull requests instead of direct releases.

 - Flow requires *no arguments* and derives a default action.
 - Flow switches between branches accordingly and advises what to do next.
 - Flow can create pull requests instead of releasing directly.
 - Flow maintains separate production branches for major versions, such as `prod-1`.
 - Flow supports parallel hotfixing, even for separate production branches.

## Branching model validation

The validation feature ensures that your project is compliant with a branching model. Flow handles semantic versioning, and keeps track of the release history.

 - Flow validates and automatically *fixes project structures* to conform to the branching model.
 - Flow pulls and pushes all key branches and checks whether local branches are not behind.
 - Flow handles [semantic versioning](https://semver.org/) across all key branches. Read more about {% post_link flow-version 'version handling with Flow' %}.
 - Flow keeps track of a release history with the [Keep a CHANGELOG](https://keepachangelog.com/en/) convention. Read more about {% post_link flow-changelog 'changelog handling with Flow' %}.

## Setup and configuration

Flow can be initiated in any folder with or without files and in any existing git repository. Flow will adapt and preserve existing branches.

 - Flow can initiate a git branching repository in any folder with or without files.
 - Flow can convert any existing git repository to a git branching model.
 - Flow automatically adapts to existing branches, such as 'release' instead of the default 'staging'.

## Try Flow today

Flow has been instrumental in helping our team manage projects more efficiently for several years, allowing us to deliver high-quality software to our clients. We believe that this tool can do the same for you and your team.

If interested, feel free to [download Flow from GitHub](https://github.com/internetguru/flow). Check out the tutorial for an easy way to get started. Your feedback is welcome as well as suggestions and contribution.