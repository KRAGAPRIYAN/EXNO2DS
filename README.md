# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.

## Date: 29/04/2026
## Roll.No: 212225040323
      
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

## Program
Developed By: K RAGAPRIYAN
RegNumber: 212225040323

```
# Exploratory Data Analysis on Titanic Dataset

# STEP 1: Import required packages
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

# Load dataset
df = pd.read_csv("titanic_dataset.csv")

# Display first 5 rows
print(df.head())

# Display dataset information
print(df.info())


# STEP 2: Replace null values using mean/median/mode

# Age -> median
df['Age'].fillna(df['Age'].median(), inplace=True)

# Fare -> mean
df['Fare'].fillna(df['Fare'].mean(), inplace=True)

# Embarked -> mode
df['Embarked'].fillna(df['Embarked'].mode()[0], inplace=True)

# Check null values
print(df.isnull().sum())


# STEP 3: Use boxplot to analyze outliers
plt.figure(figsize=(8,5))
sns.boxplot(x=df['Fare'])
plt.title("Boxplot for Fare")
plt.show()


# STEP 4: Remove outliers using IQR method
Q1 = df['Fare'].quantile(0.25)
Q3 = df['Fare'].quantile(0.75)
IQR = Q3 - Q1

lower_limit = Q1 - 1.5 * IQR
upper_limit = Q3 + 1.5 * IQR

df = df[(df['Fare'] > lower_limit) & (df['Fare'] <= upper_limit)]

print("Dataset after removing outliers:")
print(df.shape)


# STEP 5: Countplot for categorical data
plt.figure(figsize=(6,4))
sns.countplot(x='Survived', hue='Sex', data=df)
plt.title("Survival Count based on Gender")
plt.show()


# STEP 6: Displot for univariate distribution
sns.displot(df['Age'], kde=True)
plt.title("Distribution of Age")
plt.show()


# STEP 7: Cross Tabulation
cross_tab = pd.crosstab(df['Sex'], df['Survived'])
print("Cross Tabulation:")
print(cross_tab)


# STEP 8: Heatmap for relationship analysis
plt.figure(figsize=(10,6))
correlation = df.corr(numeric_only=True)

sns.heatmap(correlation, annot=True, cmap="coolwarm")
plt.title("Heatmap of Correlation Matrix")
plt.show()

```

## Output

![alt text](<Screenshot 2026-06-01 133606.png>)
![alt text](<Screenshot 2026-06-01 133657.png>)
![alt text](<Screenshot 2026-06-01 133716.png>)
![alt text](<Screenshot 2026-06-01 133738.png>)
![alt text](<Screenshot 2026-06-01 133755.png>)
![alt text](<Screenshot 2026-06-01 133809.png>)

# RESULT

Thus, Exploratory Data Analysis was performed on the given dataset using data cleansing, outlier removal, countplot, displot, cross tabulation and heatmap methods successfully.