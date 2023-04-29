---
title: Handle Changelog with Flow
date: 2023-04-08 13:49:50
copyright_author: George Pavelka
cover: /images/73b7686e-6f18-47fd-a581-95da396a6980.jpeg
categories: flow
tags:
    - cli
    - git
    - automation
    - development
keywords:
    - tools
    - branching
    - validation
    - changelog
---

# Handle Changelog with Flow

A good changelog is a quality indicator of well-managed software.
Flow is a command-line interface (CLI) tool designed to help follow a branching model and advance through it. Among other things, Flow helps maintain the changelog.

Following the [Keep a changelog](https://keepachangelog.com/en/) convention, Flow adds or modifies lines in changelog according to each action. It validates the changelog's structure and offers corrections if needed.

## Validation and conform feature

Before anything else, Flow validates the changelog on each key branch. It not only checks for its presence, but also looks for required stamps that each changelog has to contain in order to be compliant with the branching model.

Most detected irregularities can be resolved automatically. There is a default structure and a hierarchy of inheritance, with specific entries added consecutively for each branch.

## The release process

When a staging branch is created, Flow marks the unreleased section as a version release candidate, for example, `0.1.0-rc1`. Additionally, it creates a new 'Unreleased' section for the dev branch.

``` markdown Before
## [Unreleased]

### Added

- Entry 1
- Entry 2
- Entry 3

...
```

``` markdown After
## [Unreleased]

## [0.1.0-rc1] - 2023-04-08

### Added

- Entry 1
- Entry 2
- Entry 3

...
```

Any subsequent release of the development branch increments the release candidate number until the staging branch is released into production. Only after the staging branch is released, Flow creates the new version release, resetting the release candidate number to 1.

## Features and hotfixes

Upon releasing a feature, Flow prompts you for a changelog entry describing the feature. There is a list of commits from the feature branch as a memory refresher. Flow also provides available keywords, with the default being 'Added', and adds an automatic entry if this step is skipped.

``` markdown
###
# Enter 'json-format' description for CHANGELOG.md
#   New line for multiple entries.
#   Empty message to skip or end editing.
#
# Format
#   'keyword: message'
#
# Available keywords
#   Added Changed Deprecated Removed Fixed Security
#
# Branch 'json-format' commits
#   593d0f4 Add unit test 29
#   264526b Add JSON format
###

Added: |
```

The same process applies when releasing a hotfix. In such a case, the default changelog keyword is 'Fixed'. In addition to features, Flow adds a changelog stamp as the patch version is incremented. Read more about {% post_link flow-version 'version handling with Flow' %}.

## Try Flow today

Flow has been instrumental in helping our team manage projects more efficiently for several years, allowing us to deliver high-quality software to our clients. We believe that Flow can do the same for you and your team.

If you're interested, feel free to [download Flow from GitHub](https://github.com/internetguru/flow). Check out the tutorial for an easy way to get started. Your feedback is welcome as well as suggestions and contribution.
