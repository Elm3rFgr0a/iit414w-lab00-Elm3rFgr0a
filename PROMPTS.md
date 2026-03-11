# AI Usage Log — IIT414W Lab 00

## 🤖 AI Usage Log

---

**Prompt 1**
- **Tool:** Claude Sonnet 4.6
- **Prompt:** Create a code to identify the lowest score of the list like a profesional.
- **Output:** The code provided identifies de lowest score.
- **Status:** Modified
- **Why:** The code provided used simulated scores, so it was modified with my own scores later.

---

**Prompt 2**
- **Tool:** Claude Sonnet 4.6
- **Prompt:** Create a code to compare lap time variance between VER and another driver and print an interpretation sentence.
- **Output:** The code computes standard deviation for both drivers and outputs a table plus a one-line consistency comparison.
- **Status:** Modified
- **Why:** The driver selection logic and interpretation wording were adjusted to match the session data and my own analysis.

---

**Prompt 3**
- **Tool:** Claude Sonnet 4.6
- **Prompt:** Fill the prediction card dictionary with a 2025 F1 championship prediction including evidence plan, assumptions, and failure modes.
- **Output:** A Python dictionary (prediction_card) with predicted champion, evidence sources, assumptions, and invalidation conditions.
- **Status:** Modified
- **Why:** Changed the predicted champion and adjusted the assumptions and failure modes to reflect my own analysis and reasoning.

---

**Prompt 4**
- **Tool:** Claude Sonnet 4.6
- **Prompt:** Create a 3-row table mapping each ML paradigm (supervised, unsupervised, reinforcement learning) to an F1 use case and a misapplication risk.
- **Output:** A pandas DataFrame with one row per paradigm, including use case description and risk if misapplied.
- **Status:** Modified
- **Why:** Adjusted the use case descriptions and risk wording to better reflect my own understanding of each paradigm.

---

**Prompt 5**
- **Tool:** Claude Sonnet 4.6
- **Prompt:** Write an additional system check that reports the Python executable path, platform info, and available disk space with a reproducibility risk note.
- **Output:** Code using sys, platform, and shutil to print interpreter path, OS version, disk usage, and a one-line risk note.
- **Status:** Modified
- **Why:** Kept the structure but rewrote the risk note in my own words to better reflect what I consider the most relevant reproducibility concern.

---

**Prompt 6**
- **Tool:** Claude Sonnet 4.6
- **Prompt:** Write a code cell that queries the Jolpica API for 2024 F1 driver standings, prints the HTTP status code, total driver records, and the first 3 drivers with name, nationality, and points.
- **Output:** A requests.get() call to the Jolpica endpoint with safe JSON navigation through the nested MRData structure and a formatted printout of the first 3 driver entries.
- **Status:** Modified
- **Why:** Adjusted the JSON navigation logic and the printed output format after verifying the actual API response structure matched the expected nesting levels.

---

**Prompt 7**
- **Tool:** Claude Sonnet 4.6
- **Prompt:** Write a code cell that consolidates shape information from both FastF1 and Jolpica data sources and prints a summary including results shape, laps shape, LapTime dtype, and number of driver records.
- **Output:** A code cell with try/except blocks for each source that prints dataset dimensions and key column types for quick verification.
- **Status:** Modified
- **Why:** Adjusted the printed labels and formatting to match my preferred output style and added clarifying comments.

---
