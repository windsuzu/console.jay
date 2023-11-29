---
draft: false
date: 2023-11-29 15:10
tags:
  - tbd
  - workflow
---

**Trunk-based development (TBD)** is a source control branching model that involves creating only one healthy branch, typically named `trunk`, `main`, or `master`. In this approach, developers all work on the same branch without creating any long-lived branches. 

> [!note]
> **TBD** differs from other [feature branching models](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow), such as [[GitFlow]], which may contain multiple long-lived feature branches.

![[trunk-based-development.png]]
> Image source: [Git Flow vs. Trunk Based Development | Toptal®](https://www.toptal.com/software/trunk-based-development-git-flow)

![[trunk-based-development2.png]]
> Image source: [How to Select a Git Branch Mode? - Alibaba Cloud Community](https://www.alibabacloud.com/blog/how-to-select-a-git-branch-mode_597255)

Here are the caveats you need to be aware of before you and your team integrate TBD into your workflow:

1. A small team can [commit directly to the trunk branch](https://trunkbaseddevelopment.com/committing-straight-to-the-trunk/), whereas a larger team may create [short-lived branches](https://trunkbaseddevelopment.com/short-lived-feature-branches/) and [pull requests](https://trunkbaseddevelopment.com/continuous-review/) for team review and CI checks.
2. The team can choose to create a [release branch](https://trunkbaseddevelopment.com/branch-for-release/) to enable deployment to production.
3. 




> [!info] References
> - [What is the "best way" to develop software applications? - YouTube](https://www.youtube.com/watch?v=oNmcX6Gozg0)
> - [Introduction (trunkbaseddevelopment.com)](https://trunkbaseddevelopment.com/#one-line-summary)
> - [Git Flow vs. Trunk Based Development | Toptal®](https://www.toptal.com/software/trunk-based-development-git-flow)
> - [How to Select a Git Branch Mode? - Alibaba Cloud Community](https://www.alibabacloud.com/blog/how-to-select-a-git-branch-mode_597255)
> - [團隊的 GIT 分支管理策略 (3) | by fin](https://medium.com/%E5%93%88%E5%98%8D-%E4%B8%96%E7%95%8C/%E5%9C%98%E9%9A%8A%E7%9A%84-git-%E5%88%86%E6%94%AF%E7%AE%A1%E7%90%86%E7%AD%96%E7%95%A5-3-%E6%8C%81%E7%BA%8C%E6%95%B4%E5%90%88%E4%BB%A5%E5%8F%8A%E7%9B%B8%E9%97%9C%E6%AF%94%E8%BC%83-59b80a29c997)
