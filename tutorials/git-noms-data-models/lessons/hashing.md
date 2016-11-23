---
layout: lesson
title: Theoretical Background - Hashing
category: git-noms-data-models
tags:
---

## Prerequisites

Form a pair with another participant, and make sure that at least one of you is running Linux or Mac OS X.  You should already know how to use [redirection and piping on the command line](../redirection-and-piping).

## Goals (Learning Objectives)

After doing this tutorial you will know:

- What hashing means
- What features a hash function usually has
- A couple purposes for which hashing is used
- The names of a couple widely-used cryptographic hash functions

## Activities

Open up your command line.  Each activity below consists of sets of commands to execute on the command line, interspersed with questions and commentary to  discuss with your partner.

### Activity 1: Deterministic

First, let's create a simple text file:

```bash
cat > test.txt
```

Now enter the following text and end with a blank line and an EOF (end-of-file signal; `^D`).  Pay careful attention to the capitalization, spacing, and punctuation!

```
One fish, two fish
Red fish, blue fish
```

We can get a computational fingerprint for this file, called a "hash", by using the `md5` command.  (It may be called `md5sum` on your computer.)

```bash
md5 test.txt
```

On my computer, this command prints out:

```
MD5 (test.txt) = ab07f7960958aa4bf2ec2409089e9e13
```

On your computer, the output may be formatted a little differently, but the *hash*, the `ab07f...` stuff, should be exactly the same.  A "hash" is a value computed by a *hash function*, and this page is all about learning the characteristics of hash functions.  A hash function takes arbitrary data as input, and computes a hash as its output:

```
f : data -> hash
```

Many different hash functions have been invented; the `md5` program runs a hash function called "MD5".  Every hash function is *deterministic*: given the same input, it will always compute the same result (the hash), no matter who runs it, when, on what computer.  (Or even if they compute it by hand!)  Even though the hash looks totally random, I know that your computer will produce the same one that I did for the same input file, because we were both running the same hash function: MD5.  This is the first feature of a hash function:

> A hash function is **deterministic**: the same input always produces the same output.


### Activity 2: Fixed-Size Output

Let's create a bigger file to work with:

```bash
cat test.txt test.txt test.txt test.txt > bigtest.txt
cat bigtest.txt
```

The first `cat` command reads through `test.txt` four times (because we gave it as an input file four times), and copies all of that to stdout (which then gets redirected to the file `bigtest.txt`).  That explains the name "cat": it's a tool for *conCATenating* its inputs.

And what's the MD5 hash of this larger file?

```bash
md5 bigtest.txt
```

My computer tells me that it's `2fe019adee117ef8e19dcc3bb9606ff8`.  Notice that the hash is the same length as the hash for `test.txt`, even though the file is four times as big.

What about a tiny file?  Use `cat` to enter just the single line `hello` into a file called `tiny.txt`.  (Remember that you should only type `^D` on an empty line to close out `cat`.)  Then get the MD5 hash of it.  You should get `b1946ac92492d2347c6235b4d2611184`.  Once again, the hash is the same length as the others, even though the file is just a few characters long.

This tells us the second feature of a hash function:

> A hash function produces **fixed-size output**, no matter how big or small its input is.


### Activity 3: Unique*, Chaotic, and One-Way

Create another example file called `tiny2.txt` with the contents `hell0`.  (Note the zero in place of the "o".)  Get the MD5 hash of this new file; you should get `cd6fcbf38d05a09309006387f0446665`.  Notice that this hash is *completely different* from the one for `tiny.txt`, even though the files are the same size and differ by only a single character.  This is the third feature of a hash function:

> Given two **different inputs**, a hash function will always* produce two **different outputs**.

Notice the asterisk in there; this statement isn't *exactly* true.  In fact, it *can't* be exactly true!  Discuss with your partner: how can we know *for sure* that it's impossible for a hash function to always produce different outputs for any pair of different inputs?  (Hint: think about the second feature described above.  How many different possible hashes are there?  How many different possible inputs are there?)

The situation when a hash function produces the same hash for two different inputs is called a **hash collision**.  To the greatest extent possible, people who design hash functions want to avoid collisions, but it's impossible to guarantee that they will never happen.

One way to try to avoid hash collisions is to make hash functions very sensitive to their inputs: a tiny change in input produces a huge change in output.  That's what we saw when comparing the hashes of `tiny.txt` and `tiny2.txt`: changing one character gave us a totally different hash.  This is one aspect of the formal, mathematical definition of *chaos*.

> A hash function is **chaotic**: tiny changes in input produce huge, random-looking changes in output.

This means that the hashes of two very similar-looking files will probably be completely different.

From a mathematical perspective, a hash function is just like any other function: given an input, it has a particular output value.

```
f : data -> hash
```

A well-designed hash function is easy to compute: it takes very little time (on a computer, anyway) to compute the hash for a given input.  However, given how random-looking the hashes are, and how their size has no relation to the size of the corresponding input, a hash function is very hard to "run in reverse": given a hash, it takes a long time (and generally a lot of guess-and-check) to figure out what input produced it.  (A *cryptographic hash function* is one that has been *mathematically proven* to be "hard to run in reverse", for a precise meaning of the word "hard".)

> A hash function is a **one-way function**: it's easy to compute the hash of an input, but very hard to figure out the input given just its hash.


### Application 1: Do We Have the Same File?

Let's recap the features of hash functions:

1. They're deterministic
2. They produce fixed-size output, regardless of input size
3. They *almost* always produce different outputs given different inputs
4. They're chaotic
5. They're one-way

This combination of features makes hash functions (and the hashes that they compute) very useful for a variety of purposes.  The hash of a file acts as a "fingerprint" for it: a compact and (almost surely) unique identifier.  So hashes are very good for determining whether two files are the same.

Say Alice and Bob live in different countries, and they each have a 36-gigabyte file called "dump.txt", but they're not certain that their copies are identical.  They could check by having Bob send his copy to Alice, and then Alice could use a program to go through the two copies line-by-line, comparing as it goes.  But that would take a long time, and it would also involve transmitting 36 gigs over the internet just to get a simple yes-or-no answer.

Instead, Alice and Bob could each compute the MD5 hash of the files that they have, and then Bob could send Alice his hash.  Bob has to transmit only a tiny bit of information now (because of feature 2: though the input is huge, the hash is small).  Alice can very quickly compare Bob's hash to her own, and if they differ, then she knows that Bob's copy of the file *must* be different from hers (because of feature 1: hash functions are deterministic).  If the hashes are the same, then Alice can be *almost certain* that Bob's file is the same as hers (because of feature 3: hash collisions are rare).

Sending a hash rather than the whole file provides an additional benefit to Bob: if his file turns out to be different from Alice's, she won't know *in what way* it's different, only *that* it's different.  And furthermore, nobody eavesdropping on their communications will know anything about the file: not its content, and not even its size.  (These benefits arise from features 2, 4, and 5.)


### Activity 4: Hashing Things Other Than Files

Hashing is a process that applies to arbitrary data, not just files --- anything made of bits can be hashed.  Let's investigate that.  Enter this command in your shell:

```bash
md5
```

Just like `cat` and `grep` and `less`, if you don't provide a filename to `md5`, it reads its input from standard-in, which by default is just the keyboard.  Type in `hello`, then press enter, and lastly send an EOF.  What do you get?  Compare the hash to the hash of `tiny.txt` above.

We can also use `cat` and piping to send the *contents* of a file, rather than the file itself, into `md5`:

```bash
cat bigtest.txt | md5
```

Again, how does this compare to the result of just running `md5 bigtest.txt`?  Hopefully what you've found is that the hash that results in both cases is the same.  This tells us a feature, not of hashing *functions*, but of how they're used in practice:

> The hash of a file is just the hash of the **contents** of that file.

So, in the application example above, Alice's and Bob's files need not have the same name: if their contents are the same, the hashes of the files will be the same.


### Application 2: Passwords

How does a website's server verify your identity when you log into the site?  You type in a username and password on your computer, and somehow the server needs to answer the question: did you give the correct password for that username?  Here's one way for it to answer that question: it keeps a big table of usernames and passwords, and when you log in you send it your username and password.  It looks up the username that you gave it in its big table, and if the password you sent matches the one they have on file, you're all set.

There are two big problems with this approach, though.  For one, anybody could intercept the data that you send to the server, and thereby read your password.  Also, security breaches of website servers are very common; if the server stored a big username--password table, then a hacker who broke into the server could get *everybody's* passwords all at once.

Here's a better approach: the server stores a big table of usernames and the *hashes* of corresponding passwords, but not the actual passwords themselves.  Then, when you log in, you compute the hash of your password on your own machine, and send your username and password-hash to the server.  The server looks up your username in the big table, and if the hashes match, they can be *almost certain* that you typed in the correct password.  And that's basically how password-checking really works, both over the web and for logging into your own computer.


### Application 3: Hash Tables and Content Addressing

Here's a pretty common problem in computing and life in general: putting something in a place so you know you can find it later.  There are two prominent situations in which we encounter this problem in computing: retrieving data from the Internet, and retrieving data from computer memory.

You may have heard of *IP addresses*: they're unique numerical addresses for servers on the Internet.  For example, as of the writing of this document, the Github server serving this webpage had the IP address `151.101.40.133`.  An IP address is just a fixed spot for finding some information.  (Fortunately, we have the Domain Name System, DNS, so that your browser can automatically convert from a URL that you type in to the less user-friendly IP address.)

There are also *memory addresses* for the memory in your computer.  When a program is running, the value of every piece of data is located somewhere in memory.  Each location in memory has an associated address; you may have encountered them written as something like `0x7fff5eea27d8`.  If I want a piece of data, I need to know the address at which to find it.  (Fortunately, most programming languages have *variables*, and behind the scenes, the compiler generates a *symbol table* that the compiled program can use to translate between variables and memory addresses.  So the programmer generally doesn't need to type memory addresses in manually, just as you probably rarely enter IP addresses into your browser.)

Both IP addresses and memory addresses are just numbers --- even though, when written out, they look disguised with dots and "0x" and letters like "f".  And hashes, too, are just numbers (though they're similarly disguised when written out).  So what if, rather than maintaining big tables to associate URLs with IP addresses, or variable names with memory addresses, we could come up with addresses by *hashing*?  This is the essence of **content addressing**: the place where you put a piece of information is determined by the hash of that information itself.  Content addressing has a variety of advantages that we'll discuss later, but for now this is just a preview of the idea.


## Next Steps

Proceed to the [Git Hash Objects lesson](../hash-objects).
