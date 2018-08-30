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

All bugs and feature requests should be tracked in github issues. Commits and pull requests that close a particular issue should reference the issue.

### Pull Requests

- All code must be reviewed in a pull request before merging to master
- Add the `[WIP]` prefix to work-in-progress pull requests that are not ready for merge
- Prepare your pull request so that it is convenient to review
    - Verify that all tests succeed
    - Verify that the software guidelines have been adhered to
    - Verify the patch (no extraneous whitespace or files added)
    - Add supplemental information about testing procedures, usage, and images of ui changes to the pull request description
- The author should always perform their own review before asking for their peers' review
- All tests must pass before approval
- When you believe your patch is ready to merge, request a review from a maintainer

### Labels

Labels are additional metadata that may be attached to issues and pull requests. Each project has its own labels. Every project should have these labels:

- `bug` The issue is a bug
- `feature` The issue is releated to the introduction of a new feature or functionality
- `duplicate` The issue is a duplicate of an existing issue
- `confirm` The issue needs to be confirmed by the project maintainers
- `wont-fix` The issue is rejected by the project maintainers
- `waiting` Something else must be resolved before the issue can be fully addressed

### Milestones

Milestones are used to collect issues and pull requests that need to go into a particular release.

### Tags

Tags in the organization project repository are generally reserved for tagging versions. Personal development tags should go in your personal fork.

## References

- [Mastering Git](https://www.packtpub.com/application-development/mastering-git)
- [gitref](http://gitref.org)
- [progit](http://progit.org)
- [gitready](http://gitready.com)
