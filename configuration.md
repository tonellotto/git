# Git Configuration

Once you have Git installed on your system, you can configure your Git environment.
Usually, this is done once per computer, but you can change the configuration at any time.

The tool to use is `git config`, that you can use to set the Git configuration variables. These variables can be stored in three different files:

1. the `/etc/gitconfig` file: configuration for every user on the system and all their repositories;
2. the `~/.gitconfig` file: configuration specific to your user;
3. the configiguration file in a Git directory of a local repository `.git/config`: configuration for that single repository.

Each level overrides values in the previous level.

If you want to check your settings, at any time, use the following command.

```bash
$ git config --list
```

Now, we will see how to configure the most important Git values *at user level*.

## Identity

The following commands set up your identity and email address.

```bash
$ git config --global user.name "Nicola Tonellotto"
$ git config --global user.email nicola.tonellotto@gmail.com
```

## Message editor

The following command configures the default text editor that will be used when Git needs you to type in a message.

``` bash
$ git config --global core.editor nano
```

Valid alternative editors are `emacs` and `vi`.

## Credentials Caching

If you’re using an HTTPS URL to push over, the Git server will ask you for your username and password for authentication. By default it will prompt you on the terminal for this information so the server can tell if you are allowed to push.

If you do not want to type it every single time you push, you can set up a *credential cache*. The simplest is just to keep it in memory for a few minutes, which you can easily set up by running

```bash
git config --global credential.helper cache
```

The *credential cache* accepts the `--timeout <seconds>` option, which changes the amount of time the cache will store you credentials (the default is 900, i.e., 15 minutes).

## Ignoring files

Often, you will have a category of files that you do not want Git to automatically add or even show you as being untracked. These are generally automatically generated files such as log files or files produced by your build system, e.g., `.class` or `.pyc` files.
In such cases, you can create a file listing patterns to match them named `.gitignore`.

If you create a `~/.gitignore_global` file with some contents:

```
*~
.DS_Store
```

and you run:

```bash
git config --global core.excludesfile ~/.gitignore_global
```
Git will never again bother you about those files.
