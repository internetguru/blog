---
title: Version handling with Flow
date: 2023-04-05 09:15:28
coauthor: George Pavelka
tags:
    - flow
    - version
---

In branching models, version numbers play a crucial role. Flow is a command-line developer tool to maintain software projects compliant with a branching model. Additionally, Flow offers robust version handling and ensures that version numbers are always in compliance with the model.

<!-- more -->

## Validation and compliance

Flow ensures all version files are present and in compliance with the branching model. For example, the development version must be greater than the staging version. The (unreleased) staging version must be greater than the stable version and lower than the development version.

Not only Flow can verify versions, it will report irregularities and suggest fixing them for you. It offers to fix missing version files as much as invalid version numbers. Flow does this for all key branches consecutively.

## The release process

During the general release process from dev to staging to production, Flow manages the version being released. However, after releasing the development branch to staging, Flow automatically increments the minor version on dev for future releases.

When the development branch is released multiple times (without the staging branch being released), versions on the development and staging branches remain the same. However, the release candidate number increases. Read more about {% post_link flow-changelog 'handling changelog with Flow' %}.

## Hotfixing

Flow automatically increments the patch version number when a hotfix is released. Multiple parallel hotfixes are versioned consecutively in the order of their actual release.

When released, hotfixes are merged into the stable branch. Additionally, each hotfix is also released into a corresponding separate production branch based on its major version. Read more about {% post_link flow-merging 'merging branches with Flow' %}.

## Try Flow today

Flow's version handling capabilities make it easy to keep track of your project's progress and ensure that your version numbers are always in compliance.

If interested, feel free to [download Flow from GitHub](https://github.com/internetguru/flow). Check out the tutorial for an easy way to get started. Your feedback is welcome as well as suggestions and contribution.
