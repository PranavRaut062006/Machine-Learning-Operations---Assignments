# Assignment 1 – Dataset Versioning using DVC

## Objective

Implement dataset versioning using **Data Version Control (DVC)** with **Git** for source-code and version history management.

This assignment contains two parts:

1. Student Dataset – 2 versions
2. Employee Salary Dataset – 6 versions

---

# Technologies Used

* Python 3
* Pandas
* Git
* DVC
* VS Code
* Jupyter Notebook (`.ipynb`)

---

# 1. Initial Setup

## Navigate to MLOps directory

```powershell
cd "D:\COLLEGE\SEM5\MLOPs"
```

## Create the main project folder

```powershell
mkdir mlops-assignments
cd mlops-assignments
```

## Create Python virtual environment

```powershell
python -m venv .venv
```

## Activate virtual environment

```powershell
.venv\Scripts\Activate.ps1
```

The terminal should show:

```text
(.venv)
```

## Install required packages

```powershell
python -m pip install --upgrade pip
pip install dvc jupyter pandas
```

## Verify installations

```powershell
python --version
git --version
dvc --version
jupyter --version
python -c "import pandas; print(pandas.__version__)"
```

---

# 2. Initialize Git and DVC

From the `mlops-assignments` directory:

```powershell
git init
```

```powershell
dvc init
```

Check Git status:

```powershell
git status
```

---

# Part 1 – Student Dataset

## 3. Create Project Structure

```powershell
mkdir Assignment-1-Student
mkdir Assignment-1-Student\data
mkdir Assignment-1-Student\notebooks
```

Project structure:

```text
Assignment-1-Student/
├── data/
└── notebooks/
```

---

## 4. Create Student Dataset – Version 1

Create the notebook:

```text
Assignment-1-Student/notebooks/Assignment1.ipynb
```

The dataset is created using Pandas and saved as:

```text
Assignment-1-Student/data/students.csv
```

Version 1 contains:

* 10 students
* 5 columns

Columns:

```text
Student_ID
Name
Age
Branch
CGPA
```

---

## 5. Track Student Version 1 using DVC

```powershell
dvc add Assignment-1-Student/data/students.csv
```

Add files to Git:

```powershell
git add .
```

Commit Version 1:

```powershell
git commit -m "Version 1: Initial student dataset"
```

Check commit history:

```powershell
git log --oneline
```

---

## 6. Create Student Version 2

Three new student records are added to the existing dataset.

The dataset changes from:

```text
10 students → 13 students
```

The updated dataset is saved again as:

```text
Assignment-1-Student/data/students.csv
```

---

## 7. Track Student Version 2 using DVC

```powershell
dvc add Assignment-1-Student/data/students.csv
```

Add changes to Git:

```powershell
git add .
```

Commit Version 2:

```powershell
git commit -m "Version 2: Added three new student records"
```

Check history:

```powershell
git log --oneline
```

---

# 8. Restore Student Dataset Versions

View Git history:

```powershell
git log --oneline
```

Switch to Version 1:

```powershell
git checkout <version-1-commit-id>
```

Restore the corresponding dataset:

```powershell
dvc checkout
```

Return to the latest version:

```powershell
git checkout main
```

Restore the latest dataset:

```powershell
dvc checkout
```

Verify the dataset using Pandas:

```powershell
python -c "import pandas as pd; df=pd.read_csv('Assignment-1-Student/data/students.csv'); print('Students:', len(df))"
```

---

# Part 2 – Employee Salary Dataset

## 9. Create Project Structure

```powershell
mkdir Assignment-1-Employee
mkdir Assignment-1-Employee\data
mkdir Assignment-1-Employee\notebooks
```

Project structure:

```text
Assignment-1-Employee/
├── data/
└── notebooks/
```

Create:

```text
Assignment-1-Employee/notebooks/Assignment1.ipynb
```

---

# 10. Employee Version 1 – Initial Dataset

Create the employee dataset using Pandas.

Save it as:

```text
Assignment-1-Employee/data/employees.csv
```

Initial columns:

```text
Employee_ID
Employee_Name
Department
Salary
```

Version 1 contains:

```text
10 employees
4 columns
```

Track the dataset:

```powershell
dvc add Assignment-1-Employee/data/employees.csv
```

Add to Git:

```powershell
git add .
```

Commit:

```powershell
git commit -m "Version 1: Initial employee salary dataset"
```

---

# 11. Employee Version 2 – Salary Increment

Increase every employee salary by **10%**.

Dataset remains:

```text
10 employees
4 columns
```

Track the modified dataset:

```powershell
dvc add Assignment-1-Employee/data/employees.csv
```

Commit:

```powershell
git add .
git commit -m "Version 2: Increased all employee salaries by 10%"
```

---

# 12. Employee Version 3 – Years of Experience

Add the column:

```text
Years_of_Experience
```

Dataset becomes:

```text
10 employees
5 columns
```

Track with DVC:

```powershell
dvc add Assignment-1-Employee/data/employees.csv
```

Commit:

```powershell
git add .
git commit -m "Version 3: Added Years_of_Experience column"
```

---

# 13. Employee Version 4 – Performance Rating

Add the column:

```text
Performance_Rating
```

Possible values:

```text
Excellent
Very Good
Good
Average
```

Dataset becomes:

```text
10 employees
6 columns
```

Track with DVC:

```powershell
dvc add Assignment-1-Employee/data/employees.csv
```

Commit:

```powershell
git add .
git commit -m "Version 4: Added Performance_Rating column"
```

---

# 14. Employee Version 5 – Add New Employees

Add three new employee records.

Dataset changes:

```text
10 employees → 13 employees
```

Schema remains:

```text
6 columns
```

Track with DVC:

```powershell
dvc add Assignment-1-Employee/data/employees.csv
```

Commit:

```powershell
git add .
git commit -m "Version 5: Added three new employee records"
```

---

# 15. Employee Version 6 – Update Department Names

The department names are changed according to the following mapping:

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

# 16. Verify Git and DVC

Check Git status:

```powershell
git status
```

Expected:

```text
nothing to commit, working tree clean
```

Check DVC status:

```powershell
dvc status
```

Expected:

```text
Data and pipelines are up to date.
```

View all commits:

```powershell
git log --oneline
```

---

# 17. Restore Employee Dataset Versions

View commit history:

```powershell
git log --oneline
```

Switch to an older version:

```powershell
git checkout <commit-id>
```

Restore the corresponding dataset:

```powershell
dvc checkout
```

Verify the restored dataset:

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

Verify the final dataset:

```powershell
python -c "import pandas as pd; df=pd.read_csv('Assignment-1-Employee/data/employees.csv'); print('Shape:', df.shape); print('Columns:', list(df.columns))"
```

Expected final dataset:

```text
Shape: (13, 6)
```

---

# 18. DVC Workflow Summary

The workflow followed for every dataset version was:

```text
Create / Modify Dataset
        ↓
Save CSV
        ↓
dvc add <dataset.csv>
        ↓
git add .
        ↓
git commit
        ↓
Next Dataset Version
```

Git stores the **version history and DVC metadata**, while DVC manages the **actual dataset versions**.

---

# 19. Dataset Evolution

## Student Dataset

| Version   | Changes                    |
| --------- | -------------------------- |
| Version 1 | Initial 10 student records |
| Version 2 | Added 3 students, total 13 |

## Employee Dataset

| Version   | Changes                         |
| --------- | ------------------------------- |
| Version 1 | Initial employee salary dataset |
| Version 2 | Increased salaries by 10%       |
| Version 3 | Added Years_of_Experience       |
| Version 4 | Added Performance_Rating        |
| Version 5 | Added 3 new employees           |
| Version 6 | Updated department names        |

---

# 20. Learning Outcomes

* Created custom datasets using Pandas
* Used DVC for dataset versioning
* Used Git for version control
* Created multiple dataset versions
* Handled dataset value modifications
* Handled schema evolution
* Added new records
* Restored previous dataset versions
* Understood the relationship between Git and DVC
* Maintained reproducible datasets for MLOps projects

---

# Conclusion

This assignment demonstrates **Dataset Versioning using DVC and Git**.

The Student Dataset was maintained through two versions, while the Employee Salary Dataset was maintained through six versions. Previous dataset versions were successfully restored using Git and DVC, demonstrating reproducibility and version-controlled dataset management.
