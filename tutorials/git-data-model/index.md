---
layout: tutorial
title: Under the Hood of Git
---

This tutorial is based on the [Git Internals Chapter](https://git-scm.com/book/en/v2/Git-Internals-Git-Objects) of the [Official Git Book](https://git-scm.com/book/en/v2).

## Learning Objectives

After doing this tutorial you will know how to

* Locate the internal contents of a git repository
* Explain how git uses SHA1 hashes to track content
* Distinguish between the types of objects stored internally by git (blobs, trees and commits)

You will also know how to use internal git commands that do the underlying work behind the `git add`, `git commit` and `git branch` commands:

* Add files and blobs to git's internal object store using the `hash-object` command
* Add files to git's staging area using the `write-tree` command
* Create a git commit using the
 `commit-tree` command
* Create a git branch using the internal  `git update-ref` command

## Prerequisites

To do these lessons you will need to have installed

* Git
* A command-line terminal program
* A text editor

## Lessons

1. [Preface: Stream Redirection and Piping](lessons/redirection-and-piping)
2. [Preface: Hashing](lessons/hashing)
2. [Git Internals: Hash Objects](lessons/hash-objects)
3. [Git Internals: Tree Objects](lessons/tree-objects)
4. [Git Internals: Commit Objects](lessons/commit-objects)
5. (optional) [Git Internals: Object Storage](lessons/object-storage)
6. [Git Internals: Git References](lessons/git-references)
7. [Git Internals: Git HEAD Reference](lessons/git-HEAD-reference)
