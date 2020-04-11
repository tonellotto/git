### Branch

![](https://github.com/tonellotto/git-and-github/raw/2acad870b0ac4692760545a7935b76e67d92f04b/git_commands/git_branch.png)

Branches can also be created manually, and they are a useful way of organizing unfinished changes.

The branch command has two forms. The first:

```bash
$ git branch
```

simply lists all of the branches in your **local repository**. If you run it without having created any branches, it will list only one, called `master`. This is the default branch.

The other form creates a branch with a given name:

```bash
$ git branch new-branch
```

It's important to note that the other branch is not *active*. If you make changes, they will still apply to the `master` branch, not `new-branch`. To change this, you need the next command.

### Checkout

![](https://github.com/tonellotto/git-and-github/raw/2acad870b0ac4692760545a7935b76e67d92f04b/git_commands/git_checkout.png)

Checkout switches the active branch. Since branches can have different changes, checkout may make the **working directory** look very different. For instance, if you have added new files to one branch, and then check another branch out, those files will no longer show up in the **working directory**. They are still stored in the `.git` folder, but since they only exist in the other branch, they cannot be accessed until you check out the original branch.

Example:
```bash
$ git checkout new-branch
```