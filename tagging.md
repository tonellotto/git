# Tagging

Git provides a couple of mechanisms for identifying changes by labels instead of by unique hash values.
The first is **branch**es. When we switch between two branches, we are using the descriptive label of the branch to identify a specific commit to switch to.
The second is **tag**s. A tag is like a branch, in that it identifies a specific commit with a descriptive label.
When we commit, we commit to a branch. The branch referenece will automatically be updated to point to that new commit; in other words, _branches are mutable references_.
A tag, on the other hand, is created to point to a specific commit and thereafter does not change, even if the branch moves on. In other words, _tags are immutable references_.

Git has two flavours of tags: **annotated** and **lightweight**. When using them, there is little difference between the two; both will allow you to refer to a specific commit in a **local repository**.

An annotated tag creates an additional tag object in the **local repository**, which allows you to store information associated with the tag itself. This may include release notes, the meta-information about the release, and optionally a signature to verify the authenticity of the commit to which it points.

## Creating tags

We can create a **lightweight tag**, pointing to the current commit, with:
```bash
$ git tag [tag label]
```
If we want to make it as an **annotated tag**, we need to supply `-a`, and a message with `-m`:

```bash
$ git tag -a [tag label] -m "[message]"
```

## Showing tags

To list the **local repository**'s tags, run:
```bash
$ git tag
```
For a pattern, use `-l` with `*` as a wildcard:
```bash
$ git tag -l *
```
In order to see what the tag contains, you can use:
```bash
$ git show
```
If the tag is an annotated tag, you'll see the message and the tag object, followed by the commit. If the tag is a lightweight tag, then you'll see only the commit object.

## Deleting tags

To get rid of tags, you can delete them with `-d`:
```bash
$ git tag -d [tag label]
```
Deleting tags is ok if you never made them publicly available, but you really should avoid deleting tags once you've pushed them to a publicly readable **upstream repository**. Similarly, you shouldn't change a tag once it has been released to the wild either.

## Pushing and pulling tags

Since a tag (either annotated or lightweight) is just a reference on your **local repository**, it is not sent up by default to the **upstream repository** repository during pushes. Instead, you can push the tag individually:
```bash
$ git push [tag label]
```
or you can run:
```bash
git push --tags
```
which will push all tags.

For pulling, any tags associated with your current branch will be fetched when you check it out. This may result in not having all the tags in your **local repository** that the **upstream repository** has. If you'd like to fetch them all, you can do:
```bash
git fetch --tags
```
to pull them all in, or:
```bash
git fetch [tag label]
```
to pull a single one.