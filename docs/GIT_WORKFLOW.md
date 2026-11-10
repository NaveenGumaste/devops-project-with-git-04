# Git Workflow Notes

## Objective

Manage the Daymark Todo project using Git branches, commits, pull requests, and a release tag.

## Branches

- `main` holds the stable project history.
- `dev` is the integration branch.
- `feature` is for the Git workflow documentation change.

## Completed locally

- [x] Initialized the Git repository on `main`.
- [x] Added the project files, README, and `.gitignore`.
- [x] Created the initial project commit.
- [x] Created the `dev` and `feature` branches.

## Remaining tasks

- [ ] Push the repository and branches to GitHub.
- [ ] Open and merge a pull request from `feature` into `dev`.
- [ ] Open and merge a pull request from `dev` into `main`.
- [ ] Create and push an annotated release tag.
- [ ] Verify the final branches and tag on GitHub.

## Pull request flow

Changes are developed on `feature`, reviewed and merged into `dev`, then `dev` is merged into `main` through a pull request.

## Tag convention

Use an annotated tag such as `v1.0.0` to mark the completed Git workflow milestone.
