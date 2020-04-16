# Branching

When you make a commit, Git stores a commit object in your **local repository**. This commit object points to the snapshot of the current content in your **staging area**.

A *branch* in Git is simply a pointer to one of these commit objects. When you initialize a **local repository** with the Git `init` , a default branch is created with the name `master`. Every time you commit, the `master` branch moves forward automatically.
The `master` branch in Git is not a special branch. It is exactly like any other branch.

## Create branches

To create a new branch in your **local repository** with a given name use the `branch` command:

```bash
$ git branch [new-branch]
```

It is important to note that the `new-branch` branch is not *active*. If you make changes, they will still apply to the `master` branch, not the `new-branch` branch. To change this, you need the next command.

## Checkout branches

Checkout switches the active branch. Since branches can have different changes, checkout may make the **working directory** look very different. For instance, if you have added new files to one branch, and then check another branch out, those files will no longer show up in the **working directory**. They are still stored in the `.git` folder, but since they only exist in the other branch, they cannot be accessed until you check out the original branch.

To switch to an existing branch, you run the checkout command.

```bash
$ git checkout new-branch
```
This means the changes you make from this point forward on the `new-branch` branch will diverge from other branches' versions of the project, in particular the `master`branch.

To create a branch and switch to it at the same time, you can run the checkout command with the `-b` switch:

```bash
$ git checkout -b new-branch
```

This is a shorthand for:
```bash
$ git branch new-branch
$ git checkout new-branch
```
![](https://github.com/tonellotto/git-and-github/raw/2acad870b0ac4692760545a7935b76e67d92f04b/git_commands/git_checkout.png)


## Showing branches

The `branch` command has two forms. The first:

```bash
$ git branch
```

simply lists all of the branches in your **local repository**. If you run it without having created any branches, it will list only one, called `master`.
The `*` character that prefixes the master branch indicates the branch that you currently are working on. This means that if you commit at this point, the master branch will be moved forward with your new work. To see the last commit on each branch, you can run

```bash
git branch -v
```


## Pushing branches

When you want to share a branch with the world, you need to push it up to a **upstream repository** that you have write access to. Your local branches aren’t automatically synchronized to the **upstream repository** you write to -– you have to explicitly push the branches you want to share. That way, you can use private branches for work you don’t want to share, and push up only the topic branches you want to collaborate on.
If you have a branch named `serverfix` that you want to work on with others, you can push it up the same way you pushed your first branch. Run `git push (remote) (branch)`:

```bash
 $ git push origin serverfix
 ```

 ## Fetching branches

 It’s important to note that when you do a fetch that brings down new remote branches, you don’t automatically have local, editable copies of them. In other words, in this case, you don’t have a new `serverfix` branch – you only have an `origin/serverfix` pointer that you can’t modify.

 If you want your own `serverfix` branch that you can work on, you can base it off your remote branch:
```bash
$ git checkout -b serverfix origin/serverfix
```

This gives you a local branch that you can work on that starts where `origin/serverfix` is.