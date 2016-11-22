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


## Activities



### Step 3: Test Your Understanding of Git Objects

 2. When you run `git add`, which internal commands does that trigger?
 3. Which git command triggers the `write-tree` internal command? What does that command do?
