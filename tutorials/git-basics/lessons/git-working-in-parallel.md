---
layout: lesson
title: Using Git to Work in Parallel
category: git-hands-on
tags:
---

## Goals (Learning Objectives)

This lesson reviews the things you learned in the [Github Workflow](lessons/github-workflow)
and [Git Command Line Interface](lessons/git-cli) lessons and applies them to a situation where two people are making changes to files in the same git repository.

After doing this tutorial you will know how to

* Fork someone else's Github repository
* Submit Pull Requests to someone else's Github repository
* Resolve merge conflicts

## Activities

### Step 1: Find a Partner

This Lesson is designed to be done in pairs so that you can see what happens when two people work on the same git repository at the same time.  Find a partner to work with. You don't have to be in the same place -- for example you could coordinate your work with a friend over IRC or Slack.

### Step 2: Submit and Review a Pull Request

This step is a review of the activities from the [Github Workflow](lessons/github-workflow)
and [Git Command Line Interface](lessons/git-cli) tutorials.

1. **Partner 1**: fork a repository owned by Partner 2
2. **Partner 1**: make some changes to a file in the repository you forked
3. **Partner 2**: make changes in a different file within the repository
4. **Partner 2**: commit your changes and push them to the repository on github
3. **Partner 1**: push your changes to github and create a pull request with those changes
4. **Partner 2**: merge the Pull Request

### Step 3: Cause a Merge Conflict and Resolve it

1. **Partner 2**: fork a repository owned by Partner 1
2. **Both Partners**: make _different_ changes on the _same line_ of a file in the repository
3. **Both Partners**: commit your changes and push them to github
4. **Partner 2**: create a pull request with your changes
5. **Both Partners**: work together to resolve the merge conflict in the Pull Request
6. **Partner 1**: merge the pull request
