---
layout: lesson
title: Install Noms
category: git-basics
tags:
---

## Goals (Learning Objectives)

After doing this tutorial you will know how to

* Install Noms on a unix-flavored OS
* Put Noms on your command line

## Activities
These steps roughly follow the [Setup instructions on the Noms README](https://github.com/attic-labs/noms#setup).

### Step 1: Download the latest build

1. Use your web browser to go to [https://github.com/attic-labs/noms#setup](https://github.com/attic-labs/noms#setup).
2. Click the "download the latest Noms build" link.
3. On this page, there are directories for several different Noms versions.  Pick the highest-numbered one.
4. Download the .tar.gz file for your architecture (Mac OS X is "darwin").

### Step 2: Make a noms directory
1. Create a directory within your homedir called "lib", and one inside that called "noms".  (You can do that with `mkdir -p ~/lib/noms` ).

### Step 3: Extract the tar file
1. Move the downloaded .tar.gz file into the `~/lib/noms` directory.
2. Extract the .tar.gz file: `tar -xvzf noms-*.tar.gz`

### Step 4: Add Noms to your Executable Path

1. Make a "bin" directory in your homedir: `mkdir -p ~/bin`
2. Move into your new bin directory ( `cd ~/bin` ).
3. We're going to create "symlinks" from the noms executables that you extracted from the .tar.gz file into this bin directory.  The following code snippet assumes you are using Bash, which you can check by doing `echo $SHELL` on the command line.  Provided that you see `bash` as the response, you're all set to do the following:

    ```
    for f in ~/lib/noms/*; do ln -s $f .; done
    ```

4. Run `pwd` and take note of the response.  This tells you the full path of your homedir bin directory.  For example, mine is `/Users/jadrian/bin`, but yours will be different.
5. Check whether this directory is in your path.  Do `echo $PATH` and you should see a list of directory paths separated by colons.  Look for your bin directory; for example, I'm looking for `/Users/jadrian/bin`.
6. If you don't see the homdir `bin` directory in your path, you need to add it by editing your `.bashrc` or `.bash_profile` file.  Open either of those files in your text editor and add the following line somewhere:
    
    ```
    export PATH=$HOME/bin:$PATH
    ```
    
    Then save the file and go back to your command line.

7. Run `env bash` to restart your shell and then `echo $PATH` again.  You should see your homedir bin directory near the beginning of the list now.
8. Go to your home directory and run `which noms`; you should see the path to the Noms executable in your bin directory.  Then run `noms` and you should get a help message.  This means Noms is installed!

## Next Steps
Go back to the [Intro to Noms workshop](../../) and proceed to the next step.
