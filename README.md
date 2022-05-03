# Ex-04-EDA

## AIM:
To Perform the EDA method for the given data set.

## EXPLANATION :
The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM:
 ### Step1:
Import the required packages(pandas,numpy,seaborn).

### Step2:
Read and Load the Dataset.

 ### Step3:
Remove the null values from the data and remove the outliers ,then use drop() to remove non numnerical datas.

### Step4:
Returns object containing counts of unique values using (value_counts()) and plot the counts in Bargraph or Histogram.

### Step5:
Finally find the pairwise correlation of all columns in the dataframe(.corr()) and save the final data set into the file.

## CODE:
```
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
df=pd.read_csv("supermarket.csv")
print(df)
df.head()
df.info()
df.isnull().sum()
df.boxplot()
cols = ['Tax 5%', 'Total','gross margin percentage','gross income']
Q1 = df[cols].quantile(0.25)
Q3 = df[cols].quantile(0.75)
IQR = Q3 - Q1
df = df[~((df[cols] < (Q1 - 1.5 * IQR)) |(df[cols] > (Q3 + 1.5 * IQR))).any(axis=1)]
df
df["City"].value_counts()
df["Customer type"].value_counts()
df["Gender"].value_counts()
df["Quantity"].value_counts()
df["Payment"].value_counts()
plt.figure(dpi=125)
sns.countplot(y ='Product line', hue = "City", data = df) 
plt.xlabel('Count')
plt.show()
sns.boxenplot(y = 'Product line', x = 'Quantity', data=df )
sns.countplot(x="Gender",hue="Product line",data=df)
sns.countplot(x="Customer type",hue="City",data=df)
df.corr()
sns.heatmap(df.corr(),annot=True)
```
## OUTPUT:
![git](./out1.png)
![git](./out2.png)
![git](./out3.png)
![git](./out4.png)
![git](./out5.png)
![git](./out6.png)
## RESULT:
Thus the given dataset is analysed using EDA method.