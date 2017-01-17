# The command line and git

## Summary

In this assignment you will complete a series of exercises that
expose you to common shell commands and git workflows. You'll
be manipulating files and directories and you'll
end up producing a git repository that you will push up to GitHub.
When we grade the assignment, we will clone your repo on GitHub
and run our grading program. That program is made available to
you while you do the homework, so you should be able to get
full credit on the assignment. This program does two things:
it grades the assignment and it also generates the data that
you need for the assignment.

_We are guessing this assignment will take you about two hours
if you are very new to the shell and git._

## Getting started

To begin, you will need to get an invitation to begin this
assignment from Kyle Jensen. (Though, if you're reading this,
you've likely already accepted that invitation!) Now that you've
accepted, we're going to walk you through how to complete the
assignment.

First, you'll need to me working on a unix-like machine with a
shell like bash. Your average mac will work, as will a Linux virtual
machine on [Cloud9](http://c9.io),
[DigitalOcean](http://digitalocean.com), AWS, Google Compute
Engine, whatever. You can also use the Zoo computing cluster
in the CS department. (Cloud9 is free, but asks for a credit
card. I will post a link that lets you skip this part on Canvas.
Also, you can find many free resources in the [GitHub
Student Development Pack](https://education.github.com/pack).)

First, you will need to clone the repository that was created
for you on GitHub when you accepted this assignment. That repo
is likely something akin to
`https://github.com/yale-cpsc-213/command-line-and-git-USERNAME`,
where USERNAME is your GitHub username. You'll need to use the
`git clone` command to clone the repo on whatever machine you're
using to complete your homework. You'll be adding files to this
repo and them pushing them back up to GitHub. That is how we'll
grade your assignment.

Next, you'll need to download the program we'll use for grading. You
can find that at the following URLs:
* for a mac: [https://goo.gl/UWEG93](https://goo.gl/UWEG93)
* for linux: [https://goo.gl/cu2Pcq](https://goo.gl/cu2Pcq)

You could download this in many ways. E.g. I used the following
on a linux machine:
```
curl -L -o cpsc213hw1 https://goo.gl/cu2Pcq
chmod a+x ./cpsc213hw1
```

Then, you'll want to produce the example data on which you'll work.
Run the code like the following

```
./cpsc213hw1 build NETID DIRECTORY
```

(You might not need the "./" depending on your `$PATH`, I'm including it
here for those of you blindly copying and pasting.)
For example if your net id is `kls233` and you want your test data in
`homework-data` you'd run

```
./cpsc213hw1 build kls233 homework-data
```

After running this, you'll notice there are bunch of subdirectories and
files inside of `homework-data`. It is important that you do not put this
directory in the same directory as your answers---you should keep them separate.


## Exercises

For the sakes of brevity and clarity, we'll refer to your data directory
as `$DATA` and the directory with files you'll turn in as `$SUBMISSION`.
The `$SUBMISSION` directory is your local copy of the git repo you cloned
from GitHub. It is what you will ultimately submit by pushing to GitHub.
As you do analyses, you'll
be committing your work to your local git repo and I'll tell you when
you should
do that. Of course, if you get an answer
wrong, you can always fix it---that is the beauty of git.

1. **Copy the list of movie goers**.
For the first few questions, we'll be analyzing the `movie-goers.txt`
file you'll find in your example data directory. This file contains a list of
people that attended the movies on a particular night. Please inspect the file
using the `less` command. (Are you having trouble quitting `less`? You should
be able to Google for how to do that.) To begin, use the
`mkdir` command to create a directory called `movies` inside of your `$SUBMISSION`
directory. Then, use the `cp` command to copy your `movie-goers.txt` file
into that directory. You should now have a a file at
`$SUBMISSION/movies/movie-goers.txt`.
After you've done this, run `./cpsc213hw1 test $NETID $SUBMISSION`
to see if you did it correctly. For example, imagine I might run the following

  ```
  ./cpsc213hw1 test kls233 /Users/kljensen/cli-and-git
  ```

  if my answers were sitting in a directory called `cli-and-git`.

2. **Produce a list of doctors at the movies**. Next, we will use
the `grep` command to get a list of doctors at the movies. If you
need help figuring out how to use `grep`, type `man grep` to see
the manual page. Use the karat `>` to redirect the output of your
`grep` command. Put the list of doctors in to a file called
`movies/doctors-at-the-movies.txt` in your `$SUBMISSION` directory.

3. **Count the number of people going by "Mrs" at the movies**.
Some of the people at the movie go by "Mrs.". (I generate these names
randomly. The library I used contains only "Mr/Mrs/Dr".)
Use the `grep` and `wc`
commands to count how many such people there are and put that number
into a file called `mrs-count.txt` in your `$SUBMISSION/movies` directory.
You will need to "pipe" these two commands together using the `|` character
is in your shell. If I found 15, the contents of the file would look like this

  ```
  15
  ```
That's it! (We'll ignore "whitespace" in your file: newlines, spaces, etc.)

4. **Sort non-doctor movie goers by last name alphabetically**.
Use the `sort` and `grep` commands to obtain a list of the movie
goers who are not doctors in alphabetical order. Put this list into
`$SUBMISSION/movies/sorted-non-doctors.txt`. (HINT: try the `-v` option
to `grep`.)

5. **Put your work under version control and tag it as v1.5**. You should now have
a `$SUBMISSION` directory that has the following contents

  ```
  $SUBMISSION/README.md
  $SUBMISSION/movies
  $SUBMISSION/movies/doctors-at-the-movies.txt
  $SUBMISSION/movies/movie-goers.txt
  $SUBMISSION/movies/mrs-count.txt
  $SUBMISSION/movies/sorted-non-doctors.txt
  ```
  It's time to start keeping your work under version control. You should
  change to your `$SUBMISSION` directory, which should already be a git
  repo (ie. it has a `.git` hidden directory in it---type `ls -la` to see
  all the directories, even the hidden ones). Then, add all your files in `movies` to the staging area (index),
  then commit them. When you commit them, you'll be prompted for a commit
  message. (If you're stuck in the editor making the message, you should
  figure out what editor it is and how to exit. Is it `nano`? Is it `vi`?
  Is it `emacs`?) Now, I'd like you to tag the current commit (which is
  passing the first four questions) as version "v1.5". You can use
  [git lightweight tags](https://git-scm.com/book/en/v2/Git-Basics-Tagging).

6. **Create some git branches**.
  Now we're going to create some git branches.
  The purpose of this exercise is to show you that you can have different
  work (files, versions of files, directories, whatever) in different branches
  and you can switch back and forth. To begin, I'd like you to use
  the `git branch` command to create a branch
  named "fubar" and to check it out with the `git checkout` command. You should then create a file in your `$SUBMISSION`
  directory called `situation.txt` and make the contents "fubar". Then
  commit that work. After you've committed that work, please make and
  checkout a new
  branch called "normal" and alter the contents of `situation.txt` such
  that the contents say "normal" instead of "fubar". Commit your work.
  _Now, check out your "master" branch again._

7. **Use git log to inspect the Elixir history**.
  [Elixir](http://elixir-lang.org/) is a new functional
  programming language build on [Erlang](https://www.erlang.org/)
  and I think it is _super cool_. I wish we could use it in this
  class, but JavaScript is likely more practical for you. I'd like
  you to clone the [Elixir git repo](https://github.com/elixir-lang/elixir)
  to your computer. Once you've cloned the repo, you should be able
  to use the `git log` command, `grep`, `cut` and
  `tail` to show me the first 50 commits that
  [José Valim](https://twitter.com/josevalim?lang=en) contributed
  to the Elixir project. (Hint, you'll want to [pretty format git](https://git-scm.com/docs/pretty-formats) so you can search
  the commit history easily.)

  I'd like you to put the 6-letter hashes of those commits into a
  file in your `$SUBMISSION` directory called `elixir-jose.txt`.
  It should have lines like the following:
  ```
  b8c8baa
  884d607
  a2b97b6
  7216233
  31b2a19
  dd293e6
  ```
  Add this file to your git repo and commit your work.

8. **Git blame people responsible for Hapi**. [Hapi](https://hapijs.com/)
  is a JavaScript web framework---it helps you write server-side web
  applications that listen for HTTP requests and give HTTP responses.
  It was created by Walmart to handle Black Friday traffic and people
  tend to have positive feelings about it. We're likely to use Hapi in
  this class.

  Like many open source projects, Hapi's source code is
  kept on GitHub. You can `git clone` it, make a branch, fix a bug and then
  send them a "pull request" to have your bugfix accepted into the code.
  Here is "diff" showing a change contributed by a user recently:
  [https://github.com/hapijs/hapi/commit/0cfb81](https://github.com/hapijs/hapi/commit/0cfb81). Notice that line 57 of the file `lib/handler.js`
  was changed: the original is on
  the left hand side of that page and the new line is on the right hand
  side. I'd like you to use the `git blame` command (or the GitHub website)
  to figure out who last edited line 57 of `lib/handler.js` before user [sirgallifrey](https://github.com/sirgallifrey) contributed this pull
  request. Once you've found that user's GitHub user name, please put it
  in a file called `hapi-57.txt` in your `$SUBMISSION` directory. For example
  if it was me, you'd put in there
  ```
  kljensen
  ```
  Add this file to your git repo and commit your work.

9. **Use CURL to download the Gettysburg Address** The program
  `curl` is installed
  on most unix-like machines. It is a useful HTTP client that you can use to
  interact with APIs, download files, and browse the web. I'd like you to use
  use `curl` to download the file [https://goo.gl/hFevV6](https://goo.gl/hFevV6) and place the contents into a file called
  `geezy-lincoln.txt` in your `$SUBMISSION` directory.
  You'll notice that I used a URL shortener. If you want `curl` to follow
  the redirect, you'll need to give it a special command line flag. You
  can give it a different flag to tell it to write its response content
  into your `geezy-lincoln.txt` file.

  Use the program `less`
  or `cat` to take a look at it. It is important that
  you download the contents directly and not alter them in any way, so you
  should be careful: don't copy and paste them. Now, we're going to compute
  the hash of that file's contents. First, let's make a copy of the file
  and put it at `geezy-lincoln2.txt`. Then, use the `echo` command to add
  a single "!" character at the of that file. You can do that like
  `echo -n "!" >>geezy-lincoln2.txt`, where we're using `>>`. You use
  `>` when you want to put the output of a command into a file. You use
  `>>` when you want to append to that file instead. Now, I'd like you to
  compute the [SHA-1](https://en.wikipedia.org/wiki/SHA-1) hashes of each
  file and put them into a file called `lincoln-hashes.txt`. You can use
  the command  `shasum` or `sha1sum` or `openssl sha1` to compute the sha-1
  hash of the file contents. You might want to use the `cut` command
  too. Your `lincoln-hashes.txt` file might look
  something like
  ```
  fe7baa1db1bef4a5334960e89641252b73513313
  d47b548c88536962387c2e2fa6b6da5ccf8a72aa
  ```
  Add this file to your git repo and commit your work.

  You should notice that the addition of a single "!" dramatically changes
  the contents of the hash. "Collisions", where two pieces of data have the
  same hash, are exceedingly rare. That's why git can use sha-1 hashes to
  uniquely identify files: it's a small string that conveniently summarizes
  even enormous bodies of text, code, data, a directory structure, etc.
  For most purposes, we can
  even get by using the first 6 characters of the hash. Of course, it is
  hard to remember hashes, which is why we great "branches" and "tags"
  in git--they're easier to remember!


## You're done!

Commit your work to your `master` branch. Then, push it up to GitHub.
Also, push up your `fubar` and `normal` branches so we can give you
credit for answering those questions!
