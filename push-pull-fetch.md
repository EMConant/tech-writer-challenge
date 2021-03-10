## What is the difference between `git push`, `git pull`, and `git fetch`?

- `git push` - sends changes from a local branch to a remote repository
- `git pull` - gets changes from a remote branch, pulls them into your tracking branch, and merges them into a local branch
- `git fetch` - gets changes from a remote repository and pulls them into your tracking branch

`git push` takes your current branch and checks to see if there is a tracking branch for a remote repository connected to it. If so, it takes your changes from the branch and pushes them to the remote branch. This is how code is shared with a remote repository. You can think of it as "make the remote branch resemble your local branch". This will fail if the remote branch has diverged from your local branch: if not all the commits in the remote branch are in your local branch. When this happens, your local branch needs to be synchronized with the remote branch with `git pull` or `git fetch` and `git merge`. 

Often `git push` and `git pull` are described as equivalent. This isn't entirely correct, since under the hood `git pull` does two things. `git fetch` again takes your current branch and checks to see if there is a tracking branch. If so, it looks for changes in the remote branch and pulls them into the tracking branch. It does not change your local branch. To do that, you'll need to do `git merge origin/master` (for the "master" branch) to merge those changes into your branch - probably also called "master".

`git pull` simply does a `git fetch` followed immediately by `git merge`. This is often what we desire to do, but some people prefer to use `git fetch` followed by `git merge` to make sure they understand the changes they are merging into their branch before the merge happens.

