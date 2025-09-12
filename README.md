# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```py
import pandas as pd
import numpy as np
import seaborn as sns
data=pd.read_csv("SAMPLEIDS.csv")
data
```
<img width="887" height="573" alt="image" src="https://github.com/user-attachments/assets/c87090d9-90a8-4a13-9572-0f8369bb255b" />


```py
data.head(5)
```
<img width="811" height="180" alt="image" src="https://github.com/user-attachments/assets/9cb34879-c3d2-4d4c-ab77-fdc82b432959" />


```py
data.tail()
```
<img width="847" height="182" alt="image" src="https://github.com/user-attachments/assets/27c1e8e8-97d5-431b-b4a1-03ae51df3937" />


```py
data.isnull()
```
<img width="863" height="604" alt="image" src="https://github.com/user-attachments/assets/3a0f873c-1b31-41f8-a2b4-29c1ea6ccc23" />


```py
data.notnull()
```
<img width="247" height="232" alt="image" src="https://github.com/user-attachments/assets/c2a197c3-4e0e-4722-9501-b02cb620a7ea" />


```py
data.isnull().sum()
```
<img width="829" height="595" alt="image" src="https://github.com/user-attachments/assets/9cc53d4f-f724-4472-baf7-413032d8d74b" />


```py
data.isnull().any()
```
<img width="265" height="252" alt="image" src="https://github.com/user-attachments/assets/72847e29-16e2-4470-97a8-2bfc5489a4be" />

```py
data.dropna(axis=0)
```
<img width="454" height="593" alt="image" src="https://github.com/user-attachments/assets/a9039df9-9e1d-49c8-b34c-6b286f285010" />


```py
data.dropna(axis=1)
```
<img width="1004" height="399" alt="image" src="https://github.com/user-attachments/assets/227d5ed3-db60-40e1-94e7-9b3c46d72107" />


```py
data.fillna(0)
```
<img width="955" height="601" alt="image" src="https://github.com/user-attachments/assets/2abb949b-f903-4c6d-9186-52989a4d1c51" />


```py
data.fillna(method='ffill')
```
<img width="882" height="594" alt="image" src="https://github.com/user-attachments/assets/db207695-0e35-40d2-b6a6-ef236754f13a" />


```py
data.fillna(method='bfill')
```
<img width="1018" height="603" alt="image" src="https://github.com/user-attachments/assets/00b92834-0f19-4631-ba0a-e674c0fadcaf" />


```py
data.fillna({"REGNO":23006360,"NAME":"SAJEN"})
```
<img width="976" height="597" alt="image" src="https://github.com/user-attachments/assets/c0361c9e-2e3f-4a5f-a93e-e3279d8268bf" />


```py
ir=pd.read_csv("iris.csv")
ir
```
<img width="631" height="352" alt="image" src="https://github.com/user-attachments/assets/2f9a30c1-a28f-4a68-a310-05277baa4272" />


```py
ir.describe()
```
<img width="577" height="267" alt="image" src="https://github.com/user-attachments/assets/7f348640-cae8-432d-9b4b-78a4e3a48473" />


```py
sns.boxplot(x="sepal_width",data=ir)
```
<img width="699" height="472" alt="image" src="https://github.com/user-attachments/assets/051bc8bd-94fc-4c35-8c97-6c457670a381" />


```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
<img width="71" height="31" alt="image" src="https://github.com/user-attachments/assets/c06bb51d-89a8-4e97-b960-cfd51af97fea" />


```py
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
<img width="441" height="101" alt="image" src="https://github.com/user-attachments/assets/4726a649-5dc3-42b7-afa4-a2b5c43685e9" />


```py
delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
delid
```
<img width="648" height="380" alt="image" src="https://github.com/user-attachments/assets/0cdc4f76-5ea0-4163-8850-81dfdad1d827" />


```py
sns.boxplot(x='sepal_width',data=delid)
```
<img width="689" height="472" alt="image" src="https://github.com/user-attachments/assets/d74dfb8b-b6eb-4e86-ad30-973b16423c5e" />


```py
from scipy import stats
z=np.abs(stats.zscore(ir['sepal_width']))
z
```
<img width="514" height="213" alt="image" src="https://github.com/user-attachments/assets/394f5eda-b68d-4f8c-b5dc-c921ac486d86" />


```py
ir1=ir[z<3]
ir1
```
<img width="619" height="370" alt="image" src="https://github.com/user-attachments/assets/411402de-61ad-4693-aba4-12ebc1788117" />


# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
