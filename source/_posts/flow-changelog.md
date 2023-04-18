---
title: Handle Changelog with Flow
date: 2023-04-08 13:49:50
copyright_author: George Pavelka
cover: /images/73b7686e-6f18-47fd-a581-95da396a6980.jpeg
categories: Flow
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

A good changelog is a quality indicator of well-managed software. Flow is a command-line interface (CLI) tool designed to help in following a branching model and advance in it. Among other things Flow helps maintain the changelog.

Following the [Keep a changelog](https://keepachangelog.com/en/) convention, Flow adds or modifies lines in changelog according to each action. It validates its structure and offers corrections if it is invalid.

## Validation and conform feature

Before anything else, Flow validates changelog on each key branch. It not only checks for its presence, but also looks for required stamps that each changelog has to contain in order to be compliant with the branching model.

Most detected irregularities can be resolved automatically. There is a default structure and a hierarchy of inheritance, with specific entries for each branch added consecutively.

## The release process

When the development branch is released, Flow marks the current unreleased section as Release Candidate 1. Flow increments the minor version number on the development branch after releasing and marks it as the new unreleased version.

Any subsequent release of the development branch increments the release candidate number until the staging branch is released into production. Only after the staging is released, Flow creates the new version release, resetting the Release Candidate number to 1.

## Features and hotfixes

Upon releasing a feature, Flow prompts for a changelog entry describing the feature. There is a list of commits from the feature branch as a memory refresher. Flow also offers available keywords with the default 'Added' and adds an automatic entry if skipped.

```
❯ flow
* Merge feature 'json-format' into 'dev'? [YES/No] yes

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

The same applies when releasing a hotfix. In such a case, the default changelog keyword is 'Fixed'. In addition to features, Flow adds a changelog stamp because the patch version was incremented. Read more about {% post_link flow-version 'version handling with Flow' %}.

## Try Flow today

Flow has been instrumental in helping our team manage projects more efficiently for several years, allowing us to deliver high-quality software to our clients. We believe that this tool can do the same for you and your team.

If interested, feel free to [download Flow from GitHub](https://github.com/internetguru/flow). Check out the tutorial for an easy way to get started. Your feedback is welcome as well as suggestions and contribution.
