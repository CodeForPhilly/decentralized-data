---
layout: lesson
title: Go Introductory Tutorials
category: get-started-with-golang
tags:
---

*If you encounter anything confusing or incomplete in these instructions, please mention it in our Slack channel and/or [write an issue about it in our issue tracker](https://github.com/CodeForPhilly/decentralized-data/issues).*

## Goals (Learning Objectives)

To learn the Go programming language well enough that you can read code written in it and create some small programs on your own.

## Activities

Your objective by the end of this lesson is to complete the following five tasks.  We recommend that you first take a [guided tour of Go](https://tour.golang.org), but if you'd like you can just dive right into writing the following programs while referring to the [Go language reference](https://golang.org/doc/effective_go.html).

1. **Write a "Hello, World" program.**  Write a program that you run from the command line whose only behavior is to print out `Hello, World` and then exit.  Call your source-code file `hello.go` so that the resulting program file is called `hello`.

2. **Write a word-count program.**  Write a program that takes a filename as a command-line argument and prints out the number of characters, words, and lines in the file.
    
    A command-line argument is a string written after the name of a program when you run it from the command line.  For example, the following command is how you change from your current directory into the directory `foo` on the command line:
    
    ```
$ cd foo
```
    
    In this case, `foo` is a command-line argument.
    
    Go, like most other programming languages, has a way for you to get the values of any command-line arguments within the logic of your program.  You'll have to look around a little to figure out how to do that.

3. **Write a typing-speed program.**  Write a program that prints out a block of text, then waits for the user to type that text back in.  Once the user hits the Enter key, your program should compute their typing accuracy and report the number of words per minute that they typed.
    
    Once you've got that functionality working, upgrade your program so that it runs in a loop: after each typing test, prompt the user to either continue or quit.  Give them another, harder test if they ask to continue.

4. **Write a web application.**  Follow the instructions on the [golang.org Writing Web Applications tutorial](https://golang.org/doc/articles/wiki/).

5. **Write a program of your own.**  Think of a small program that you'd like to write, and write it!  The emphasis here is on *small*; it's better to choose something simple and acheivable than to bite off more than you can chew.
    
    You could write a game with a text-based interface and a turn-based mechanic (like tic-tac-toe or mastermind), a web-based chat bot, a web scraper, a small database application, a simple blog engine, etc.  We recommend against trying to write things with graphics, animation, or real-time feedback, as these can get complicated fast.

## Links

* [The official Go tour](https://tour.golang.org)
* [The "Effective Go" language reference](https://golang.org/doc/effective_go.html)
* [More official tutorials and resources at golang.org](https://golang.org/doc)
* [Community-created resources on the Go wiki](https://github.com/golang/go/wiki/Learn)
* [Another large, standalone intro to Go](http://www.golangbootcamp.com/book/intro)

