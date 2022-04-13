# Ex-04-EDA

## AIM
To perform EDA on the given data set. 

## Explanation
The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
Exploratory Data Analysis (EDA) is an approach to analyze the data using visual techniques. It is used to discover trends, patterns, or to check assumptions with the help of statistical summary and graphical representations. 

## ALGORITHM
### STEP 1
Import the required packages.
### STEP 2
Read the csv file and convert into DataFrame.
### STEP 3
Perform Data Cleaning on the DataSet.
### STEP 4
Detect and Remove the Outliers from the Dataset.
### STEP 5
Perform Exploratory Data Analysis on the data.

## CODE
```
'''
Program developed by: Nithishkumar P
Register No.:212221230070
'''
import pandas as pd
import numpy as np
import seaborn as sns

df=pd.read_csv("supermarket.csv")
df
df.info()
df.isnull().sum()
df.boxplot()

Q1 = df.quantile(0.25)
Q3 = df.quantile(0.75)
IQR = Q3 - Q1
print(IQR)
df_outlier= df[~((df < (Q1 - 1.5 * IQR)) |(df > (Q3 + 1.5 * IQR))).any(axis=1)]
print(df_outlier.shape)
df_outlier.boxplot()
df_outlier.info()

df["Branch"].value_counts()
df_outlier["Branch"].value_counts()
df["Customer type"].value_counts()
df_outlier["Customer type"].value_counts()
df["Gender"].value_counts()
df_outlier["Gender"].value_counts()
df["Payment"].value_counts()
df_outlier["Payment"].value_counts()
df["City"].value_counts()
df_outlier["City"].value_counts()
df["Product line"].value_counts()
df_outlier["Product line"].value_counts()
df["Quantity"].value_counts()
df_outlier["Quantity"].value_counts()

sns.countplot(x="Branch",data=df_outlier)
sns.countplot(x="Customer type",data=df_outlier)
sns.countplot(x="Gender",data=df_outlier)
sns.countplot(x="Payment",data=df_outlier)
sns.countplot(x="City",data=df_outlier)
sns.countplot(x="Product line",data=df_outlier)
sns.countplot(x="Quantity",data=df_outlier)

sns.displot(df_outlier["Total"])
sns.displot(df_outlier["Unit price"])
sns.displot(df_outlier["Rating"])
sns.displot(df_outlier["cogs"])
sns.displot(df_outlier["gross income"])

sns.countplot(x="Branch",hue="Customer type",data=df_outlier)
sns.countplot(x="Gender",hue="Customer type",data=df_outlier)
sns.countplot(x="Quantity",hue="Gender",data=df_outlier)
sns.countplot(x="Customer type",hue="Product line",data=df_outlier)
sns.countplot(x="Gender",hue="Payment",data=df_outlier)
sns.countplot(x="City",hue="Payment",data=df_outlier)
sns.countplot(x="Product line",hue="City",data=df_outlier)
sns.countplot(x="Quantity",hue="Product line",data=df_outlier)
sns.countplot(x="Branch",hue="Quantity",data=df_outlier)
sns.countplot(x="Payment",hue="Product line",data=df_outlier)

sns.displot(df_outlier[df_outlier["Quantity"]==10]["Gender"])
sns.displot(df_outlier[df_outlier["Quantity"]==1]["City"])
sns.displot(df_outlier[df_outlier["Customer type"]=="Member"]["Branch"])
sns.displot(df_outlier[df_outlier["Gender"]=="Female"]["Payment"])
sns.displot(df_outlier[df_outlier["City"]=="Yangon"]["Quantity"])

pd.crosstab(df_outlier["Branch"],df_outlier["Customer type"])
pd.crosstab(df_outlier["Customer type"],df_outlier["Gender"])
pd.crosstab(df_outlier["Gender"],df_outlier["Payment"])
pd.crosstab(df_outlier["City"],df_outlier["Product line"])
pd.crosstab(df_outlier["Product line"],df_outlier["Customer type"])
pd.crosstab(df_outlier["Quantity"],df_outlier["Product line"])

df.corr()
df_outlier.corr()
sns.heatmap(df.corr(),annot=True)
sns.heatmap(df_outlier.corr(),annot=True)
```
## OUPUT

### Initial DataFrame:
![Output](o1.png)
### Number of Rows and Columns in the DataFrame:
![Output](o2.png)
### Sum of null data value present in each column:
![Output](o3.png)
### Graphical Representation - Before removing Outliers:
![Output](o4.png)
### Statistical Method (IQR) to remove Outliers from Dataset:
![Output](o5.png)
### Graphical Representation - After removing Outliers:
![Output](o6.png)
### Infromation on Number of rows and columns after removing Ouliers:
![Output](o7.png)
## EDA 

### Statistical Method of Analyzation:
```
df - DataFrame before removing Outliers.

df_outlier - DataFrame after removing outliers.
```
### Insight about data in Column -Branch:
![Output](o8.png)
### Insight about data in Column -Customer type:
![Output](o9.png)
### Insight about data in Column -Gender:
![Output](o10.png)
### Insight about data in Column -Payment:
![Output](o11.png)
### Insight about data in Column -City:
![Output](o12.png)
### Insight about data in Column -Product line:
![Output](o13.png)
### Insight about data in Column -Quantity:
![Output](o14.png)

### Graphical Method of Analyzation:

### Analyzation of Column - Branch:
![Output](o15.png)
### Analyzation of Column - Customer type:
![Output](o16.png)
### Analyzation of Column - Gender:
![Output](o17.png)
### Analyzation of Column - Payment:
![Output](o18.png)
### Analyzation of Column - City:
![Output](o19.png)
### Analyzation of Column - Product line:
![Output](o20.png)
### Analyzation of Column - Quantity:
![Output](o21.png)

### Non Categorical Data- Distributive Plot:

### Column-Total:
![Output](o22.png)
### Column-Unit price:
![Output](o23.png)
### Column-Rating:
![Output](o24.png)
### Column-cogs:
![Output](o25.png)
### Column-gross income:
![Output](o26.png)
### Comparing Column "Quantity" with Column "Gender":
![Output](o27.png)
### Comparing Column "Quantity" with Column "City":
![Output](o28.png)
### Comparing Column "Customer type" with Column "Branch":
![Output](o29.png)
### Comparing Column "Gender" with Column "Payment":
![Output](o30.png)
### Comparing Column "City" with Column "Quantity":
![Output](o31.png)

### Categorical Data - Bivariate Graphical:

### Comparing Columns "Branch" and "Customer type":
![Output](o32.png)
### Comparing Columns "Gender" and "Customer type":
![Output](o33.png)
### Comparing Columns "Quantity" and "Gender":
![Output](o34.png)
### Comparing Columns "Customer type" and "Product line":
![Output](o35.png)
### Comparing Columns "Gender" and "Payment":
![Output](o36.png)
### Comparing Columns "City" and "Payment":
![Output](o37.png)
### Comparing Columns "Product line" and "City":
![Output](o38.png)
### Comparing Columns "Quantity" and "Product line":
![Output](o39.png)
### Comparing Columns "Branch" and "Quantity":
![Output](o40.png)
### Comparing Columns "Payment" and "Product line":
![Output](o41.png)

### Statistical Method - Cross tabulation:

### Cross Tab of "Branch" and "Customer type":
![Output](o42.png)
### Cross Tab of "Customer type" and "Gender":
![Output](o43.png)
### Cross Tab of "Gender" and "Payment":
![Output](o44.png)
### Cross Tab of "City" and "Product line":
![Output](o45.png)
### Cross Tab of "Product line" and "Customer type":
![Output](o46.png)
### Cross Tab of "Quantity" and "Product line":
![Output](o47.png)

### Correlation of columns:

### Correlation of columns in Initial DataFrame(Before removing Outliers): 
![Output](o48.png)
### Graphical Representation to view correlation:
![Output](o49.png)
### Correlation of columns in Final DataFrame(After removing Outliers): 
![Output](o50.png)
### Graphical Representation to view correlation:
![Output](o51.png)

## Result:
Data cleaning and Outlier removal has been carried out in the given DataFrame.EDA is sucessfully performed in the given dataset.
