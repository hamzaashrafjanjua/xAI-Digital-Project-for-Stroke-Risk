# xAI-Digital-Project-for-Stroke-Risk
Implementing xAI Techniques on "healthcare-dataset-stroke"

## Repository structure

```
xAI-Digital-Project-for-Stroke-Risk/
├─ README.md
├─ digitalProject.ipynb
└─ healthcare-dataset-stroke-data.csv
```

### Typical work cycle

```bash
# start from up-to-date main
git checkout main
git pull

# create a branch
git checkout -b feature/add-branch-name

# do work, commit
git add digitalProject.ipynb
git commit -m "Commit comment here"

# rebase on latest and push
git pull --rebase
git push -u origin feature/add-branch-name

# open a PR, get review, merge, then clean up
```

## Notes

- The notebook expects the dataset at `healthcare-dataset-stroke-data.csv` in the repository root (same folder as the notebook). The provided notebook already uses this path.

## Collaboration workflow

To keep the notebook up to date and avoid clashing when multiple people work:

- Use branches
	- Create a feature branch per task: `git checkout -b feature/<short-name>`
	- Open a Pull Request to merge into `main` when ready.
	- Keep PRs small and focused for easy review.

- Pull before you start and before you push
	- Always run `git pull --rebase` on your branch to replay your changes on top of the latest remote.
	- Resolve any conflicts locally; test; then push.

- Avoid noisy notebook diffs
	- This repo is configured to strip notebook outputs on commit (nbstripout), so commits don’t include large output diffs.
	- nbdime is enabled globally for notebook-aware diffs/merges, making conflict resolution clearer.

- Commit discipline
	- Write clear messages about what changed and why.
	- Prefer many small commits over a single large one.

- Data files
	- The dataset is kept at the repository root as `healthcare-dataset-stroke-data.csv`. If you plan to commit very large files or frequent changes, consider Git LFS.

- Reviews and protection (on GitHub)
	- Enable branch protection on `main` and require PR reviews and status checks.
	- Optionally require linear history to encourage `--rebase` workflows.
