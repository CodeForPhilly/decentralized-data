---
layout: lesson
title: Command-Line Skills - Stream Redirection and Piping
category: git-noms-data-models
tags:
---

## Prerequisites

Form a pair with another participant, and make sure that at least one of you is running a Mac.  (The instructions on this page are written for the Mac OS X command line; the commands are subtly different on Linux and Cygwin.)

## Goals (Learning Objectives)

After doing this tutorial you will know how to

- Use stream redirection to write files on the command line
- Use `cat` to read and write files on the command line
- Use pipes to connect different commands together

## Activities

Open up your command line.  Each activity below consists of sets of commands to execute on the command line, interspersed with questions and commentary to  discuss with your partner.

### Activity 1: Output redirection, `cat`, and writing files

To begin, let's do a refresher of some basic commands.  Execute all three of the following:

```bash
cd ~
pwd
ls
```

Discuss with your partner: what does each of these commands do?  Each name (`cd`, `pwd`, `ls`) stands for a longer name or phrase; what are they?

Now let's really get into it.

```bash
ls > file_list.txt
ls
```

Notice that there is now a new file in your homedir: `file_list.txt`.  Open this file in your text editor.  What's the text in it?  How did it get there?

The `>` operator is the shell *output redirection operator*.  It takes the output from a command, which would ordinarily be printed out on the screen, and instead writes it to a file.  This stream of output is called **"standard output"**, or "standard out" for short.

If you want to see the contents of a file without leaving the command line, you can use the `cat` command instead:

```bash
cat file_list.txt
```

When given the name of a file as an argument, `cat` reads the contents of that file, line by line, and prints each line to standard out.

What if we run `cat` with no arguments?

```bash
cat
```

Nothing happens!  Try typing in some text, perhaps...

```
You do not have to be good.
You do not have to walk on your knees
for a hundred miles through the desert repenting.
You only have to let the soft animal of your body
love what it loves.
```

What happens each time you hit Enter?  `cat` just parrots back to you what you typed in.

That's because, when you don't give `cat` a filename as an argument, it assumes the file will be given to it via **"standard input"**, which by default is read from the keyboard.  As `cat` receives each line of the "file" (that is, each line of standard input as you type it), it copies it to standard output.

To finish working with `cat` cleanly, we have to send the "end-of-file" signal.  Hit Enter so you're on a blank line, and then hold down the Control key (*not* Command!) and type D.  (This is usually abbreviated `^D` in written instructions.)  `^D` sends the end-of-file signal, which makes `cat` believe it's at the end of the file it's copying.  So, with its work concluded, it quits and now we're back on the command line.

Since `cat` copies its input (from standard in) to standard out, we can use output redirection to type a file directly on the command line!  Try this:

```bash
cat > poem.txt
```

Type in a couple lines of your favorite poem and then close out the file by sending an end-of-file signal (also known as an "EOF").

```bash
ls
cat poem.txt
```

What happened?  To recap, discuss:

- What are "standard out" and "standard in"?
- What does it mean to "redirect standard out"?  How do we do that on the command line?
- What is the basic functionality of the `cat` command?  How does its behavior differ when you give it a filename as an argument and when you give it no arguments?

### Activity 2: `history`, `grep`, and piping

Enter this command:

```bash
history
```

Discuss: what does the `history` command do?

What if we wanted to find all the `git` commands we'd entered in the past?  We could write the history to a file and then use `grep` to search through that file for lines that contain the text "git":

```bash
history > history.txt
grep git history.txt
```

Turns out, if you don't give `grep` a filename, it works similarly to `cat`: it reads its input from standard in instead of from a file.  Try it out:

```bash
grep git
```

Type in some lines of text







