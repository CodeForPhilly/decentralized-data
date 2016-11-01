---
layout: tutorial
title: Versioning Data with Git and Noms
---

It has become common for researchers to use Git to track their datasets by exporting the data to CSV files and adding those CSV files to Git. They also often publish those datasets to github. This runs into some issues because Git was not designed to track datasets. By contrast, Noms was designed specifically to track datasets.  This workshop allows you to experience what it's like to use each of these two tools to track a dataset so that you can compare and contrast the two tools.

## Prerequisites

Before proceeding with the lessons in this workshop, you should have both git and noms installed.  You should also be familiar with the material covered in these workshops:

* [Git basics](../git-basics)
* [Actually using Git](../actually-using-git)
* [Intro to Noms Tutorial](../noms)

## Learning Objectives

After this workshop you will know how to

* Use either Git or Noms to track CSV datasets
* Find free, open source datasets on Github
* Describe the technologies of Git, Noms, and CSV in terms of their
  * Overall Strengths & Weaknesses as tools for tracking data
  * Constraints -- What kinds of uses does the technology encourage? Which uses does it make hard or impossible?

## Lessons

1. [Find an Open Source Dataset on github and fork it](lessons/find-a-dataset)
2. [Clone the dataset to your local machine](lessons/clone-the-dataset)
3. [Import the dataset into Noms and publish the dataset](lessons/import-the-dataset-into-noms)
4. [Make some changes to the dataset and import them](lessons/import-dataset-changes)
7. [Make a lot of changes to the dataset and import them](lessons/import-lots-of-dataset-changes)
9. [Compare Git and Noms](lessons/compare-the-experiences): Compare the experience of using these two tools to track versions of datasets
10. [Compare CSV and Code](lessons/discuss-csv-vs-code): Discuss how (tabular) data like CSV is similar to other text files and how it's different
