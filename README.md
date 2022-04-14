# Ex-04-EDA
### AIM
To perform EDA on the given data set.

### Explanation
The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

### ALGORITHM
### STEP 1
Import the required packages(pandas,numpy,seaborn).

### STEP 2
Read and Load the Dataset.

### STEP 3
Remove the null values from the data and remove the outliers.

### STEP 4
Remove the non numerical data columns using drop() method.

### STEP 5:
returns object containing counts of unique values using (value_counts()).

### STEP 6:
Plot the counts in the form of Histogram or Bar Graph.

### STEP 7:
find the pairwise correlation of all columns in the dataframe(.corr()).

### STEP 8:
Save the final data set into the file.

### CODE :
```
Program 
Developed by:GAUTHAM M
Register no:212221230027

import pandas as pd
import numpy as np
import seaborn as sns
df=pd.read_csv("supermarket.csv")
df

#cleaning dataset
#checking for null values
df.isnull().sum()

#data is cleaned, proceed to remove outliers
#checking for outliers
df.boxplot()

#removing outliers
cols = ['Unit price','Quantity','Tax 5%','Total','cogs','gross margin percentage','gross income','Rating']
Q1 = df[cols].quantile(0.25)
Q3 = df[cols].quantile(0.75)
IQR = Q3 - Q1
df = df[~((df[cols] < (Q1 - 1.5 * IQR)) |(df[cols] > (Q3 + 1.5 * IQR))).any(axis=1)]
df
df.boxplot()

#outliers removed
# performing data analysis
# performing data analysis
#statistical analysis for single data group
df['Branch'].value_counts()
df['City'].value_counts()
df['Customer type'].value_counts()
df['Gender'].value_counts()
df['Product line'].value_counts()
df['Quantity'].value_counts()
df['Payment'].value_counts()

#statistical analysis for two data groups
pd.crosstab(df["Customer type"],df["Branch"])
pd.crosstab(df["Customer type"],df["City"])
pd.crosstab(df["Customer type"],df["Gender"])
pd.crosstab(df["Customer type"],df["Payment"])
pd.crosstab(df["Product line"],df["Quantity"])

#statistical analysis for multiple data groups
#analysing pairwise correlation of columns in dataset
df.corr()

#graphical analysis of categorical data--univariate
sns.countplot(x="Branch",data=df)
sns.countplot(x="City",data=df)
sns.countplot(x="Customer type",data=df)
sns.countplot(x="Payment",data=df)
sns.countplot(x="Gender",data=df)
sns.countplot(y="Product line",data=df)
sns.countplot(x="Quantity",data=df)

#graphical analysis of non-categorical data or data with multiple categories--univariate
sns.displot(df["Unit price"])
sns.displot(df["Tax 5%"])
sns.displot(df["cogs"])
sns.displot(df["gross income"])

#graphical analysis of categorical data--bivariate
sns.countplot(x="City",hue="Customer type",data=df)
sns.countplot(x="Branch",hue="Customer type",data=df)
sns.countplot(x="Gender",hue="Customer type",data=df)
sns.countplot(x="Payment",hue="Customer type",data=df)
sns.countplot(y="Product line",hue="Quantity",data=df)

#graphical analysis of non-categorical data or data with multiple categories--bivariate
sns.displot(df[df["City"]=='Yangon']["cogs"])
sns.displot(df[df["City"]=='Mandalay']["cogs"])
sns.displot(df[df["City"]=='Naypyitaw']["cogs"])

sns.displot(df[df["Product line"]=='Health and beauty']["Gender"])
sns.displot(df[df["Product line"]=='Electronic accessories']["Gender"])
sns.displot(df[df["Product line"]=='Home and lifestyle']["Gender"])
sns.displot(df[df["Product line"]=='Sports and travel']["Gender"])
sns.displot(df[df["Product line"]=='Food and beverages']["Gender"])
sns.displot(df[df["Product line"]=='Fashion accessories']["Gender"])

sns.displot(df[df["Gender"]=='Male']["gross income"])
sns.displot(df[df["Gender"]=='Female']["gross income"])

#Graphical representation of data--multivariate 
df.drop('gross margin percentage',axis=1,inplace=True)
sns.heatmap(df.corr(),annot=True)
```
### OUPUT :
Original Data :
![image](https://user-images.githubusercontent.com/94810884/163436918-10bf35e8-c6c8-45ac-8896-937cc71cfae5.png)

Data Cleaning Process :
![image](https://user-images.githubusercontent.com/94810884/163437071-5cf4ea8b-ae2e-430b-8af5-0a51786f1705.png)

Removing Outliers Process :
![image](https://user-images.githubusercontent.com/94810884/163437216-a0f49746-3952-4248-a710-d1188ab740d0.png)
![image](https://user-images.githubusercontent.com/94810884/163437610-8e014c38-f7f9-407d-ab8b-bc72b5ac6637.png)
![image](https://user-images.githubusercontent.com/94810884/163437745-21c341d4-8d60-4ece-80b7-c9a0ecb547d8.png)

### statistical analysis for single data group :
![image](https://user-images.githubusercontent.com/94810884/163438484-ae14b003-0da6-44da-bb65-0efaa71daebb.png)
![image](https://user-images.githubusercontent.com/94810884/163438549-7cc1d08a-e76e-4f96-9309-ad22586e71ea.png)
![image](https://user-images.githubusercontent.com/94810884/163438601-5c09a291-8ccb-4a0a-a620-0056c77d085c.png)
![image](https://user-images.githubusercontent.com/94810884/163438651-b1c0e8b6-9ff3-49f2-b474-2fe87555906c.png)
![image](https://user-images.githubusercontent.com/94810884/163438693-8f8b2df0-7def-4910-a9eb-aa90e414adc4.png)
![image](https://user-images.githubusercontent.com/94810884/163438740-1f8024fc-857e-4e91-8a53-f6d98700645c.png)
![image](https://user-images.githubusercontent.com/94810884/163438788-9cc3ab0c-a6fc-49d5-b9a7-a10ed2e1642b.png)

### statistical analysis for two data groups :
![image](https://user-images.githubusercontent.com/94810884/163439480-81c17522-e4d8-46da-be04-4728f5864cf7.png)
![image](https://user-images.githubusercontent.com/94810884/163439602-6d61ddc0-1021-48a8-92f2-1d4fec452d4e.png)




