# Daymark Todo

A small vanilla JavaScript todo tracker served by Bun. Add, edit, complete, delete, search, and filter tasks. Your list is saved in this browser with `localStorage`.

## Run locally

```bash
bun install
bun run start
```

Open <http://localhost:3000>. The `/health` route returns a small health response.

## Run with Docker

```bash
docker build -t daymark-todo .
docker run --rm -p 3000:3000 daymark-todo
```

Tasks stay in the browser profile where they were created; the server does not store task data.

## Frontend

The frontend UI was made using Codex with vanilla HTML, CSS, and JavaScript.

## Terraform Docker task

Terraform uses the Docker provider to manage a local container for this app. Build the image first so Terraform can find it on the local Docker host:

```powershell
docker build -t daymark-todo:local .
terraform -chdir=terraform init
terraform -chdir=terraform plan -out=tfplan-daymark
terraform -chdir=terraform apply tfplan-daymark
```

Open <http://localhost:18080>. The health route is <http://localhost:18080/health>.

Inspect Terraform state and remove the container when finished:

```powershell
terraform -chdir=terraform state list
terraform -chdir=terraform state show docker_container.daymark
terraform -chdir=terraform destroy
```

Execution logs are in `execution-logs/`. Terraform destroy removes the container; the locally built image remains on the Docker host.

## Git workflow

This repository uses three branches:

- `main` contains the stable project history.
- `dev` is the integration branch.
- `feature` contains task-specific changes before review.

Push each local branch to GitHub so it appears in the remote repository:

```powershell
git push -u origin main
git push -u origin dev
git push -u origin feature
```

The `-u` option sets the upstream for each branch, so later `git push` and `git pull` commands can use the configured remote branch. Check local and remote branches with:

```powershell
git branch -a
```

Use pull requests to merge `feature` into `dev`, then `dev` into `main`. After the workflow is complete, an annotated version tag can mark the release:

```powershell
git switch main
git tag -a v1.0.0 -m "Version 1.0.0"
git push origin v1.0.0
```

The `-a` option creates an annotated tag with metadata, and `-m` adds its message.
