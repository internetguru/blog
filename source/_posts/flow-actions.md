---
title: Flow's action decision tree
date: 2023-04-16 13:49:31
copyright_author: George Pavelka
cover: /images/3360cdd0-bc7e-44c2-8ce9-fd8a8d60492b.jpeg
categories: Flow
keywords:
  - tools
  - branching
  - action
tags:
  - cli
  - git
  - automation
  - development
---

# Flow's action decision tree

Advancement in branching models is mostly deterministic. That's why branching models often have 'flow' in their names. Internet Guru Flow is a CLI tool for developers designed to automate the flow.

Flow advances (flows) on a branching model. By default it releases the current branch into a proper destination. Let's explore how Flow determines the destination and how you can influence it.

## Flow key branches

Flow distinguishes three key branches – development, staging, and stable. The development branch is released to the staging branch. The staging branch is released to the stable branch.

Note: Technically, each of its commits needs to be merged into the development branch. Read more about {% post_link flow-merging 'merging with Flow' %}.

By design, the stable branch can only proceed into a hotfix. If Flow runs on a stable branch without an argument, a default hotfix is created.

## Flow hotfixes and features

Any other existing branch besides the key branches is considered either a hotfix or a feature. This is determined by its relation to the stable branch and development branch respectively.

Features are merged into the development branch. Similarly hotfixes are merged to stable branch and an appropriate production branch (see below) according to the major version number.

Note: Using 'hotfix' or 'feature' keywords flows a default hotfix or feature branch. The default branch is either created or merged according to its existence.

## Flow to new branches

Feature branches are created from the development branch. Running Flow with an argument on the development branch creates a new feature with that name. Hotfixes work on the same principle when run from stable or production branches.

Production branches are stable branches for separate major versions, like 'prod-1'. Running Flow on them creates a hotfix respecting their major version. Therefore, merging such a hotfix will affect the appropriate production branch.

## Try Flow today

Flow focuses on simplicity in usage. No argument is required unless you want to specify a different or new branch to flow. Before proceeding, Flow offers the action to the user to confirm.

If interested, feel free to [download Flow from GitHub](https://github.com/internetguru/flow). Check out the tutorial for an easy way to get started. Your feedback, suggestions, and contributions are welcome.
