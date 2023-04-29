---
title: Version handling with Flow
date: 2023-04-05 09:15:28
copyright_author: George Pavelka
cover: /images/d9c1cdb7-30dc-4b9b-be3a-94377ef87800.jpeg
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
    - merging
---

# Version handling with Flow

In branching models, version numbers play a crucial role. Flow is a command-line developer tool to maintain software projects compliant with a branching model. Additionally, Flow offers robust version handling and ensures that version numbers are always in compliance with the model.

## Validation and compliance

Flow ensures all version files are present and valid. For example, the development major or minor version must be greater than the staging version. Not only Flow can verify versions, it will report irregularities and offer to correct them.


``` plaintext Before
            A prod [0.0.0]
             \
              B---C develop [0.0.0] (invalid)
```

``` plaintext After
            A prod [0.0.0]
             \
              B---C develop [0.1.0] (fixed)
```

Similarly, the (unreleased) staging version must be greater than the production version and lower than the development version. Flow can fix that too including missing version files as well as invalid version format.

## The release process

During the general release process (from dev to staging to production), Flow preserves the source version value. After a first release candidate is created, Flow automatically increments minor version on dev for future releases.

``` plaintext Before
            A prod [0.0.0]
             \
              B---C develop [0.1.0]
```

``` plaintext After
            A prod [0.0.0]
             \
              \       D staging [0.1.0]
               \     /
                B---C develop [0.2.0]
```

When the development branch is released multiple times (without the staging branch being released), versions on the development and staging branches remain the same. However, the release candidate number increases. Read more about {% post_link flow-changelog 'handling changelog with Flow' %}.

Note: Schemes only show the most relevant information for the current topic. They are simplified and miss (otherwise important) information such as tags, branches, and even commits that occur during operations like this.

## Hotfixing

When released, the hotfix is merged into the production branch (non-fast-forward). Flow automatically increments the patch version number. It also removes the hotfix branch and prompts for a changelog entry.

``` plaintext Before
                  A---B---C hotfix [0.1.0]
                 /
            D---E prod [0.1.0]
```

``` plaintext After
                  A---B---C
                 /         \
            D---E-----------F prod [0.1.1]
```

The hotfix version is not incremented until being merged. That supports multiple parallel hotfixing. Hotfixes are also released into corresponding separate production branches based on their major version. Read more about {% post_link flow-merging 'merging branches with Flow' %}.

## Try Flow today

Flow's version handling capabilities make it easy to keep track of your project's progress and ensure that your version numbers are always in compliance.

If interested, feel free to [download Flow from GitHub](https://github.com/internetguru/flow). Check out the tutorial for an easy way to get started. Your feedback is welcome as well as suggestions and contribution.
