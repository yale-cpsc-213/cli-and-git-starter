# The command line and git

## Summary

In this assignment you will complete a series of exercises that
expose you to common shell commands and git workflows. You'll
end up producing a git repository that you will push up to GitHub.
Along the way, you'll be able to run a program that does two things:
it generates data (mostly directories and files) upon which you'll
use shell commands and it tells you if you're successfully completing
the assignment. We'll use this same program to grade the assignment.
_We are guessing this assignment will take you about an hour._

## Getting started

First, you will need to clone the starter code. You might have done
that already, because that's where we're keeping this file.

Next, you'll need to download ...TOTO: COMPLETE!

Then, you'll want to produce the example data on which you'll work.
Run the code like the following

```
cli_exam build NETID DIRECTORY
```

For example if your net id is `kls233` and you want your test data in
`homework-data` you'd run

```
cli_exam kls233 homework-data
```

After running this, you'll notice there are bunch of subdirectories and
files inside of `homework-data`. IMPORTANTLY: do not put this directory
in the same directory as your answers---you should keep them separate.


## Exercises

For the sakes of brevity and clarity, we'll refer to your data directory
as `$DATA` and the directory with files you'll turn in as `$SUBMISSION`.
As you do analyses, you'll
be committing your work to your git repo and I'll tell you when you should
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
After you've done this, run `cli_exam test $NETID $SUBMISSION`
to see if you did it correctly. For example, imagine I might run the following

  ```
  cli_exam test kls233 /Users/kljensen/cli-and-git
  ```

  if my answers were sitting in a directory called `cli-and-git`.

2. **Produce a list of doctors at the movies**. Next, we will use
the `grep` command to get a list of doctors at the movies. If you
need help figuring out how to use `grep`, type `man grep` to see
the manual page. Use the karat `>` to redirect the output of your
`grep` command.

3. **Count the number of people going by "Mrs" at the movies**.
Some of the people at the movie go by "Mrs.". Use the `grep` and `wc`
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

## Others

* curl
* sha hash, md5
* merging
* git blame
