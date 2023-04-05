---
title: 'Introducing Flow: A CLI tool for git flow'
date: 2023-04-05 09:14:00
tags:
    - flow
---

# Introducing Flow: A CLI tool for git flow

As a developer, you understand the importance of maintaining a branching model. That's where Flow comes in. It's a CLI developer tool that simplifies the process of maintaining a project on a branching model.

<!-- more -->

Flow helps to reduce human errors and streamline your workflow, allowing you to focus on what really matters – developing high-quality software. Flow offers a wide range of features arising from using it on our small-to-bigger projects over years.

## Git Flow Automation

The Flow automation features simplify branching tasks by providing default actions and advising users on next steps. It also supports parallel hotfixing and creates GitHub pull requests instead of direct releases.

 - It has a simple usage that *requires no arguments* picking a default action for you.
 - It takes you across branches with the flow and advises what to do next.
 - It creates GitHub pull requests instead of releasing directly when asked.
 - It maintains separate production branches for major versions, such as `prod-1`.
 - It supports parallel hotfixing, even for separate production branches.

## Branching Model Validation

The validation features ensure project conformity to the branching model, manage semantic versioning, and track release history.

 - It validates and automatically *fixes projects* to conform to the branching model.
 - It pulls and pushes all key model branches and checks whether local branches are not behind.
 - It handles [semantic versioning](https://semver.org) across all key branches.
 - It keeps track of a release history with the [Keep a CHANGELOG](https://keepachangelog.com/en) convention.

## Setup and Configuration

The Setup and Configuration features facilitate the branching model setup, repository conversion, and pre-existing branch adaptation.

 - It can initiate a git flow branching repository on any selected folder.
 - It can convert an existing git repository into a git flow branching model.
 - It automatically adapts to pre-existing branches, such as 'release' instead of the default 'staging'.

## Give Flow a chance

Flow has been instrumental in helping our team manage projects more efficiently for several years, allowing us to deliver high-quality software to our clients. We believe that this tool can do the same for you and your team.

If you're interested in trying Flow for yourself, you can download it from GitHub. We welcome any feedback, suggestions, or contributions you may have, and we look forward to hearing from you.
