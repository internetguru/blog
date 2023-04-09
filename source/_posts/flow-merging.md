---
title: Merging branches with Flow
date: 2023-04-08 18:44:29
coauthor: George Pavelka
tags:
  - flow
  - merging
---

Git branching models define three key branches: development, staging, and stable. Flow is a command-line developer tool to keep track of those branches and their mutual relations.

<!-- more -->

## Key branches

Flow ensures that key branches exist and are merged into subordinate branches (stable to staging to development). Any irregularities are reported and offered to be corrected automatically by Flow.

For example, releasing a hotfix results in subsequent merges to staging and development branches. Similarly, Flow checks for the staging branch being merged into development and offers to fix it for you.

Flow defines default names for the key branches and lets you specify your own. In existing repositories, Flow automatically adapts to existing branches that match typical naming conventions, such as 'development' instead of the default 'dev'.

## Helper branches

Besides key branches, Flow can recognize feature branches and hotfix branches. In addition to features, merging hotfixes into the stable branch requires additional merging. Flow also checks for potential collisions *before* the actual merging happens.

According to branching models, the stable branch needs to be merged with the development and the (unreleased) staging branches. Flow takes care of that automatically, including {% post_link flow-version 'version incrementing' %} and {% post_link flow-changelog 'changelog handling' %}.

## Additional branches

There is a set of production branches that Flow automatically maintains – one for each major version. This is especially handy for continuous deployment. On top of that, Flow supports hotfixing of these branches regardless of their age.

For consistency purposes, Flow makes sure the staging branch does not completely vanish even after releasing. This benefits continuous deployment again for the sake of running a beta-testing environments.

Note that Flow also checks whether local branches are behind their remote counterparts. Flow can effortlessly fix this as well.

## Try Flow today

Branching models introduce significant overhead in terms of merging and integration. Flow automates these tasks and saves lots of time and unnecessary mistakes. With Flow, you can be sure the project is compliant and you can focus on the development.

If interested, feel free to [download Flow from GitHub](https://github.com/internetguru/flow). Check out the tutorial for an easy way to get started. Your feedback is welcome as well as suggestions and contribution.
