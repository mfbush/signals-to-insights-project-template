# 002: Copy the course environment

- **Status:** active
- **Created:** YYYY-MM-DD
- **Updated:** YYYY-MM-DD
- **Due:** 2026-11-08, after task 001

## Goal

This repository builds the same Python environment as the course repository, from its own copy of `pyproject.toml` and `uv.lock`, and a notebook here runs on it. The copy matters because Reproducibility is a criterion of the final submission. A reader who clones your repository needs the lock file to rebuild the packages your notebook ran with, and a path to the course folder on your laptop gives them nothing.

## Steps

1. In the VS Code terminal, in your project folder, copy the two files from the course clone beside it:

```bash
cp ../signals-to-insights/pyproject.toml .
```

```bash
cp ../signals-to-insights/uv.lock .
```

2. Build the environment. It takes a minute or less, because uv reuses the packages it downloaded for the course.

```bash
uv sync
```

3. Check what git sees:

```bash
git status
```

The list of untracked files should show `pyproject.toml` and `uv.lock`, and no `.venv/`. If `.venv/` is listed, `.gitignore` is missing or misspelled; fix task 001 before you go on. If it is not listed, close task 001.

4. Make a new notebook named `check.ipynb`. Click **Select Kernel** at the top right, choose **Python Environments**, and pick the entry that shows `.venv` and Python 3.14. Paste this cell and run it:

```python
import sys

import numpy as np
import pandas as pd
import matplotlib
import scipy

print(f"Python     {sys.version.split()[0]}")
print(f"NumPy      {np.__version__}")
print(f"pandas     {pd.__version__}")
print(f"SciPy      {scipy.__version__}")
print(f"Matplotlib {matplotlib.__version__}")
```

5. Compare its output with the last cell of any session notebook you have run in the course clone. Then delete `check.ipynb`, and commit and push the two files:

```bash
git add pyproject.toml uv.lock
```

```bash
git commit -m "Copy the course environment"
```

```bash
git push
```

If the course announces a change to its package list, copy the two files again, run `uv sync`, and commit them. If you use conda for the course, choose the kernel named `signals` in step 4, and still commit `pyproject.toml` and `uv.lock` so that a reader with uv can rebuild the environment.

## Done when

The cell in step 4 prints Python 3.14 and the same package versions as a session notebook, and the two files are pushed.

## Progress log

## Outcome
