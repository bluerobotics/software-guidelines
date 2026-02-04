# Version Control

All projects inside Blue Robotics are hosted by GitHub and version controlled by Git tool (the stupid content tracker). Any project used and modified inside the company, should exist under GitHub, as a main remote repository, fork or just a mirror synchronized by someone.

## Commits

- Commit messages should be clear, and document clearly the development of a project.
- The header line should always be a single meaningful line summarizing the commit.
- Commits should address a single change at a time. Don't mix unrelated changes in a single commit (eg. don't correct style/spelling in the same commit as a refactor or functional change)
- For larger or more significant patches, the body of the commit message should provide a more detailed explanation of why the changes were made.
- Use verbs in the imperative in the commit message (eg."Fix bug that...", "Add file/feature ...")
- No stray (irrelevant) whitespace changes in commits (use `git add -p`)
- Generally, files added to a particular commit should exist under a single path (eg. Don't add files from both `lib/` and `src/` to a single commit; submodule updates should have their own dedicated commit)
- Commits should be in a logical order. (eg. commit the changes to the library, then update the source to use the new library implementation)
- Prefix the header with the context of the patch (e.g., Class: Fix something..., Folder: Add file...)
- All commits should be fast-forwards (no merge commits)
- Generally, the code should build and all tests should pass for every commit (no 'WIP' commits in master)

## What should be tracked

Here you can see a simple list of files that should not be tracked by the version control tool in majority of the cases.
- Binary executable files
    - These files should be download via the build manager, or travis for tests.
- Automatically generated files by the build system.
    - If you add them to the repository, there is a high chance that they will get out of sync with their source. Besides, they are not necessary, as you can always re-generate them.
- Generated doxygen documentation
    - Orphan branches (disconnected branches having no history in common with the master branch), should be used to manage such types. This is because GitHub can be used to manage a project's web pages together in one repository with code.
- Files that contain passwords, private keys and other files that contain privileged and sensitive information.

> Tip: For git, ignored files are considered expendable (ignored files are different from untracked).

## Github

### Pushing

- It is not allowed to push directly to the master branch. Make a pull request.
- Do not force push to branches in the organization repository.

### Branches

The number of branches in the organization repository should be minimized. Generally, push your work to your fork. Branches in the organization repository should be deleted immediately after they are merged. Remember to do your own git housecleaning regularly to avoid a buildup of stale branches. (Note: there is a button on the github pull request page that allows you to delete a branch after merge)

### Issues

All bugs and feature requests should be tracked in github issues. Pull requests that close a particular issue should reference the issue, so that the issue will be [automatically closed](https://help.github.com/articles/closing-issues-using-keywords/) when the pull request is merged. Do not reference github issues in commit messages. This will keep the git repository decoupled from github, and the better option is to call out the problem itself rather than the github issue in the commit message. ie 'fixes *bug that does this*' instead of 'fixes #124'.

### Pull Requests

- All code must be reviewed in a pull request before merging to master
- **Minimum 1 approval required**
- Add the `[WIP]` prefix to work-in-progress pull requests that are not ready for merge, or use GitHub's draft PR feature
- Consolidate pull requests: Rather than creating multiple PRs for the same feature, update existing open ones with necessary modifications. This preserves review history and helps maintainers track your development progression
- Keep PRs focused and self-contained: Avoid combining multiple features in one PR. Complex pull requests can balloon during review and become difficult to merge
- Prepare your pull request so that it is convenient to review
    - Verify that all tests succeed
    - Verify that the software guidelines have been adhered to
    - Verify the patch (no extraneous whitespace or files added)
    - Add supplemental information about testing procedures, usage, and images of ui changes to the pull request description
- The author should always perform their own review before asking for their peers' review. This catches quality issues early and demonstrates respect for maintainers' volunteer time
- All tests must pass before approval
- When you believe your patch is ready to merge, request a review from a maintainer

### Labels

[Labels](https://help.github.com/articles/about-labels) are additional metadata that may be attached to issues and pull requests. Each project has its own labels. Every project should have (and put to use) the [github default labels](https://help.github.com/articles/about-labels/#using-default-labels).

### Milestones

Milestones are used to collect issues and pull requests that need to go into a particular release.

### Tags

Tags in the organization project repository are generally reserved for tagging versions. Personal development tags should go in your personal fork.

## Versioning

- Use [Semantic Versioning (SemVer)](https://semver.org/)
- Tags in organization repositories are reserved for version releases

## Git Tools and Workflows

### Tig (Terminal Interface for Git)
What's the use of having access to everything, if you can't visualize it. This UI tool enhances repository visualization with commands like `log`, `show`, `status`, `reflog`, `blame`, `grep`, and `refs`. Use `tig --all` for comprehensive branch viewing.

### Commit Fixup
Correct previous commits without rewriting history manually. Create an alias like:
```bash
git config --global alias.fix-old '!f() { git commit --fixup=$(git rev-parse HEAD~$(($1-1))); }; f'
```
This lets you fix the nth previous commit with simplified syntax: `git fix-old 3` fixes the 3rd previous commit.

### Interactive Rebase
Use `git rebase -i --autosquash` to reorganize commits. The autosquash feature automatically applies fixup commits to their target commits, streamlining cleanup workflows.

### Git Reflog
This command provides access to all tracked changes and project history states. It enables:
- Recovery from mistakes
- Branch state exploration before merges or rebases
- Checkout to any previous point

Pair with `tig reflog` for better visualization.

### Patch Mode Operations
The `--patch` (or `-p`) flag with `add`, `checkout`, and `stash` enables selective staging of changes. This creates atomic commits containing only necessary modifications and prevents accidental inclusion of unrelated code.

```bash
git add -p           # Interactively stage hunks
git checkout -p      # Interactively discard hunks
git stash -p         # Interactively stash hunks
```

### Git Stash
Temporarily remove uncommitted work without losing it.
```bash
git stash                           # Stash current changes
git stash show stash@{0} --all      # Display stashed changes
git stash apply stash@{0}           # Reapply stashed changes
```

### Cherry-Pick
Copy individual commits or commit ranges to different branches for testing or cross-branch application.
```bash
git cherry-pick <commit-hash>       # Apply a single commit
git cherry-pick A..B                # Apply a range of commits
```

### Recommended Extensions
- [Delta](https://github.com/dandavison/delta): Syntax-highlighted diff and git output
- [Git-absorb](https://github.com/tummychow/git-absorb): Automated fixup commit creation

## References

### Books
- [Mastering Git](https://www.packtpub.com/application-development/mastering-git) (ISBN: 9781783553754)
- [Pro Git (Free)](https://git-scm.com/book/en/v2)

### Official Documentation
- [Git SCM](https://git-scm.com/)
- [Git Repository Layout](https://git-scm.com/docs/gitrepository-layout)
- [Git Internals: Git Objects](https://git-scm.com/book/en/v2/Git-Internals-Git-Objects)
- [Git Index Format](https://git-scm.com/docs/index-format)

### Articles
- [Git Index Deep Dive](https://mincong.io/2018/04/28/git-index/)
- [gitref](http://gitref.org)
- [gitready](http://gitready.com)

### Patrick posts
- [How to rock: First tips](https://patrickelectric.work/blog/2020/how-to-rock-first-tips/)
- [How to rock: Flowing with git](https://patrickelectric.work/blog/2020/how-to-rock-flowing-with-git/)
- [How to rock: Doing the right thing](https://patrickelectric.work/blog/2020/how-to-rock-contribution-tips/)
