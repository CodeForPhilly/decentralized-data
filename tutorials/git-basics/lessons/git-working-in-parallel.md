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

### Activity 1: Find a Partner

This lesson is designed to be done in pairs so that you can see what happens when two people work on the same git repository at the same time.  Find a partner to work with. You don't have to be in the same place&nbsp;--- for example you could coordinate your work with a friend over IRC or Slack.

In these instructions, we will call the two partners **Alex** and **Jamie**; decide which one of you will play each role.

### Activity 2: Submit and Review a Pull Request

**This activity is done entirely on Github, not on the command line.**

1. **Together:** Pick a repository owned by Jamie.  This is the repository (a.k.a. "repo" or "project") that Alex will also contribute to.
2. **Alex:** Go to the Github page for Jamie's repo.  In the upper-right corner, click the "Fork" button.  This will create a duplicate copy of Jamie's repo that you (Alex) now own.
3. **Alex:** Look at the main Github page for your new repo.  Notice that underneath the repo name it says something like "forked from Jamie/repo-name".  Github keeps track of which original project you forked from.
4. **Jamie:** Refresh the main Github page for your repository.  Notice that there _isn't_ any message beneath the repository title about Alex forking your repo.  Alex's fork doesn't affect you yet, so there's no reason for Github to tell you about it.
5. **Alex:** Make some changes to a file in your forked repo, and then commit your changes.
6. **Jamie:** Make changes in a _different file_ within your own repo, and then commit your changes.
7. **Alex:** Go back to your repo's main Github page and create a pull request with your committed changes.  Submit the pull request.
8. **Jamie:** Wait a moment and refresh your repo's main page; you should get a notification about the pull request.  Open it up, write a comment on it, and then merge the pull request.
9. **Together:** On your separate computers, go back to the main Github page for your respective projects.  Click on the "Graphs" tab along the top, and then click on "Network".  Hover your mouse over the dots in the diagram to see what they show.  Are your diagrams the same or different?  Discuss with your partner to figure out how the diagram relates to the actions you took above.

### Activity 3: Cause a Merge Conflict and Resolve it

**This activity is done on Github and also on the command line.**  Each instruction is labeled either _[Github]_ for those that should be done on the Github website, or _[Shell]_ for those that should be done on the command line or using your text editor.

1. **Together:** _[Github]_ Pick a repo owned by Alex.  This is the repo that Jamie will also contribute to.
2. **Jamie:** _[Github]_ Fork Alex's repo.
3. **Jamie:** _[Shell]_ Clone your new forked repo to your local machine.
4. **Alex:** _[Github]_ Pick a relatively long line in an existing file in this repository.  Make a small change in that line, and commit your change.
5. **Jamie:** _[Shell]_ Use your text editor to open your copy of the file that Alex just changed.  Notice that you see the original version of this file, since Alex only changed it in their repo.
6. **Jamie:** _[Shell]_ Make a _different_ edit to the same line that Alex changed, and save the file.
7. **Jamie:** _[Shell]_ Stage your change (with `git add`), commit it, and then push it to your Github repository.
8. **Jamie:** _[Github]_ Refresh the main page for your forked repository.  You should see a message above the list of files saying something like "This branch is 1 commit ahead, 1 commit behind Alex:master".  What does that mean?
    * Your repo is 1 commit ahead of Alex's because you have committed a change to your repo since forking.
    * Your repo is also 1 commit behind Alex's because Alex has committed a change since the last time you got information from their repo.
    * This is Jamie's first indication that a pull request would be a bad idea right now.  Before sending your work back to a "project owner", you should make sure that you're up-to-date with whatever they've done recently.  We'll get to that in a moment.
9. **Jamie:** _[Github]_ Click the "New pull request" button.  You should see a message on the next page that says "Can't automatically merge".
    * Git doesn't know how to automatically merge your changes into Alex's repo because they happened on the same line.  So it's going to be somebody's responsibility to merge the changes manually.
    * Since Alex owns the repo that Jamie forked, it's _Jamie's_ responsibility (as the forker) to merge Alex's recent changes into their own.
10. **Jamie:** _[Github]_ Click the back button on your browser to abandon the pull request.
11. **Jamie:** _[Shell]_ Enter the following command, replacing stuff in angle brackets with the appropriate names:
    
    ~~~
    git pull https://github.com/<ALEX'S USER NAME>/<REPO NAME>.git
    ~~~
    
    You should get the following warning:
    
    ~~~
    CONFLICT (content): Merge conflict in <CONFLICTED FILE>
    Automatic merge failed; fix conflicts and then commit the result.
    ~~~

12. **Jamie:** _[Shell]_ Open the conflicted file in your text editor.  Two copies of the conflicting line should be shown, surrounded by `<<<<` and `>>>>`.  Your version comes first, followed by Alex's version.  It should look something like this:
    
    ~~~
    <<<<<<< HEAD
    **City:** Philadelphia
    =======
    **Current City:** Philly
    >>>>>>> 8907ab85c55e86a151ac1c584fb7251783f81289
    ~~~
    
13. **Jamie:** _[Shell]_ Edit the file in your text editor to remove the conflict.  Make sure you get rid of all the extra `<<<`/`===`/`>>>` cruft.  Save the file.
14. **Jamie:** _[Shell]_ Stage and commit your new edits.  The commit message will default to saying that you merged with Alex's repo; leave the message as is.
15. **Jamie:** _[Github]_ Refresh your project's main page again.  You should now see, above the file list, a message saying that "This branch is 2 commits ahed of Alex:master".
16. **Jamie:** _[Github]_ Click the "New pull request" button and note that Github now says that git is "Able to merge".  Click "Create pull request" and fill out the description of your request.
17. **Alex:** _[Github]_ Refresh your project's main page.  You should now see Jamie's pull request.  Open it up, take a look at the changes on the "Files Changed" tab, and comment and merge in the pull request on the "Conversation" tab.  Now you have Jamie's changes as well as your own!
18. **Together:** _[Github]_ As in the last activity, open up the main Github page of your respective projects.  Click on "Graphs" and then "Networks", and examine and discuss the diagrams you see.

## Review

Notice that each partner only ever made changes in their own repository.  Anyone can fork anybody else's repository on Github, resulting in a new forked copy that they own.  This way, everyone's free to make the changes they want without disrupting anyone else's work.

Take a minute with your partner to contemplate the similarities and differences between branches and forks.

* Can multiple branches exist in a repository that is a fork of some other repository?
* Can a pull request be made from _any_ branch of _any_ repository to _any other_ branch of the repository from which it was forked?

## Next Steps

None!  This is the last lesson of this workshop.  If you have any lingering questions about Git, make sure to ask them in the workshop or on Slack.
