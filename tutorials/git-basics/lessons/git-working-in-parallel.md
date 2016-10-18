---
layout: lesson
title: Using Git to Work in Parallel
category: git-basics
tags:
---

## Goals (Learning Objectives)

This lesson reviews the things you learned in the [Github Workflow](lessons/github-workflow) lesson and applies them to a situation where two people are making changes to files in the same git repository.

After doing this tutorial you will know how to

* Fork someone else's Github repository
* Submit Pull Requests to someone else's Github repository
* Resolve merge conflicts

## Activities

### Step 1: Find a Partner

This Lesson is designed to be done in pairs so that you can see what happens when two people work on the same git repository at the same time.  Find a partner to work with. You don't have to be in the same place -- for example you could coordinate your work with a friend over IRC or Slack.

In these instructions, we will call the two partners **Alex** and **Jamie**; decide which one of you will play each role.

### Step 2: Submit and Review a Pull Request

1. **Alex**: Go to the Github page for a repository owned by Jamie.  In the upper-right corner, click the "Fork" button.  This will create a duplicate copy of Jamie's repository that you (Alex) now own.
2. **Alex**: Make some changes to a file in your forked repository, and then commit your changes.
3. **Jamie**: Make changes in a _different file_ within your own repository, and then commit your changes.
3. **Alex**: Create a pull request with your committed changes.
4. **Jamie**: Write a comment on the pull request, and then merge the pull request.

### Step 3: Cause a Merge Conflict and Resolve it

1. **Jamie**: Fork a repository owned by Alex.
2. **Jamie**: Pick a line in an existing file in this forked repository, and make some changes to that line.  Commit your changes.
3. **Alex**: Make some _different_ changes on the _same line_ of the chosen file, but in your repository.  Commit your changes.
4. **Jamie**: Create a pull request with your committed changes.
5. **Both Partners**: Work together (through comments on the pull request, through Slack, or by talking in person) to resolve the merge conflict in the pull request.
6. **Alex**: Merge the pull request.

## Next Steps

Next, learn how to use the [Git Command Line Interface](../git-cli).
