# Assignment 1 – Employee Dataset Versioning using DVC

## Objective

Implement dataset versioning using **Data Version Control (DVC)** with Git.

The Employee Salary Dataset is modified through six versions. Each version is tracked using DVC and committed using Git.

## Technologies Used

* Python 3
* Pandas
* Git
* DVC
* VS Code
* Jupyter Notebook

---

# Initial Setup

Navigate to the MLOps project:

```powershell
cd "D:\COLLEGE\SEM5\MLOPs"
mkdir mlops-assignments
cd mlops-assignments
```

Create and activate the virtual environment:

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

Install dependencies:

```powershell
python -m pip install --upgrade pip
pip install dvc jupyter pandas
```

Verify:

```powershell
python --version
git --version
dvc --version
jupyter --version
python -c "import pandas; print(pandas.__version__)"
```

Initialize Git and DVC:

```powershell
git init
dvc init
```

---

# Project Structure

```text
Assignment-1-Employee/
├── data/
│   ├── employees.csv
│   ├── employees.csv.dvc
│   └── .gitignore
│
├── notebooks/
│   └── Assignment1.ipynb
│
└── README_employee.md
```

---

# Version 1 – Initial Dataset

Initial dataset contains:

* Employee_ID
* Employee_Name
* Department
* Salary

Dataset size:

```text
10 employees × 4 columns
```

Track using DVC:

```powershell
dvc add Assignment-1-Employee/data/employees.csv
```

Commit using Git:

```powershell
git add .
git commit -m "Version 1: Initial employee salary dataset"
```

---

# Version 2 – Salary Increment

Every employee's salary was increased by **10%**.

Dataset remains:

```text
10 employees × 4 columns
```

Track the updated dataset:

```powershell
dvc add Assignment-1-Employee/data/employees.csv
```

Commit:

```powershell
git add .
git commit -m "Version 2: Increased all employee salaries by 10%"
```

---

# Version 3 – Added Years of Experience

Added:

```text
Years_of_Experience
```

Dataset becomes:

```text
10 employees × 5 columns
```

Track:

```powershell
dvc add Assignment-1-Employee/data/employees.csv
```

Commit:

```powershell
git add .
git commit -m "Version 3: Added Years_of_Experience column"
```

---

# Version 4 – Added Performance Rating

Added:

```text
Performance_Rating
```

Possible values:

* Excellent
* Very Good
* Good
* Average

Dataset becomes:

```text
10 employees × 6 columns
```

Track:

```powershell
dvc add Assignment-1-Employee/data/employees.csv
```

Commit:

```powershell
git add .
git commit -m "Version 4: Added Performance_Rating column"
```

---

# Version 5 – Added New Employees

Three new employees were added.

Dataset changes:

```text
10 employees → 13 employees
```

Schema remains:

```text
13 employees × 6 columns
```

Track:

```powershell
dvc add Assignment-1-Employee/data/employees.csv
```

Commit:

```powershell
git add .
git commit -m "Version 5: Added three new employee records"
```

---

# Version 6 – Updated Department Names

Department names were changed according to the following mapping:

| Old Name   | New Name             |
| ---------- | -------------------- |
| HR         | Human Resources      |
| IT         | Engineering          |
| Finance    | Accounts & Finance   |
| Marketing  | Business Development |
| Sales      | Sales & Marketing    |
| Operations | Business Operations  |

Track the final dataset:

```powershell
dvc add Assignment-1-Employee/data/employees.csv
```

Commit:

```powershell
git add .
git commit -m "Version 6: Updated department names"
```

---

# Dataset Version History

| Version   | Changes                   | Dataset Size |
| --------- | ------------------------- | ------------ |
| Version 1 | Initial dataset           | 10 × 4       |
| Version 2 | Salary increased by 10%   | 10 × 4       |
| Version 3 | Added Years_of_Experience | 10 × 5       |
| Version 4 | Added Performance_Rating  | 10 × 6       |
| Version 5 | Added 3 employees         | 13 × 6       |
| Version 6 | Updated department names  | 13 × 6       |

---

# Restoring Previous Versions

View Git history:

```powershell
git log --oneline
```

Switch to an older version:

```powershell
git checkout <commit-id>
```

Restore its dataset:

```powershell
dvc checkout
```

Verify the dataset:

```powershell
python -c "import pandas as pd; df=pd.read_csv('Assignment-1-Employee/data/employees.csv'); print('Shape:', df.shape); print('Columns:', list(df.columns))"
```

Return to the latest version:

```powershell
git checkout main
```

Restore the latest dataset:

```powershell
dvc checkout
```

---

# Verification

Check Git:

```powershell
git status
```

Expected:

```text
nothing to commit, working tree clean
```

Check DVC:

```powershell
dvc status
```

Expected:

```text
Data and pipelines are up to date.
```

View commit history:

```powershell
git log --oneline
```

---

# DVC Workflow

```text
Create / Modify Dataset
        ↓
Save CSV
        ↓
dvc add employees.csv
        ↓
git add .
        ↓
git commit
        ↓
Next Dataset Version
```

---

# Learning Outcomes

* Created a custom employee salary dataset
* Versioned datasets using DVC
* Used Git for version control
* Modified dataset values
* Performed schema evolution
* Added new employee records
* Updated categorical values
* Restored previous dataset versions
* Understood Git and DVC integration
* Practiced reproducible dataset management

---

# Conclusion

The Employee Salary Dataset was successfully versioned through six stages using **DVC and Git**.

The assignment demonstrated dataset value modification, schema evolution, record addition, categorical value changes, and restoration of previous dataset versions.
