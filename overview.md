# Git Overview

## What is Git?

Git is a piece of software that helps organize and track changes to files over time (usually text based files, like code), and helps multiple users work on the same projects, without stepping on each others' toes. Git is run from the command line, usually by running `git`, followed by another key word, then often followed by various options.

## What is Github?

[Github](https://github.com) is a website that provides a visual interface for Git, as well as hosting the files that make up a project. One version of these files is hosted on [Github](https://github.com) servers (called the *remote version*), but in almost every case there are many other versions on various other computers (called *clones*). For example, on my computer at work I have a version of these files, and another version on my computer at home. As we work on the files, at various times we will sync them up with the remote version that is on [Github](https://github.com), by pushing the changes we make to [Github](https://github.com) and pulling down the changes other users make to the remote version.

Many open-source software projects are hosted on [Github](https://github.com) (or [Bitbucket](https:bitbucket.org), [GitLab](https://gitlab.com) and other Git hosting services).
Most software developers write their code using `git`, sometimes in public, sometimes in private (charging for private hosting is one way [Github](https://github.com) makes money). The more you work with Git, the more invaluable it will become to you.

## Overview

Here, I'll just give a quick overview of the fundamental Git workflow. Let's say you're working on some files, on your local clone, and want to sync up with the remote version on [Github](https://github.com):

### git add

Flag certain file(s) as ready to be synced.

### git commit

Lump all your changes together, and write a message describing the changes.

### git pull

Retreive changes other users have sent to the remote repository.

### git push

Send your changes to the remote repository.