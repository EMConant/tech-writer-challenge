## What is the difference between `git push`, `git pull`, and `git fetch`?

- `git push` - sends changes from a local branch to a remote repository
- `git pull` - gets changes from a remote branch, pulls them into your tracking branch, and merges them into a local branch
- `git fetch` - gets changes from a remote repository and pulls them into your tracking branch

`git push` takes your current branch and checks to see if there is a tracking branch for a remote repository connected to it. If so, it takes your changes from the branch and pushes them to the remote branch. This is how code is shared with a remote repository. You can think of it as making the remote branch resemble your local branch.

_Note that a `git push` will fail if the remote branch has diverged from your local branch. This could happen if not all the commits in the remote branch are in your local branch. When this happens, your local branch needs to be synchronized with the remote branch with `git pull` or `git fetch` and `git merge`._

Often `git pull` and `git fetch` are described as equivalent. However, there is a notable difference: `git fetch` does one action while `git pull` does two. `git fetch` takes your current branch and checks to see if there is a tracking branch. If so, it looks for changes in the remote branch and pulls them into the tracking branch. It does not change your local branch. To do that, you'll need to do `git merge origin/master` (for the "master" branch) to merge those changes into your branch.

`git pull` simply does a `git fetch` followed immediately by `git merge`. If you'd prefer, however, you can use `git fetch` followed by `git merge` to make sure you understand the changes you are merging into your branch before the merge happens.

