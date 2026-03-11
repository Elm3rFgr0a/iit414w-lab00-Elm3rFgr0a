# iit414w-lab00 — Reproducibility Runbook

| Field | Value |
|---|---|
| **Full name** | Benjamin Figueroa |
| **GitHub username** | Elm3rFgr0a |
| **Course** | IIT414W |
| **Date** | March 11, 2026 |

---

## System info

| Property | Value |
|---|---|
| Operating system | Windows 11 (Build 22631) |
| Python version | 3.10 (managed by conda) |
| Conda version | 24.x (`conda --version` to confirm) |

---

## Setup instructions

Follow these steps in order. Commands are written for **Anaconda Prompt** or any terminal where `conda` is available.

**1. Clone the repository (if you haven't already)**
```bash
git clone https://github.com/Elm3rFgr0a/iit414w-lab00-Elm3rFgr0a.git
cd iit414w-lab00-Elm3rFgr0a
```

**2. Create the conda environment from the provided file**
```bash
conda env create -f environment.yml
```
This installs Python 3.10, JupyterLab, NumPy, pandas, scikit-learn, matplotlib, seaborn, requests, FastF1, and ipykernel — all at pinned versions.

**3. Activate the environment**
```bash
conda activate iit414w
```
You should see `(iit414w)` in your prompt. All subsequent commands must be run inside this environment.

**4. Register the kernel with Jupyter (one-time setup)**
```bash
python -m ipykernel install --user --name iit414w --display-name "Python (iit414w)"
```

**5. Launch JupyterLab**
```bash
jupyter lab
```

---

## How to run

Run the notebooks **in this order** — `setup_check.ipynb` validates the environment before `data_check.ipynb` attempts live data downloads.

| Order | Notebook | Purpose |
|---|---|---|
| 1 | `setup_check.ipynb` | Verifies packages, versions, disk space, and Git setup |
| 2 | `data_check.ipynb` | Loads real F1 data from FastF1 and the Jolpica API |

To run a notebook from the command line (non-interactive):
```bash
jupyter nbconvert --to notebook --execute setup_check.ipynb --output setup_check_out.ipynb
jupyter nbconvert --to notebook --execute data_check.ipynb --output data_check_out.ipynb
```

Or open each file in JupyterLab and run **Kernel → Restart Kernel and Run All Cells**.

> **Note:** `data_check.ipynb` downloads FastF1 session data on first run (1–3 min depending on connection). Subsequent runs use the local cache and are fast.

---

## Problems encountered

**Problem 1 — FastF1 `SyntaxError` in f-string with nested quotes**

While writing Cell 2 of `data_check.ipynb`, the line:
```python
print(f'Event  : {session.event.get("EventName", 'n/a')}')
```
raised a `SyntaxError: f-string: unmatched '('` because single quotes inside a single-quoted f-string break parsing in Python 3.10.

**Fix:** Replaced the f-string with a plain `print()` using comma separation:
```python
print('Event  :', session.event.get('EventName', 'n/a'))
```

---

**Problem 2 — FastF1 cache path resolving to wrong directory**

The initial cache path used `os.path.dirname(os.getcwd())` to navigate up one level, but when the notebook was opened from a different working directory (e.g., directly from JupyterLab file browser), `os.getcwd()` pointed to the repo root instead of the notebook folder, so the cache ended up in an unexpected location.

**Fix:** Used `os.path.abspath` with a path relative to the repo root and added `os.makedirs(..., exist_ok=True)` so the directory is always auto-created regardless of where the notebook is launched from.

---

## Expected outputs

### `setup_check.ipynb`
- A 6-row package version table (numpy, pandas, sklearn, matplotlib, seaborn, fastf1)
- Working directory, FastF1 cache path, and Git version printed
- Platform info (OS, Python executable, disk space) printed
- Self-assessment checklist table with scores and one action sentence
- Prediction card dictionary printed
- ML paradigm table (3 rows: supervised, unsupervised, reinforcement)
- No `NotImplementedError` raised in any cell

### `data_check.ipynb`
- `HTTP status code: 200` from the Jolpica API
- FastF1 session loads without error; prints session name, event name, results shape, column list, and first 5 lap rows
- 20 driver records returned from the standings endpoint
- First 3 drivers printed with name, nationality, and points
