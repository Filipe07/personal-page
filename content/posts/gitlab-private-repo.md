---
author: "Filipe Gonçalves"
title: "Gitlab Composer Packages with Private Repositories"
date: "2021-04-20"
description: "Gitlab Composer Packages with Private Repositories"
tags: ["gitlab", "composer", "private-repositories"]
hideMeta: true
searchHidden: true
ShowBreadCrumbs: false
---

![](https://cdn-images-1.medium.com/max/3200/0*u7fDDmzbbvWuwDLb)

For those who use Composer to manage the dependencies of PHP projects, the goal usually is to add all the dependencies for a certain release version, for example:

 <iframe src="https://medium.com/media/05965c3ebf4144413def4432da859fbf" frameborder=0></iframe>

When using Gitlab with the self-managed version and with dependencies on private repositories, it is not possible to point to the **release number** or **tag**, but only to **branch name**.

Despite having Googled this “problem” a few times, I never found the solution and then ended up using the name of the branches. Although the behavior is the desired, it seriously affects the OCD of those who like to keep the composer.json file consistent (jokes aside, it hurts my eyes).
For example, it is common to have a file that looks like this:

 <iframe src="https://medium.com/media/a4b10f1745e69bdd8d275db22e1ff64b" frameborder=0></iframe>

## **Packages & Registries**

Through the “Packages & Registries” functionality of Gitlab (https://docs.gitlab.com/ee/user/packages/) it is possible to publish a version of a project so that it can be loaded by the release version and not by branch name.

To publish the package version, simply add the following lines to the CI/CD pipeline configuration file gitlab (*.gitlab-ci.yml*):

 <iframe src="https://medium.com/media/bcba674a83f7c68ca29ab714aaa35c97" frameborder=0></iframe>

From now on, whenever a branch has an associated tag (for example, 1.2.3), the Package will be registered and can be loaded through the version number.

To see all published packages, just go to **Packages & Registries**  > **Package Registry**.

Let me know if this tip helped you in any of your projects!
