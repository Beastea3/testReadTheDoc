# Git better practices for teams

## Formalize Git conventions for your team

- Use aliases to formalize team members’ actions;
- Build a standard for git committing/branching/tagging.

## Rebase & Merge

### Rebase your feature branch often;
```bash
git checkout master
git pull
git checkout feature-new  # name of your hypothetical feature branch
git rebase master  # may need to fix merge conflicts in feature-new
```
After the commands above, your branch should not have any conflicts against `master`. Then you can create a PR to merge your code to `master`;

```bash
git checkout feature
git pull
git merge feature-new
```
The commands above are aimed to merge your feature branch to a `feature` branch, which is integrated with many features including other colleagues' code.

### The difference between `merge` and `rebase` is critical:
 - `merge` has a non-linear history, and will generate "Merge Commit" to make the git history difficult to follow and read;
 - `rebase` will hand on all commits of this branch to the `master`, and will have a cleaner project history. However, `rebase` will be tricky because it will rewrite the history and will be tougher to resolve conflicts;

### To Rebase or To Merge?

If you are working on a local and individual branch which no one else is looking at or using your branch to base their works, it will be best to rebase your branch; Otherwise, it will be dangerous because `rebase` will rewrite the commit history. Moreover, rebasing as frequently as you are committing will be a good solution for complicated rebases;

`git merge --squash` is also a good choice to merge feature branch, it will squash all your commits into one commit to make the merge meaningful and consolidated. What's more, `--squash` can also give you an opportunity to select which files you want to merge.

### git pull

`git pull` runs `git fetch` and `git merge`, but if followed by a `--rebase`, it will run `git rebase` instead of `git merge`;

## Bug Fixing

### git bisect

It is very annoying to find when the code was broken. Now the code is not working, and you know that at commit `b18271663a8117`, the code works well. `git bisect` can accelerate your progress to reach the incorrect point. The workflow is sampled below:

```
$ git bisect start
$ git bisect bad                 # Current version is bad
$ git bisect good v2.6.13-rc2    # v2.6.13-rc2 is known to be good

Bisecting: 675 revisions left to test after this (roughly 10 steps)  # Output
$ git bisect good # If this commit is good;
$ git bisect bad # If this commit is broken;

Bisecting: 337 revisions left to test after this (roughly 9 steps) # Output

$ git bisect reset # go back to HEAD
```

`git bisect` uses a binary search to locate the point at which the code is broken;

## Branching Strategy

Agile recommends three branches strategy:
  - Release
  - Feature
  - Task

Since Agile is user story centered, every task including bug-fix or feature should have its branch, which is named by the story id;

### Branching's evil twin

Short-lived branches make it easier to merge branches. because with short-lived branches simply contain fewer changes. Under this strategy, "merge hell" will not affect our development;


## *References*:

1. [*Atlassian Agile Coach*](https://www.atlassian.com/agile/software-development/branching)
2. [*Git Documentation - bisect*](https://git-scm.com/docs/git-bisect)
3. [*5 advanced Git commands to up your Git game*](https://www.infoworld.com/article/3561098/5-advanced-git-commands-to-up-your-git-game.html#:~:text=The%20git%20rebase%20command%20also,commit%20history%20for%20that%20branch.)
4. [*Git Workflow - Merge vs. Rebase*](https://frontend.turing.io/lessons/module-2/merge-vs-rebase.html?ads_cmpid=6451354298&ads_adid=76255849919&ads_matchtype=b&ads_network=g&ads_creative=378042327747&utm_term=&ads_targetid=dsa-416714872696&utm_campaign=&utm_source=adwords&utm_medium=ppc&ttv=2&gclid=Cj0KCQiA7qP9BRCLARIsABDaZzg0X4MRpZbVzQed0EifMB8V9hdmcxS9ZpNBXfKhYFwJECNJMTbjb30aAgv5EALw_wcB)
5. [*6 best practices for teams using Git*](https://opensource.com/article/20/7/git-best-practices)
