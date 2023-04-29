---
title: flow-deploy
tags:
---

Note: Flow defines default names for key branches and lets you specify your own. In existing repositories, Flow automatically adapts to existing branches that match common naming conventions, such as 'develop' instead of the default 'dev'.

For consistency purposes, Flow makes sure the staging branch does not completely vanish even after releasing. This benefits continuous deployment again for the sake of running a beta-testing environments.

Note that Flow also checks whether local branches are behind their remote counterparts. Flow can effortlessly fix this as well.

There is a set of production branches that Flow automatically maintains – one for each major version. This allows to lock continuous deployment to a specific production branch and independent hotfixing.
