# 001: Write `.gitignore`

- **Status:** active
- **Created:** YYYY-MM-DD
- **Updated:** YYYY-MM-DD
- **Due:** 2026-11-08, before task 002

## Goal

A file named `.gitignore` in the top folder of the repository, committed and pushed before anything else is added. It lists the files git should never track. Task 002 builds the Python environment, a folder named `.venv` of about 400 MB and thousands of files, and without this file a single `git add .` would put all of it in your repository's history, where it stays even after you delete it.

## Steps

1. In VS Code, click the **New File** icon above the file list and name the file `.gitignore`, with the leading dot and no extension. Windows File Explorer hides names that start with a dot, so make it in VS Code.
2. Paste in these lines. Each comment says why the line is there.

```text
# Python environment built by `uv sync`; anyone can rebuild it from uv.lock
.venv/

# Python's cache of compiled files
__pycache__/

# Jupyter's autosaved copies of each notebook
.ipynb_checkpoints/

# Operating system files
.DS_Store
Thumbs.db
desktop.ini

# Files your notebook writes, rebuilt each time it runs
output/

# Claude Code's record of the permissions you granted on this laptop
.claude/settings.local.json
```

3. If you know your dataset, decide now whether it goes in the repository, by the next section. If you do not know it yet, as for CHEM 427 students before November 3, come back to that section in task 003.
4. Save the file, then commit and push it:

```bash
git add .gitignore
```

```bash
git commit -m "Add .gitignore"
```

```bash
git push
```

Do not add `AGENTS.md`, `judgment-log.md`, `tasks/`, or `.claude/skills/` to this file. The final submission needs all four. Note that the course repository ignores `.claude/skills/`, because a skill you write in session 12 is yours alone, whereas in this repository your skill is part of what you submit.

## Data: commit them, or download them in a cell

Commit your data in a `data/` folder when they total less than about 50 MB and their source allows you to share a copy. GitHub warns about any file over 50 MB and refuses one over 100 MB. Projects 4, 5, 6, and 11 on the CHEM 427 project list download 95 to 145 MB, so they are in the second case.

Otherwise, add this line to `.gitignore`:

```text
# Data downloaded by the load cell in topic.ipynb and the project notebook
data/
```

Then have the notebook's load cell download the file when it is missing. The markdown cell above it gives the URL and the date you accessed it, as the final project page requires.

```python
from pathlib import Path
from urllib.request import urlretrieve

DATA_URL = "https://example.org/spectra.csv"  # accessed 2026-11-05
data_file = Path("data/spectra.csv")
if not data_file.exists():
    data_file.parent.mkdir(exist_ok=True)
    urlretrieve(DATA_URL, data_file)
```

## Done when

`.gitignore` is pushed, and after `uv sync` in task 002, `git status` does not list `.venv/`. Close this task then.

## Progress log

## Outcome
