# Assignment 2 – ML Experiment Tracking using MLflow

## Objective

The objective of this assignment is to perform and track machine learning experiments using **MLflow**. The Iris dataset is used with a Logistic Regression classifier, while different hyperparameter values are tested and compared.

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* MLflow
* Matplotlib
* Jupyter Notebook

## Project Structure

```text
Assignment-2/
├── notebooks/
│   └── Assignment2.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

## Setup

The assignment was performed using Ubuntu/WSL with a Python virtual environment.

### 1. Create and activate virtual environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 2. Install dependencies

```bash
pip install --upgrade pip
pip install mlflow scikit-learn pandas numpy matplotlib jupyter ipykernel
```

### 3. Start MLflow Tracking Server

From the `Assignment-2` directory:

```bash
mlflow server --backend-store-uri sqlite:///notebooks/mlflow.db --port 5000
```

The MLflow UI can then be accessed at:

```text
http://127.0.0.1:5000
```

## Experiment Workflow

The notebook performs the following operations:

1. Loads the Iris dataset using Scikit-learn.
2. Converts the dataset into a Pandas DataFrame.
3. Examines the dataset structure, statistics, class distribution, and missing values.
4. Separates features and target values.
5. Splits the data into 80% training and 20% testing sets.
6. Applies `StandardScaler` to the feature data.
7. Creates an MLflow experiment named **Iris Classification - Hyperparameter Tracking**.
8. Trains a baseline Logistic Regression model.
9. Tests different `C` values:

   * 0.1
   * 1.0
   * 10.0
10. Tests different `max_iter` values:

* 50
* 100
* 200

11. Logs model parameters, accuracy metrics, models, and dataset information to MLflow.
12. Retrieves and compares experiment runs.
13. Visualizes the effect of `C` and `max_iter` on test accuracy.
14. Selects and evaluates the best-performing model.
15. Logs the final selected model separately in MLflow.

## Results

| Experiment     | Test Accuracy |
| -------------- | ------------: |
| C = 0.1        |        86.67% |
| C = 1.0        |        93.33% |
| C = 10.0       |       100.00% |
| max_iter = 50  |        93.33% |
| max_iter = 100 |        93.33% |
| max_iter = 200 |        93.33% |

### Best Model

* **Algorithm:** Logistic Regression
* **C:** 10.0
* **max_iter:** 100
* **Scaler:** StandardScaler
* **Test Accuracy:** 100%
* **Correct Predictions:** 30/30

## MLflow Tracking

MLflow was used to track:

* Experiment runs
* Hyperparameters
* Test accuracy
* Dataset information
* Trained model artifacts
* Final selected model

The MLflow UI provides a convenient way to compare the different experiment runs and identify the best-performing configuration.

## Conclusion

This assignment demonstrates how MLflow can be used to organize and compare machine learning experiments. By tracking parameters, metrics, datasets, and model artifacts, the experiments can be reproduced and evaluated systematically. The best Logistic Regression configuration achieved **100% test accuracy** on the Iris test set.
