---
title: Remove Sensitive Data from GitHub
date: 2025-03-10
categories: [How-to, GitHub]
tags: [github, git, bfg, security, sensitive-data]     # TAG names should always be lowercase
---

# Remove Sensitive Data from GitHub

In this tutorial we are going to be using nix-shell so we do not have to install any dependencies on our machines.

1. Run the below command to start a nix-shell with the needed tools.

```shell
nix-shell -p openjdk17-bootstrap git bfg-repo-cleaner
```

2. Once inside the nix-shell clone the repo with the `--mirror` command.

```shell
git clone --mirror https://github.com/org/reponame.git
```

3. Create a passwords.txt file containing all sensitive data that needs to be removed from the repository.

```shell
nano passwords.txt
```

4. Run the command to remove the passwords from git history.

```shell
bfg --replace-text passwords.txt reponame.git
```

5. cd into the repo directory and force git to push back to github.

```shell
cd reponame.git
git push --force
```

6. cd back out of the directory and delete the repo folder and passwords.txt file. You will be left with a .bfg-report you can use to see what was changed. This can be deleted as well once done.

> If any sensitive data was included inside of a PR you will need to open a ticket with github asking them to remove the PR data from there end.
{: .prompt-warning }

More information can be found here: [Removing sensitive data from a repository - GitHub Docs](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository)