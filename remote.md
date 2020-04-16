# Working with Upstream Repositories

To be able to collaborate on any Git project, you need to know how to manage your **upstream repositories**. **Upstream repositories** are versions of your project that are hosted on the Internet or network somewhere.

## Showing Your Upstream Repositories

To see which **upstream repository** you have configured, you can run the `remote` command. It lists the shortnames of each **upstream repository** you’ve specified. If you have cloned your repository, you should at least see the `origin` string –- that is the default shortname Git gives to the **upstream repository** you cloned from. If you have more than one **upstream repository**, the command lists them all. The `-v` option shows you the URLs that Git has stored for the shortname to be used when reading and writing to that **upstream repository**.

```bash
$ git remote -v
```

## Adding Upstream Repositories

To add a new **upstream repository** as a shortname you can reference easily, run the following.

```bash
$ git remote add github https://github.com/tonellotto/cloud-computing
```

From now on, you can use the shortname `github` on the command line in lieu of the whole URL `https://github.com/tonellotto/cloud-computing`.

## Fetching and Pulling from Upstream Repositories

To get data from a specific **upstream repository**, you can run:

```bash
$ git fetch github
```

If you clone a **upstream repository**, the command automatically adds that **upstream repository** under the shortname `origin`. So, the `fetch` command fetches any new work that has been pushed to that **upstream repository**. It is important to note that the `fetch` command pulls the data to your **local repository** -– it does not automatically merge it with any of your work or modify what you are currently working on in your **working directory**. You have to merge it manually into your work when you are ready.

Running the `pull` command generally fetches data from the **upstream repository** you originally cloned from and automatically tries to merge it into the code in your **working directory**.

## Pushing to Upstream Repositories

When you have your **working directory** at a point that you want to share, you have to push it to a **upstream repository**.

If you want to push your `master` branch (more info on branches [here](./branches.md)) to your `origin` **upstream repository** (cloning generally sets up both of those names for you automatically), then you can run the following.

```bash
$ git push origin master
```

The `push` command works only if you cloned from a **upstream repository** to which you have write access and if nobody has pushed in the meantime. If you and someone else clone at the same time and they push upstream and then you push upstream, your push will rightly be rejected. You have to pull down their work first and merge it into yours before you’ll be allowed to push.

## Inspecting a Upstream Repository

If you want to see more information about a particular **upstream repository**, you can use the following.

```bash
git remote show github
```

It lists the URL for the **upstream repository** as well as other information.

## Removing and Renaming Upstream Repositories

You can run the following command to change a **upstream repository**'s shortname.

```bash
$ git remote rename github git_hub
```

If you want to remove a  **upstream repository** for some reason –- you moved the server or are no longer using a particular mirror -– you can use the following command.

```bash
git remote rm git_hub
```

## Remote Push to Multiple URLs

To set up the push URLs do this:
```bash
$ git remote set-url --add --push origin https://github.com/tonellotto/cloud-computing
$ git remote set-url --add --push origin https://github.com/foobar/cloud-computing
```
Now pushes with the `push` command will send to both of these destinations, rather than the fetch URL. Check it out by running the following

```bash
$ git remote show origin
```