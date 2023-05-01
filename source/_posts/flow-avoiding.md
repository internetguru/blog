---
title: Avoiding Git branching models
date: 2023-04-30 21:35:55
copyright_author: George Pavelka
cover: /images/b55bf970-b043-493b-aa10-044b61ee79e0.jpeg
categories: flow
tags:
    - cli
    - git
    - automation
    - development
keywords:
    - git branching models
    - simplicity
    - workflow
    - integration
    - collaboration
    - performance
    - git flow
    - project size
---

# Avoiding Git branching models

There are several Git branching models from very basic to complex. I asked ChatGPT what reason there could be to avoid Git branching models – apart from ignorance. It provided several valid points, so I decided to publish it with comments and examples from my own experience.

## 1. Simplicity

> In small projects or when working alone, developers might find a branching model to be overkill, preferring a simpler linear history to keep their work straightforward.

This follows up a common question – whether all our projects use Git Flow. Of course not. Some of our small scripts even share a common project for the sake of incremental backups. It is easy to switch to a branching model when a small project starts growing and requirements show up.

On the other hand, all our projects that use Git branching model, use Git Flow branching model. The reason is that Flow reduces its maintenance overhead to a minimum.

## 2. Workflow preference

> Developers might have their own preferred workflow that doesn't involve a branching model, or they might be using another version control system that doesn't support branching as effectively as Git.

Another version control system that doesn't support branching may need to be replaced. This is easier said than done especially with larger projects. The only way is to run a cost-benefit analysis.

A preferred workflow that does not involve a branching model is usually either vague (non-deterministic) or a slightly disrupted or sometimes even enhanced existing branching model. Transitioning to a deterministic branching model is usually easy and relieving once all benefits are realized.

## 3. Learning curve

> For some developers, especially those new to Git, the learning curve associated with adopting a branching model might be a deterrent, as they may find it more challenging to understand and implement than simpler workflows.

Sure, for certain jobs, even a basic Git usage can be overwhelming. Introducing more complex branching strategies adds another layer of complexity. It is yet another factor to consider when deciding about a branching model.

For junior developers and external workers with no skills or ambitions in Git, there are workarounds depending on their engagement. Flow could be a suitable workaround, provided it is integrated properly.

## 4. Integration with external tools

> Certain tools or platforms might not support or integrate well with a Git branching model, leading developers to opt for a different workflow to ensure compatibility.

Changing the incompatible tools may be just another factor to consider within the cost-benefit analyses. Flow is highly compatible when it comes to integrating due to its simplicity and versatility. For more information, see the Flow man page.

## 5. Collaboration challenges

> In some team environments, introducing a branching model might be seen as adding complexity and potential for confusion, making it harder for team members to coordinate and collaborate effectively.

Using Flow, most of the common development is simplified down significantly with minimum overhead. Additionally, linear development can be arranged for individual tasks like creating unit tests or performing quality assurance.

## 6. Resistance to change

> Developers might be resistant to change, especially if they have been using a particular workflow for a long time and see no reason to adopt a new model.

Seeing no reason to adopt a new model feels like ignorance to me. However an irrational resistance to change is a severe and very common reason to reject a branching model in my experience.

You know the saying: the worst part of any change is that something is different. Make sure you are considering relevant factors, such as how much the change will cost and what it will bring.

## 7. Performance considerations

> In some cases, a Git branching model could introduce additional overhead in terms of merging and integration, leading to potential performance issues or merge conflicts that developers might wish to avoid.

This is my favorite reason. Especially with complex models, such as Git Flow, the overhead can be significant. With Flow, the overhead is reduced significantly as demonstrated in other articles about Flow.

## Try Flow today

In my experience, the only rational reason to avoid any kind of branching model is project size and the absence of requirements. There is a working example of using Flow on the Flow man page. See for yourself how easy it feels to maintain the most complex branching model including a feature, release candidate, bug fixing, and hot fixing.

If you're interested, feel free to [download Flow from GitHub](https://github.com/internetguru/flow). Check out the tutorial for an easy way to get started. Your feedback is welcome as well as suggestions and contribution.
