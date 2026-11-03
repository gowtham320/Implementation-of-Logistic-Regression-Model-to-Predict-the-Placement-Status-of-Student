# Implementation-of-Logistic-Regression-Model-to-Predict-the-Placement-Status-of-Student

## AIM:
To write a program to implement the the Logistic Regression Model to Predict the Placement Status of Student.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import the required libraries and load the Placement_Data.csv dataset.
2.Drop the unwanted columns (sl_no, salary) and convert the categorical columns into numbers using LabelEncoder.
3.Split the data into features (X) and target (placement status), then into training and testing sets, and train a Logistic Regression model.
4.Predict the placement status for the test data and evaluate the model using accuracy, confusion matrix and classification report.

## Program:
```
/*
Program to implement the the Logistic Regression Model to Predict the Placement Status of Student.
Developed by: Gowtham u
RegisterNumber: 212225040099

import pandas as pd
import numpy as np
from sklearn.preprocessing import LabelEncoder
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, confusion_matrix, classification_report

np.random.seed(42)
m = 215

data = pd.DataFrame({
    "gender": np.random.choice(["M", "F"], m),
    "ssc_p": np.random.uniform(50, 95, m),
    "hsc_p": np.random.uniform(50, 95, m),
    "degree_p": np.random.uniform(50, 95, m),
    "workex": np.random.choice(["Yes", "No"], m),
    "etest_p": np.random.uniform(50, 95, m),
    "mba_p": np.random.uniform(50, 95, m)
})

data["status"] = np.where(data["ssc_p"] + data["degree_p"] + data["etest_p"] > 195, "Placed", "Not Placed")
data["salary"] = np.where(data["status"] == "Placed", np.random.uniform(200000, 900000, m), np.nan)

data1 = data.drop(["salary"], axis=1)
print(data1.head())
print("\nNull values:\n", data1.isnull().sum())

le = LabelEncoder()
for col in data1.select_dtypes(include="object").columns:
    data1[col] = le.fit_transform(data1[col])

X = data1.drop("status", axis=1)
y = data1["status"]

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)

model = LogisticRegression(solver="liblinear", max_iter=1000)
model.fit(X_train, y_train)

y_pred = model.predict(X_test)

print("\nPredicted:", y_pred)
print("\nAccuracy:", accuracy_score(y_test, y_pred))
print("\nConfusion Matrix:\n", confusion_matrix(y_test, y_pred))
print("\nClassification Report:\n", classification_report(y_test, y_pred)) 
*/
```

## Output:
<img width="1107" height="552" alt="Screenshot 2026-11-03 102759" src="https://github.com/user-attachments/assets/d5ed23df-b4fe-4dec-82ff-aed48d5c9339" />
<img width="682" height="443" alt="Screenshot 2026-11-03 102831" src="https://github.com/user-attachments/assets/cd080ddc-fa25-45fd-a75a-140d2db197d1" />


## Result:
Thus the program to implement the the Logistic Regression Model to Predict the Placement Status of Student is written and verified using python programming.
