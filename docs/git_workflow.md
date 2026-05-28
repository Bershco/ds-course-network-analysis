# Git and GitHub Workflow

Use a single repository with one branch per assignment part.

## Branches

Recommended branches:

```text
main
part-a
part-b
part-c
optional-practice
```

Use more branches if a part becomes too large.

## Before starting any work

```bash
git status
```

If the repository is not initialized:

```bash
git init
git add AGENTS.md README.md requirements.txt .gitignore docs prompts
git commit -m "Initialize network analysis assignment repository"
```

## Starting a part

```bash
git checkout main
git pull --ff-only || true
git checkout -b part-a
```

Replace `part-a` with the relevant branch.

## Commit frequently

Good commit examples:

```text
Add Part A notebook scaffold
Implement movie degree distribution analysis
Add graph embedding visualization for movie networks
Export Cytoscape and Gephi files for Part A
Execute Part A notebook
```

## Push and PR

If remote exists:

```bash
git push -u origin part-a
```

If GitHub CLI is installed and authenticated:

```bash
gh pr create --fill
```

If not, print manual instructions for creating the PR.

## Never do these without explicit student approval

- Do not force-push.
- Do not rewrite history.
- Do not delete branches.
- Do not commit datasets.
- Do not commit secrets or API keys.
