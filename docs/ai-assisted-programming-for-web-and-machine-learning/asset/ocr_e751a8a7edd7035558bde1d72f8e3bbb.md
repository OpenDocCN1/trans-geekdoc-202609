+   - **Pre-commit hooks**: Automate tasks like linting and formatting before every commit:
  `pip install pre-commit`

```
pre-commit install
```

# # Advanced Git techniques

If you are looking to step up your Git skills, check out these advanced techniques to make coding and project management even easier:

+   - **Interactive rebasing**: Clean up commit history by combining or rearranging commits:
  `git rebase -i HEAD~5`

+   - **Cherry-picking**: Apply specific commits to another branch:
  `git cherry-pick commit_hash`

+   - **Stashing changes**: Save your uncommitted changes temporarily:
  `git stash`n  `git stash apply`

+   - **Conflict resolution**: Resolve merge conflicts manually and mark the files as resolved:

```
git add resolved_file.py
git commit
```

# # Real-world use cases

Git is not just for handling code; it is a versatile tool with real-world uses in many fields. Here are a few examples of how it is making a difference:

+   - **ML development**: A team builds a sentiment analysis model using feature branches for data preprocessing, model development, and evaluation while automating tests with GitHub Actions.

+   - **Open-source contributions**: Contribute to an open-source project by forking a repository, implementing