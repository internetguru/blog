---
title: Merging branches with Flow
date: 2023-04-12 18:44:29
copyright_author: George Pavelka
cover: /images/50356bcb-b5bd-4a68-a065-8b8873786730.jpeg
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

# Merging branches with Flow

In accordance to typical git branching models, Flow defines key branches, feature and hotfix branches, and individual major branches. It helps developers to keep track of those branches and their mutual relations.

## Merging key branches

Flow ensures that key branches exist and are merged into subordinate branches (production branch to staging, staging to development). Any irregularities are reported and offered to be corrected automatically by Flow. Such as the following bug fixing on staging:

``` plaintext Before
                  A---B---C staging
                 /
            D---E develop
```

``` plaintext After
                  A---B---C staging
                 /         \
            D---E-----------F develop
```

Flow handles more complex merging actions, such as releasing a hotfix. This results in subsequent merges of the hotfix to production branch, production to staging (if not merged), and staging to development branch. It will fix any partial inconsistency as well.

## Merging features

Feature branches are only created from and merged to development branch on demand. Flow also checks for potential collisions *before* the actual merging happens.


``` plaintext Before
                  A---B---C feature
                 /
            D---E---F---G---H develop
```

``` plaintext During
                  A---B---C---I feature
                 /           /
            D---E---F---G---H develop
```

``` plaintext After
                  A---B---C---I
                 /           / \
            D---E---F---G---H---J develop
```

## Merging hotfixes

In addition to features, merging hotfixes requires further merging. According to branching models, the production branch must be merged with the development branch. Flow takes care of that automatically, including {% post_link flow-version 'version incrementing' %} and {% post_link flow-changelog 'changelog handling' %}.

``` plaintext Before
              D---E hotfix
             /
            A prod, staging [0.0.0]
             \
              B---C develop [0.1.0]
```

``` plaintext After
              D---E
             /     \
            A-------F prod, staging [0.0.1]
             \       \
              B---C---G develop [0.1.0]
```

According to branching models, the production branch must be also merged to an (unreleased) staging branch. Flow takes care of that too.

## Merging the staging branch

Flow maintains a staging branch initially attached to the production branch. Releasing the development branch results in a separate staging branch designed for bug fixing. All fixes must be merged back to the development branch until the staging branch is released.

``` plaintext Initial state
            A prod, staging [0.0.0]
             \
              B---C develop [0.1.0]
```

``` plaintext Release develop
            A prod [0.0.0]
             \
              \       D staging [0.1.0]
               \     / \
                B---C---E develop [0.2.0]
```

``` plaintext Bug fix on staging
            A prod [0.0.0]
             \
              \       D---F staging [0.1.0]
               \     / \   \
                B---C---E---G develop [0.2.0]
```

``` plaintext Release staging
            A---------------H prod, staging [0.1.0]
             \             / \
              \       D---F   \
               \     / \   \   \
                B---C---E---G---I develop [0.2.0]
```

Apart from feature and hotfix branches, the staging branch is never removed. It is still present despite being fully merged to production. This allows a consistent CI/CD for the sake of beta-testing.

## Additional production branches

There is a set of production branches that Flow automatically maintains – one for each major version. This allows an independent hotfixing of any major branch anytime in the future.

When releasing a staging branch, Flow makes sure there is a corresponding major branch. Note that there is always a general staging branch matching the most current major branch. Assume the first and the last state from the previous example releasing a major version of `[1.0.0]` instead of minor `[0.1.0]`.

``` plaintext Initial state
            A prod, staging, prod-0 [0.0.0]
             \
              B---C develop [1.0.0]
```

``` plaintext Release staging
            A---------------H prod, staging, prod-1 [1.0.0]
             \             / \
              \       D---F   \
               \     / \   \   \
                B---C---E---G---I develop [1.1.0]
```

Note that there still exists a major branch `prod-0` on commit `A` with a version of `[0.0.0]`. When merging a hotfix, Flow picks its corresponding 'major' branch. That means any major version can be hotfixed independently regardless of when the branch or the hotfix was created.

## Try Flow today

In terms of merging, advanced branching models introduce significant overhead for developers. Flow automates these tasks into a single (often one-word) command. With Flow, you can be sure the project is compliant and you can focus on the development.

If interested, feel free to [download Flow from GitHub](https://github.com/internetguru/flow). Check out the tutorial for an easy way to get started. Your feedback is welcome as well as suggestions and contribution.
