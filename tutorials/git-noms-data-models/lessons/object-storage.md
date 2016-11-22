---
layout: lesson
title: (optioanl) Git Internals - Commit Objects
category: git-noms-data-models
tags:
---

## Goals (Learning Objectives)

This section is optional. It gets into deep technical details about how git creates hash objects. It also (indirectly) explains why the sha1 hashes created by `git hash-object` are different from the hashes returned by a simple sha1 command like `shasum`. *If you're not curous about those details, It's ok to skip this section.*

After doing this tutorial you will know how to

* explain how git creates hash objects using headers, gzip and a SHA1

## Activities

### Step 1: Git Internals - Object Storage

Read the section under the heading 'Object Storage' on the [Git Internals - git References](https://git-scm.com/book/en/v2/Git-Internals-Git-References#Object-Storage) page. **Don't proceed to the next page.** We will cover that in the next lesson.

## Next Steps

Proceed to the [Git References](../git-references) lesson.
