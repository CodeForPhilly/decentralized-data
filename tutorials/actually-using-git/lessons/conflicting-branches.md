---
layout: lesson
title: Creating and Merging Conflicts on Git Branches
category: actually-using-git
tags:
---

This recreates the example described in the Github help page about [Resolving a Merge Conflict on the Command Line](https://help.github.com/articles/resolving-a-merge-conflict-from-the-command-line/).  You will create a git branch to represent each step in this process:

1. Create a file called planets.md
2. Make conflicting edits to the file on two different branches
3. Merge the changes on a fake "master" branches

You will then merge those changes to the real master branch.  

We use these branches to explore some of the most useful features of git.

## Step: Create a new File

In a git repository, create a file called planets.md with one line of text that reads

```
the number of planets are

```

Just _create_ the file; don't add or commit it in Git quite yet.

## Step: Add the file to a new branch

Create a new git branch called `planets-before-merge-conflict` by running

`$ git branch planets-before-merge-conflict`

Now check out that branch by running

`$ git checkout planets-before-merge-conflict`

**Note:** You can create a branch and check it out with a single command. To create a branch called `planets-before-merge-conflict` and check it out, you could have used `git checkout -b planets-before-merge-conflict` instead of the two commands above.

Add planets.md to git and commit it to the current branch by running

`$ git add .`  
`$ git commit -m"planets.md before merge conflict"`

Now look at the difference between the `master` branch and the `planets-before-merge-conflict` branch by running

`$ git diff master planets-before-merge-conflict`

```
diff --git a/planets.md b/planets.md
new file mode 100644
index 0000000..463f8d5
--- /dev/null
+++ b/planets.md
@@ -0,0 +1 @@
+the number of planets are
```

## Step: Create two working branches

Create two new branches called `branch-a` and `branch-b` by running

`$ git branch branch-a`  
`$ git branch branch-b`  

Compare branch-a and branch-b by running
`$ git diff branch-a branch-b`

**Note:** This didn't return anything because the two branches are identical. Git diff lists all the differences between the two branches. There are no differences between the two branches, so it doesn't return anything.

To confirm that the two branches are identical, look at the git log for each branch

`$ git log branch-a`  
`$ git log branch-b`

The commit messages and the commit hashes should be identical.

## Step : Make a change on branch-a

Check out `branch-a` by running

`$ git checkout branch-a`

Run `git branch` to confirm that you're on the right branch

```
* branch-a
branch-b
master
planets-before-merge-conflict
```

Open planets.md and add "nine" on line 2, so the text looks like:

```
the number of planets are
nine

```

Add this change to git and commit it to the current branch (branch-a)

`$ git add .`  
`$ git commit -m"sets the correct number of planets"`

## Step

Check out `branch-b` by running

`$ git checkout branch-b`

Open planets.md and add "eight" on line 2, so the text looks like:

```
the number of planets are
eight

```

Add this change to git and commit it to the current branch (branch-b)

`$ git add .`  
`$ git commit -m"pluto is not a planet."`

## Step: Compare your edits

Compare `branch-a` and `branch-b` by running

`$ git diff branch-a branch-b`

```
diff --git a/planets.md b/planets.md
index 641c3e9..60b4993 100644
--- a/planets.md
+++ b/planets.md
@@ -1,2 +1,2 @@
 the number of planets are
-nine
+eight
```

## Step: Compare the commit histories

Output the commit history for each branch by running

`$ git log branch-a`  
`$ git log branch-b`

When you compare these two commits, you should see that both of them have the original commit with the message "planets.md before merge conflict" and that commit hash is the same in both branches but each branch has a different commit after this one.  On branch-a there is a commit with the message "sets the correct number of planets" while on branch-b there is a commit with the message "pluto is not a planet." the commit messages are different AND the commit hashes are different.

## Step: Create a fake "master" branch

In normal use, you would merge these changes into the master branch, but for the purposes of this exercise we will create a fake "master" branch. This will let us compare all of the stages of the process before we finish.

To create the fake "master" branch, checkout the `planets-before-merge-conflict` branch which contains the original version of planets.md by running

`$ git checkout planets-before-merge-conflict`

Now create a new "branch-master" branch where we will combine everyone's work

`$ git checkout -b branch-master`  

## Step: Start merging the work into the fake "master" branch

With the `branch-master` branch checked out, merge the work from `branch-a` to `branch-master` by running

`$ git merge branch-a`

```
Updating 8b8c8ee..57c1710
Fast-forward
 planets.md | 1 +
 1 file changed, 1 insertion(+)
```

Now `branch-master` contains the work from `branch-a`

## Step: Confirm that the fake "master" branch has the work from branch-a

Inspect the git log -- at this point branch-master is identical to branch-a.

`$ git log branch-a`  
`$ git log branch-master`

The final commit hashes for both histories should be identical. This means that both histories are identical.

You can also confirm that their contents are identical by running
`$ git diff branch-a branch-master`
If it returns nothing, that means they are identical (there are no differences to display)

## Step: Merge the conflicting branches

Now we need to resolve the conflict between our two branches. While on `branch-master`, run

`$ git merge branch-b`

Git will warn you about the conflict:

```
Auto-merging planets.md
CONFLICT (content): Merge conflict in planets.md
Automatic merge failed; fix conflicts and then commit the result.
```

To get more information about which files are in conflict, run

`$ git status`

```
On branch branch-master
You have unmerged paths.
  (fix conflicts and run "git commit")

Unmerged paths:
  (use "git add <file>..." to mark resolution)

	both modified:   planets.md

no changes added to commit (use "git add" and/or "git commit -a")
```

## Step: Use a text editor to look at the merge conflict

Open planets.md in a text editor. You will see that git has marked the merge conflicts in the file:

```
the number of planets are
<<<<<<< HEAD
nine
=======
eight
>>>>>>> branch-b
```

The conflict is marked with "conflict markers". It begins with `<<<<<<< HEAD` and ends with `>>>>>>> branch-b`.  The changes that came from HEAD (the current branch) are before the `=======` and the changes that came from branch-b are after the `=======`.

## Step: (optional) Use a visual merge tool to look at the merge conflict

Visual merge tools like [Meld](http://meldmerge.org/) make it easier to read merge conflicts and resolve them.

This is a good opportunity to try out one of those tools.

## Step: Resolve the Merge Conflict

As the [github help page](https://help.github.com/articles/resolving-a-merge-conflict-from-the-command-line/) says, to resolve the conflict simply open the file in a text editor, delete the conflict markers, and type out the value you want to put in that line:

```
the number of planets are
nine, or eight, depending on who you ask.

```
Save the edited file and add it to git by running

`$ git add .`  

Confirm that everything is staged properly for the commit by running `git status`.  It should say

```
On branch branch-master
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:

	modified:   planets.md
```

Commit the merged file by running

`$ git commit -m"making peace between branch-a and branch-b"`

## Step: Look at the git history

Run `git log` to see that branch-master now reflects the full history of changes, including the conflicting changes on branch-a and branch-b and the most recent commit, which merges those branches.  It should include commits with all of these messages (in reverse-order because git displays the most recent commits first):

* "planets.md before merge conflict"
* "pluto is not a planet."
* "sets the correct number of planets"
* "making peace between branch-a and branch-b"


## Step Compare against the other branches

Now you have at least 5 branches in your git repository, including the original `master` branch from before you started this lesson.

`$ git branch`

```
branch-a
branch-b
* branch-master
master
planets-before-merge-conflict
```

Compare the contents of these branches using `git diff` and `git log`. For example:

`$ git diff planets-before-merge-conflict master`  
`$ git diff branch-master planets-before-merge-conflict`  
`$ git diff master branch-master`

## Step: Push all of your branches to github

Push all of your branches to github

`git push --all`

```
Counting objects: 16, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (9/9), done.
Writing objects: 100% (16/16), 1.28 KiB | 0 bytes/s, done.
Total 16 (delta 4), reused 0 (delta 0)
remote: Resolving deltas: 100% (4/4), done.
To git@github.com:codeforphilly/decentralized-data-examples.git
 * [new branch]      branch-a -> branch-a
 * [new branch]      branch-b -> branch-b
 * [new branch]      branch-master -> branch-master
 * [new branch]      planets-before-merge-conflict -> planets-before-merge-conflict
```

## Step: Merge your work to the real master branch

Checkout the `master` branch and merge the work from `branch-master`

`$ git checkout master`  
`$ git merge branch-master`

```
Updating 0de7844..72f3743
Fast-forward
 planets.md | 2 ++
 1 file changed, 2 insertions(+)
 create mode 100644 planets.md
```

## Step: Confirm that the master branch has your whole history

Now that you've merged your work into the main `master` branch, you can delete all of the other branches without losing any history because the `master` branch actually contains _all of the work_ from all of the branches, including the entire history of changes. To confirm this, compare the commit hashes that you see when you run `git log master` against the commit hashes in each of the other branches. You will see that the git history in branch-master contains all of the commits from the other branches, with exactly the same commit messages and hashes.

You can also restore a specific state from your history by checking out that commit. To do this, you need the commit hash from running `git log`.  Run `git log` and pick the commit hash for any of the old commits. For example, the hash for the commit with the log message "pluto is not a planet.".  For this example, we will pretend the hash for that commit is ca41886daca7f55aa7d88a5ae7b226dd3e670739.  The first 8 characters will be enough to uniquely identify the hash, so we'll use `ca41886d` in the example.

You can make the working copy of your git repository match the state in that commit by running

`$ git checkout ca41886d`

This will warn you that "You are in 'detached HEAD' state.".  This means your working copy is showing a state of the repository that is not the HEAD of any of your branches.  This is great for poking around in your git history, but you will eventually want to either check out one of your branches or you will want to create a _new_ branch with this commit as its head.

With your working copy in this 'detached HEAD' state, you will see the files exactly as they were when the commit was written to git.  In this example, planets.md will say there are eight planets. Open it up and check!

Note that the git history for this 'detached HEAD' state is the git history that you would have seen when this commit was written to git. Try running `git log` and see what it shows as the history.

When you're done exploring this feature, go back to the `master` branch by running

`$ git checkout master`

This will revert your working copy to the contents of the master branch. It will be like you never checked out the old commit.

## Step: Delete the redundant branches

Now, if you want, clean up your repository by deleting the redundant branches. If you want to get a copy of

`$ git branch -d planets-before-merge-conflict`  
`$ git branch -d branch-a`  
`$ git branch -d branch-b`  
`$ git branch -d branch-master`

## Step: Delete the remote branches

You've deleted the _local_ branches, but we pushed copies of those branches to github when you ran `git push --all`.  Deleting remote branches involves one of the strangest git commands. Git doesn't have a "delete remote branch" argument. Instead you have to "push" the instructions to delete the branch by putting a colon before the branch name. For example:

`$ git push :branch-a`

### What's up with the colon meaning "delete"?

This is really weird, but it's just how git works.  When you push a branch to a remote git repo, you can give it any name you want. For example, if you want to push branch-b to the remote repository called origin, you use the command:

`$ git push origin branch-b`

If you want to call the remote branch `thestuff` instead of `branch-b`, you would use the command

`$ git push origin branch-b:thestuff`

And so, _this is the weird part_, in order to delete a remote branch called  `branch-b` you need to use the command

`$ git push origin :branch-b`

This is basically telling git "push the _lack of a branch_ to the remote location called `branch-b`". Yeah. Weird.

# Next Steps

If you want to review an example of this repository with all of the branches you created in this lesson, Look at the branches in [https://github.com/CodeForPhilly/decentralized-data-examples](https://github.com/CodeForPhilly/decentralized-data-examples).
