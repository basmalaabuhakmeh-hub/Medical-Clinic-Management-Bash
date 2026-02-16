# Medical Records Management — Bash Script (Linux)

**ENCS3130 Linux Laboratory (shell project)**  
Bash script for a menu-driven medical clinic system: add/retrieve/update/delete test records, filter by patient ID/date range/status, detect abnormal test results (Hgb, BGT, LDL, systole, diastole), and show average test values. Uses two text files that the script creates on first run: `medicalRecord.txt` (patient records) and `medicalTests.txt` (test definitions and normal ranges).


## Overview

- **Add record** — Patient ID (7 digits), test name (≤10 chars), date (yyyy-mm), result (number + unit), status (Pending/Completed/Reviewed). Appends to `medicalRecord.txt`.
- **Retrieve by patient ID** — (1) All tests for that ID; (2) Abnormal tests only; (3) Tests in a date range; (4) Tests by status. Submenu for options 1–4.
- **Search abnormal tests** — Scans all records and prints tests outside normal ranges (Hgb, BGT, LDL, systole, diastole).
- **Average test value** — Reads `medicalTests.txt` and prints average of numeric range values per test (for reference).
- **Update / Delete** — Update an existing test result or delete a test by patient ID and test name.

**Data files (created by the script):**

- **medicalRecord.txt** — One line per record: `patientID: Test_name, date, value, unit, status`
- **medicalTests.txt** — Created at start with default tests: Hemoglobin (Hgb), BGT, LDL, systole, diastole (name; range; unit). Used for normal-range checks and average display.

---

## Project structure

```
.
├── README.md
└── medical.sh.txt    # Bash script (run as bash medical.sh.txt or rename to medical.sh)
```

**No other project files are required.** The script creates `medicalRecord.txt` and `medicalTests.txt` in the current directory when you run it. No input data or config files need to be added.

---

## Requirements

- **Bash** — Linux, macOS, or WSL/Git Bash on Windows.
- **Standard tools** — `grep`, `sed`, `date`, `bc` (for floating-point comparisons). `bc` is usually pre-installed on Linux; on Windows use WSL or ensure Git Bash has `bc` if you rely on abnormal-test or average logic.
- **Note:** The script uses `sed -i` (in-place edit). On macOS you may need a different `sed` or adjust; on WSL/Linux it works as-is.

---

## Usage

Run from the directory where you want `medicalRecord.txt` and `medicalTests.txt` to live (e.g. the project folder):

```bash
bash medical.sh.txt
```

Or rename the script to `medical.sh`, make it executable, and run:

```bash
mv medical.sh.txt medical.sh
chmod +x medical.sh
./medical.sh
```

Then use the menu: 1 = Add record, 2 = Retrieve by patient ID (submenu), 3 = Abnormal tests, 4 = Average values, 5 = Update, 6 = Delete, 7 = Exit.

---

## Do you need any other files?

**No.** The script is self-contained. It creates and uses only:

- **medicalRecord.txt** — created empty at start, filled when you add/update records.
- **medicalTests.txt** — created and filled with default test definitions at start.

You only need the script file (`medical.sh.txt` or `medical.sh`) and a Bash environment. No extra data or config files are required.
