# EX.NO:02
# AIM:
  To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
dt=pd.read_csv("titanic_dataset.csv")
dt
```
```py
dt.info()
```
```py
dt.shape
```
(891, 12)

```py
dt.set_index("PassengerId",inplace=True)
dt
```
```py
dt.describe()
```
```py
dt.nunique()
```
```py
dt["Survived"].value_counts()
```
```py
per=(dt["Survived"].value_counts()/dt.shape[0]*100).round(2)
per
```
```py
sns.countplot(data=dt,x="Survived")
```
![image](https://github.com/user-attachments/assets/48e8743c-4fe4-41a5-a292-2ffbafb9c2b7)

```py
dt.Pclass.unique()
```
array([3, 1, 2])

```py
dt.rename(columns={"Sex":"Gender"},inplace=True)
dt
```
```py
sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5,aspect=.7)
```
![image](https://github.com/user-attachments/assets/e5849b5a-6d9c-481c-a236-55ba69148749)

```py
sns.catplot(x="Survived",hue="Gender",data=dt,kind="count")
```
![image](https://github.com/user-attachments/assets/9873b906-bf45-4db7-9dbd-f95a3ea885b5)

```py
dt.boxplot(column="Age", by="Survived")
```
![image](https://github.com/user-attachments/assets/8b407bf1-ba8a-4f4b-974f-d5f8225ed3c2)

```py
sns.scatterplot(x=dt["Age"],y=dt["Fare"])
```
![image](https://github.com/user-attachments/assets/6355d284-029b-4365-939a-6d7b71f47e74)

```py
sns.jointplot(x=dt["Age"],y=dt["Fare"])
```
![image](https://github.com/user-attachments/assets/9ebe95fb-c6c7-432b-a0c1-9a1e23a29377)

```py
fig, ax1= plt.subplots(figsize=(8,5))
pt = sns.boxplot(ax=ax1, x = 'Pclass', y= 'Age',hue = 'Gender', data = dt)
```
![image](https://github.com/user-attachments/assets/07156353-a47d-4406-b0ef-96e6f4480c84)

```py
sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count")
```
![image](https://github.com/user-attachments/assets/e2970cd9-f690-40e0-8e9e-7a203a455151)

```py
numeric_dt = dt.select_dtypes(include=['number'])
corr = numeric_dt.corr()
sns.heatmap(corr,annot=True)
```
![image](https://github.com/user-attachments/assets/289f7bd5-c020-4853-b420-e4fd422d7191)

```py
sns.pairplot(dt)
```
![image](https://github.com/user-attachments/assets/b026edcd-a362-43be-9155-57aa00c2aaa3)

# RESULT
  Thus the Exploratory Data Analysis has been successfully performed  on the given data set.
