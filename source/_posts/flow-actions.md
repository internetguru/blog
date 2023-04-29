---
title: Flow's action decision tree
date: 2023-04-16 13:49:31
copyright_author: George Pavelka
cover: /images/3360cdd0-bc7e-44c2-8ce9-fd8a8d60492b.jpeg
categories: flow
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

Flow recognizes three key branches – development, staging, and production. These branches 'flow' into each other in the given order. Development into staging and staging into production. The production branch can only 'flow' into its hotfix. The same is true for individual 'major' branches (e.g. `prod-1`) that follow the production branch while matching its major version.

- Command `flow` on the *develop* branch results into action 'release development branch'.
- Command `flow` on the *staging* branch results into action 'release staging branch'.
- Command `flow` on the *production* or *major* branch results into command `flow hotfix` (see below).

Running Flow with a key branch argument results into similar actions. This works regardless of the current branch.

- Command `flow develop` results into action 'release development branch'.
- Command `flow staging` results into action 'release staging branch'.
- Command `flow prod` or `flow prod-1` results into command `flow hotfix` (see below).

## Flow hotfixes and features

Any other existing branch besides key branches is considered a feature or hotfix. Flow tells one from another by their relation to key branches. Features are merged into the development branch. Similarly hotfixes are merged to production branch and into the corresponding 'major' branch (see above).

- Command `flow` on a *feature* branch results into action 'release feature'.
- Command `flow` on a *hotfix* branch results into action 'release hotfix'.

Using a 'hotfix' or 'feature' keyword results into a hotfix or feature action regardless of the current branch. The default hotfix or feature branch is either created or merged according to its existence.

- Command `flow feature` results into action 'create/release default feature'.
- Command `flow hotfix` results into action 'create/release default hotfix'.

## Flow arbitrary branches

As stated above, any arbitrary branch is considered either a feature or hotfix. Therefore running Flow with an arbitrary branch name argument results in creating or releasing a feature or a hotfix of that name with the following logic.

1. If the specified branch exists, it is merged accordingly (as a feature or hotfix).
2. Else if on a production branch (or a 'major' production branch), a hotfix is created.
3. Else a new feature is created.

## Try Flow today

Flow focuses on simplicity in usage. No arguments are required unless you want to specify a different or new branch. Flow always asks before proceeding.

If interested, feel free to [download Flow from GitHub](https://github.com/internetguru/flow). Check out the tutorial for an easy way to get started. Your feedback, suggestions, and contributions are welcome.
