# Assignment 1 – Student Dataset Versioning using DVC

## Objective

Implement dataset versioning using Data Version Control (DVC) and Git.

## Dataset

The Student Dataset contains:

* Student_ID
* Name
* Age
* Branch
* CGPA

## Dataset Versions

| Version   | Changes                                 |
| --------- | --------------------------------------- |
| Version 1 | Initial dataset with 10 students        |
| Version 2 | Added 3 new students, total 13 students |

## DVC Workflow

```text
Create / Modify Dataset
        ↓
Save CSV
        ↓
dvc add students.csv
        ↓
git add .
        ↓
git commit
```

## Version 1

Initial dataset containing 10 student records.

```bash
dvc add Assignment-1-Student/data/students.csv
git add .
git commit -m "Version 1: Initial student dataset"
```

## Version 2

Three new student records were added, increasing the dataset from 10 to 13 records.

```bash
dvc add Assignment-1-Student/data/students.csv
git add .
git commit -m "Version 2: Added three new student records"
```

## Restoring Previous Versions

Git is used to switch to the required commit and DVC restores the corresponding dataset.

```bash
git checkout <commit-id>
dvc checkout
```

## Verification

Version 1 was successfully restored with 10 students.

Version 2 was successfully restored with 13 students.

## Learning Outcomes

* Dataset versioning using DVC
* Git-based version control
* Creating multiple dataset versions
* Restoring previous dataset versions
* Understanding Git and DVC integration
* Maintaining reproducible datasets
