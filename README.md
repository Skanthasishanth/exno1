# Exno:1

Data Cleaning Process and Outliers Detection & Removal

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation

Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect , incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data , but rather finding a way to maximize datasets accuracy without necessarily deleting the information. An Outlier is a data item/object that deviates significantly from the rest of the (so-called normal) objects. Identifying outliers is important in statistics and data analysis because they can have a significant impact on the results of statistical analyses.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# 1) Read and display DataFrame
```
import pandas as pd
df=pd.read_csv('/content/SAMPLEIDS.csv')
df
```
## OUTPUT:

![Op1-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/54a175d9-f75c-46d4-aa34-9805f8756ed1)

## 2) Display head
```
df.head()
```
## OUTPUT:

![Op2-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/38ac9560-4fdc-41e8-803b-b54fc2f2d1e6)


## 3) Display tail
```
df.tail()
```
## OUTPUT:

![Op3-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/3f801907-b3d6-41a6-aab9-c8d6f4bd8f13)


## 4) Info of dataframe
```
df.info()
```
## OUTPUT:

![Op4-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/f61ec320-7527-432e-b9b5-79c8b4a7fb6d)


## 5) Describe about the dataframe
```
df.describe()
```
## OUTPUT:


![Op5-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/559fd39d-c59f-44af-8d6e-a2a55741254e)



## 6) Shape of the dataframe
```
df.shape
```
## OUTPUT:


![Op6-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/84671999-f54c-400b-8e3c-5644719e54ce)



## 7) Checking tha NUll values
```
df.isnull().sum()
```
## OUTPUT:

![Op7-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/99699853-0572-4272-bb88-1b40f503c48a)


## 8) Drop the Null values
```
x=df.dropna(how='any')
x
```
## OUTPUT:


![Op8-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/961535d6-c004-42de-8748-867eaf3f6eff)



## 9) Drop the Null values in Total
```
tot=df.dropna(subset=['TOTAL'],how='any')
tot
```
## OUTPUT:


![Op9-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/4ba28b9a-e63b-4929-bdd2-02e9f2dfb3f6)


## 10) FIll the Null values
```
df.fillna(0)
```
## OUTPUT:

![Op10-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/28e88a38-84f4-4a20-881a-c98ee5096570)


## 11) Finding the mean value
```
mn=df.TOTAL.mean()
mn
```
## OUTPUT:

![Op11-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/38e149f1-5a01-45d8-b331-490f5e9da6d5)


## 12) Final output
```
for x in df.index:
  if df.loc[x,"AVG"]>100:
    df.drop(x,inplace=True)
df
```
## OUTPUT:

![Op12-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/e40e418b-b08e-43bf-a3c9-f758743e10c1)


## 13) Outlier detection and removal
```Python
import pandas as pd
import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
dff=pd.DataFrame(age)
dff
```
## OUTPUT:

![Op13-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/e85ddba5-3ed0-46f6-bf22-34f76c627b83)


## 14) Boxplot
```Python
dsf=sns.boxplot(dff)
```
## OUTPUT:


![Op14-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/3899895b-e337-4b4d-86eb-e81e1102b475)


## 15) Scatterplot
```Python
dsf=sns.scatterplot(dff)
```
## OUTPUT:

![Op15-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/916dfb0c-3e2e-483c-be9a-758ce462f08c)



## 16) IQR
```Python
q1=dff.quantile(0.25)
q2=dff.quantile(0.5)
q3=dff.quantile(0.75)
iqr=q3-q1
iqr
```
## OUTPUT:

![Op16-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/b495843e-d90a-42a0-b88d-385cc2744db0)


## 17) Checking the high and low value
```Python
low=q1-1.5*iqr
low
high=q3+1.5*iqr
high
```
## OUTPUT:

![Op17-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/797b9ec8-cfe7-44f2-a527-f1a23b193efa)



![Op18-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/ba8dae3c-e928-4df6-86ee-d54c221c91b5)


## 18) Filtering outlier value
```Python
dff=dff[((dff>=low)&(dff<=high))]
dff
```
## OUTPUT:

![Op19-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/739e8ad5-7478-4fcd-84a6-96407bf41e0a)


### 19) Dropping the null value
```Python
dff.dropna()
```
## OUTPUT:

![Op20-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/8e6a8403-9f81-4ca4-ab60-75be02ba9aa8)


## 20) Box plotting after filtering outlier
```Python
sns.boxplot(data=dff)
```
## OUTPUT:

![Op21-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/5dc91e13-d598-46f0-94c8-3323940cfb41)


## 21) Z Score
```Python
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
data={'weight':[12,15,18,21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57,60,63,66,69,202,72, 75, 78, 81, 84, 232, 87, 90, 93,96,99,258]}
ds=pd.DataFrame(data)
ds
```
## OUTPUT:


![Op22-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/6269ca2a-f469-4614-a261-69c0e8a8f0be)


## 22) Z Score
```Python
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
data={'weight':[12,15,18,21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57,60,63,66,69,202,72, 75, 78, 81, 84, 232, 87, 90, 93,96,99,258]}
ds=pd.DataFrame(data)
ds
```
## OUTPUT:


![Op23-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/7d6d2ee0-9e0c-4ef4-bca4-b00af7d18f5f)


## 23) Z Score
```Python
sns.boxplot(data=ds)
```
## OUTPUT:

![Op24-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/b1e47e13-7a81-4c3d-b638-58caf6431d1b)



## 24) Z Score
```Python
z=np.abs(stats.zscore(ds))
z
```
## OUTPUT:

![Op25-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/b9fcd57a-d8fa-4b7d-8e39-0b75b913ac42)


## 25) Z score 
```Python
print(ds[z['weight']>3])
```
## OUTPUT:

![Op26-ds1](https://github.com/Skanthasishanth/exno1/assets/118298456/21e9d1cc-ca18-4ba9-9804-0ca0b2cae4ec)


## Result
Hence the data was cleaned , outliers were detected and removed.
