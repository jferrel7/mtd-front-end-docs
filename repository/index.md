---
layout: default
title: MTD Front-End Docs / Repository
---

# Repository (Repo)

* [Version Control](#version-control)
* [Cloning the Repo](#cloning-the-repo)
* [Commits](#commits)

### Version Control

The repository for the MTD front-end code uses Git for version control and is stored on Bitbucket to allow collaboration. 

### Cloning the Repo

From a command prompt, go to the directory where you would like the repo stored on your computer and use one of the two following options.

#### 1. Using SSH

You will need to setup SSH on your Bitbucket account before you can clone via SSH. See: [Using SSH with Bitbucket - Instructions](https://confluence.atlassian.com/bitbucket/use-the-ssh-protocol-with-bitbucket-cloud-221449711.html). 

Once SSH is set up on your Bitbucket account and you are in the directory where you would like the repo stored via a command prompt.  Type `git clone git@bitbucket.org:jferrell/mtd-shared-checkout.git`

You can now change to the mtd-shared-checkout directory to verify you have the files.

#### 2. Using HTTPS

Once you are in the directory where you would like the repo stored via a command prompt.  Type `git clone https://{insert_bitbucket_username}@bitbucket.org/jferrell/mtd-shared-checkout.git`

You can now change to the mtd-shared-checkout directory to verify you have the files.

### Commits

Before doing any work, it's best to pull down any changes from Bitbucket. Type `git pull origin master`.

As we are working across many sites, it is helpful for commit messages to include the site you are working on. For example, `git commit -m 'troybilt: product detail template complete'
