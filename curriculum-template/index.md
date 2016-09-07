---
layout: page
title: Curriculum Template
---

## Curriculum Structure

A Curriculum is made up of Courses, Learning Modules, and Activities  

### Directory structures

The template assumes that you structure your curriculum like this:

#### Minimal Structure
If your lessons are relatively simple and straightforward, you can use a structure like this:

```
|-- summary.md
|-- tutorial-name
|   |-- index.md
|   |-- lessons
|   |   |-- lesson-name.md
```

#### More Structure

If your lessons are bigger and include lengthly activities that need a lot of context or explanation, you can use this more deeply nested structure to put each activity on its own page:

```
|-- summary.md
|-- tutorial-name
|   |-- index.md
|   |-- lessons
|   |   |-- lesson-name
|   |   |   |-- index.md
|   |   |   |-- activities
|   |   |   |   |-- activity-name.md
```

For your reference, this git repository contains a complete sample curriculum in its [curriculum directory](https://github.com/flyingzumwalt/jekyll-curriculum-template/tree/gh-pages/curriculum).  In fact, you're reading the overview page from that curriculum now!

## Tutorials

See the [Tutorial Template](tutorial-template)

## Lessons

See these two options  

* [Simple Lesson Template](tutorial-template/lessons/simple-lesson-template)
* [Complex Lesson Template](tutorial-template/lessons/complex-lesson-template)

## Activities

For simple lessons you can put the activities directly into the lesson markdown file. If you want to split the activities within a lesson into their own files, see the  [Complex Activity Template](tutorial-template/lessons/complex-lesson-template/activities/activity-template)
