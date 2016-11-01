---
layout: lesson
title: Noms Command Line Tour
category: noms
tags:
---

## Goals (Learning Objectives)

* Understand how the noms command line works

## Activities

### Step 1: Watch the video of the Noms Command line tour

Go to the [Noms Command Line Tour](https://github.com/attic-labs/noms/blob/master/doc/cli-tour.md) page and watch teh video.

### Step 2: Do the Command Line Tour

Follow the steps of the [Noms Command Line Tour](https://github.com/attic-labs/noms/blob/master/doc/cli-tour.md).

### Some Notes

In the command line tour, under the **noms sync** section, the tour tells you to run:
```
> go install github.com/attic-labs/noms/samples/go/csv/...
```

Sometimes this command returns a warning like
```
warning: "github.com/attic-labs/noms/sample/go/csv/..." matched no packages
```

**It's ok!** If you followed the [installation instructions in the previous lesson](../install-noms), you can ignore this step and proceed with the tour, starting with the next command it lists:

```
> csv-export /tmp/noms::films > /tmp/film-locations.csv
```

## Next Steps
When you're done with the command line tour, go back to the [Intro to Noms workshop](../../) and follow the link to _Tour the Noms Golang API_.
