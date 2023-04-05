---
title: Version handling with Flow
date: 2023-04-05 09:15:28
tags:
    - flow
    - version
---
# Version handling with Flow

In the branching models, version numbers play a crucial role. Flow is a powerful CLI developer tool to stick a software project to a branching model. In addition Flow offers robust version handling and ensures that your version numbers are always in compliance with the model.

<!-- more -->

## Validation and compliance

Flow ensures all versions in the branching model are present and compliant with the branching model. For example, the development version must be greater than the staging version, and the (unreleased) staging version must be greater than the stable version.

Not only Flow can verify version numbers, it will report irregularities and suggest fixing them for you. With the ‘conform’ parameter, it will fix missing version files as much as invalid version numbers. It will do so for all key branches consecutively.

## Versions during releasing

During the general release process from dev to staging to production, Flow maintains the version being released. However, after releasing dev to staging, Flow automatically increments the minor version on dev for future releases. This also meets the branching model requirements.

When the development branch is released repeatedly (before the staging branch is released), versions on dev and staging remain the same. However, the release candidate number increases. Read more about changelog handling with Flow.

Flow automatically increments the patch version number when a hotfix is released. Multiple parallel hotfixes are versioned consecutively in the order of their release. Additionally each hotfix is also released into an appropriate separate stable branch according to its major version.

In conclusion, Flow's version handling capabilities make it easy to keep track of your project's progress and ensure that your version numbers are always in compliance. To try out Flow and learn more about version handling and other features, visit our GitHub page.
