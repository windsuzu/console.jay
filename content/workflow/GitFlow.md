---
draft: false
date: 2023-11-29 16:07
tags:
  - workflow
---

The **GitFlow source control branching model** typically involves three default branches (`dev`, `release`, `master`) and multiple feature branches checked out from `dev` and created by different developers or teams.

- **Develop branch**: is a branch that collects the developed features.
- **Release branch**: is a branch that is responsible for version release.
- **Master branch**: is a branch that stores the baseline of the latest released version.
- **Feature branch**: is a branch for developers to develop features.

The feature branch usually includes more than one commit to implement a single feature. Additionally, there may be multiple fix and review commits before merging the pull request.

![[gitflow.png]]
> Image source: [Git Flow vs. Trunk Based Development | Toptal®](https://www.toptal.com/software/trunk-based-development-git-flow)

![[gitflow2.png]]
> Image source: [How to Select a Git Branch Mode? - Alibaba Cloud Community](https://www.alibabacloud.com/blog/how-to-select-a-git-branch-mode_597255)



> [!info] References
> - [Git Flow vs. Trunk Based Development | Toptal®](https://www.toptal.com/software/trunk-based-development-git-flow)
> - [How to Select a Git Branch Mode? - Alibaba Cloud Community](https://www.alibabacloud.com/blog/how-to-select-a-git-branch-mode_597255)
