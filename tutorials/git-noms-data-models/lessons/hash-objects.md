---
layout: lesson
title: Git Internals - Hash Objects
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
* Add files and blobs to git's internal object store using the `hash-object` command


## Activities

### Step 1: Keep a notepad for hashes

Open a text file that you can write notes into while you work.

While going through these lessons, whenever a git command returns a hash, copy that hash, paste it into the notepad and add a note so you can remember what content that hash points to.

This is because future steps might ask you to use that hash as the input for a command.

### Step 2: Introduction

Read the introduction to the Git Internals chapter of the Official Git Book:
[Git Internals - Plumbing and Porcelain](https://git-scm.com/book/en/v2/Git-Internals-Plumbing-and-Porcelain)

### Step 3: Git Internals - Hash Objects

Read the first section of the page on [Git Internals - Git Objects](https://git-scm.com/book/en/v2/Git-Internals-Git-Objects). **Stop at the heading 'Tree Objects'.** We will cover that in the next lesson.


## Next Steps

Proceed to the [Tree Objects](../tree-objects) lesson.
