# Daily Git Workflow

This repository is based on AnyBody’s `ammr4-beta`, which is the main upstream model I regularly fetch from.  
My own working base branch is `pelvicfloor`, and my testing branch is `testing-pelvicfloor`.
My Git-Repo: https://github.com/tobiiba/AMMR4-Beta


## Branch purpose

- `ammr4-beta` upstream AnyBody base model.
- `pelvicfloor` my main working branch for development.
- `testing-pelvicfloor` branch for experiments and tests that may not be merged back.

## Daily workflow

### 1) Start by updating the upstream base
From the repo root

```bash
git switch ammr4-beta
git fetch upstream
git merge upstreamammr4-beta
git push origin ammr4-beta
```

This updates my local and forked copy of `ammr4-beta` to the latest AnyBody version.

### 2) Sync my base branch
```bash
git switch pelvicfloor
git merge ammr4-beta
git push
```

This brings the latest upstream changes into my main working branch.

### 3) Work on testing branch if needed
```bash
git switch testing-pelvicfloor
git merge pelvicfloor
git push
```

Use this branch for experiments, tests, and changes that may stay separate from the main development line.

### 4) During the day
- Make changes in the active branch.
- Check status with
  ```bash
  git status
  ```
- Inspect diffs with
  ```bash
  git diff
  ```
- Commit small logical changes regularly
  ```bash
  git add .
  git commit -m Short message
  ```

### 5) End of day
Push the current branch to GitHub

```bash
git push
```

If this is the first push for a new branch, use

```bash
git push -u origin branch-name
```

## Notes

- Always fetch and merge `ammr4-beta` first before syncing `pelvicfloor`.
- Use `testing-pelvicfloor` for temporary or experimental work.
- Resolve merge conflicts in VS Code if they appear, then test before committing.