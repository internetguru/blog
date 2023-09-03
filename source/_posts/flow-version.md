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
description: Version numbers play a crucial role in branching models. Flow is a command-line developer tool to maintain software projects compliant with a branching model. Additionally, Flow offers robust version handling and ensures that version numbers are always in compliance with the model.
---

# Version handling with Flow

Version numbers play a crucial role in branching models. Flow is a command-line developer tool to maintain software projects compliant with a branching model. Additionally, Flow offers robust version handling and ensures that version numbers are always in compliance with the model.

{% note info %}
The diagrams presented only display relevant information related to the topic at hand. Additional details, including tags, branches, and commits that occur in the process, are omitted.
{% endnote %}

## Validation and compliance

Flow ensures all version files are present and valid. For example, the development major or minor version must be greater than the staging version. Flow not only verifies versions but also reports irregularities and offers to correct them.

``` plaintext Before
            A prod [0.0.0]
             \
              B develop [0.0.0] (invalid)
```

``` plaintext After
            A prod [0.0.0]
             \
              B---C develop [0.1.0] (fixed)
```

Similarly, the (unreleased) staging version must be greater than the production version and lower than the development version. Flow can fix this as well, including missing version files and invalid version formats.

## The release process

During the general release process, from development to staging to production, Flow preserves the source version value. After the first release candidate is created, Flow automatically increments the minor version on the development branch for future releases.

``` plaintext Initial
            A prod [0.0.0]
             \
              B---C develop [0.1.0]
```

``` plaintext Release develop
            A prod [0.0.0]
             \
              \       E staging [0.1.0]
               \     /
                B---C---D develop [0.2.0]
```

``` plaintext Release staging
            A-----------F prod, staging [0.1.0]
             \         /
              \       E
               \     /
                B---C---D develop [0.2.0]
```

When the development branch is released multiple times without releasing the staging branch, versions on the development and staging branches are preserved. However, the release candidate number increments. Read more about {% post_link flow-changelog 'handling changelog with Flow' %}.

## Hotfixing

Hotfixes are released into the production branch using a non-fast-forward merge. Flow automatically increments the patch version number, removes the hotfix branch, and prompts for a changelog entry.

``` plaintext Before
                  C---D---E hotfix [0.1.0]
                 /
            A---B prod [0.1.0]
```

``` plaintext During
                  C---D---E---F hotfix [0.1.1]
                 /                          ^ based on prod
            A---B prod [0.1.0]
```

``` plaintext After
                  C---D---E---F hotfix [0.1.1]
                 /             \
            A---B---------------G prod [0.1.1]
```

The hotfix version is not incremented until it is merged. This supports multiple parallel hotfixes. Hotfixes are also released into separate production branches corresponding to their major version. Read more about {% post_link flow-merging 'merging branches with Flow' %}.

## Try Flow today

Flow's version handling capabilities make it easy to track your project's progress and ensure that your version numbers are always in compliance.

If you're interested, feel free to [download Flow from GitHub](https://github.com/internetguru/flow). Check out the tutorial for an easy way to get started. Your feedback is welcome as well as suggestions and contribution.
