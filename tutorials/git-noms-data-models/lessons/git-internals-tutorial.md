---
layout: lesson
title: Git Internals - Git Objects
category: git-noms-data-models
tags:
---

## Prerequisites

In order to understand the steps in this tutorial, you should be familiar with:

* Using `cat` command on the command line to read files
* Using unix pipes to write files on the command line
* Using hash functions like sha1 or md5 to calclulate the hashes of files, text, and any other content

## Goals (Learning Objectives)

After doing this tutorial you will know how to

* Locate the internal contents of a git repository
* Explain how git uses SHA1 hashes to track content
* Distinguish between the types of objects stored internally by git (blobs, trees and commits)

You will also know how to use internal git commands that do the underlying work behind the `git add`, `git commit` and `git branch` commands

* Add files and blobs to git's internal object store using the `hash-object` command
* Add files to git's staging area using the `write-tree` command
* Create a git commit using the
 `commit-tree` command
* Create a git branch using the internal  `git update-ref` command

## Activities

### Step 1:

Read the introduction to the Git Internals chapter of the Official Git Book:
[Git Internals - Plumbing and Porcelain](https://git-scm.com/book/en/v2/Git-Internals-Plumbing-and-Porcelain)

### Step 2: Git Internals Tutorial

Follow the [Git Internals - Git Objects](https://git-scm.com/book/en/v2/Git-Internals-Git-Objects) in the [Official Git Book](https://git-scm.com/book/en/v2).

The **Object Storage** section at the end of the tutorial is optional. It covers the deep internals of how git packs and compresses the contents of blob objects. This also (indirectly) explains why you


```bash
echo 'test content' | git hash-object --stdin
```

```bash
echo 'test content' | shasum
```
or

```bash
git hash-object test.txt
```

```bash
shasum test.txt
```



### Step 3: Test Your Understanding

 1. When you run `git checkout master`, which internal commands does that trigger?
 2. When you run `git add`, which internal commands does that trigger?
 3. Which git command triggers the `write-tree` internal command? What does that command do?

### Step 4: Tutorial on Git References
Create a git branch using the internal  `git update-ref` command

### Step 5: Test Your Understanding of Git References

## Next Steps

If you want to learn more about git internals, proceed with the sections in the Git book on [Packfiles](https://git-scm.com/book/en/v2/Git-Internals-Packfiles)
