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

import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df

<img width="1117" height="954" alt="image" src="https://github.com/user-attachments/assets/2931fabd-69b5-43d3-83ce-946eb987b220" />

df.head()

<img width="1085" height="273" alt="image" src="https://github.com/user-attachments/assets/c9db64a3-ee66-47c7-bdde-6484156b60bb" />

df.tail()

<img width="1097" height="270" alt="image" src="https://github.com/user-attachments/assets/3491d51f-54e1-45a3-93a4-3e710c862519" />

df.isnull()

<img width="890" height="944" alt="image" src="https://github.com/user-attachments/assets/8c6dd5e2-49ef-4186-bcee-a5ca9c3e944f" />

df.notnull()

<img width="878" height="945" alt="image" src="https://github.com/user-attachments/assets/0868dbd0-503d-40f7-8629-9337fb102428" />

df.isnull().sum()

<img width="176" height="634" alt="image" src="https://github.com/user-attachments/assets/8b062c7e-1d87-4418-9e7d-e1d31ef68f6a" />

df.notnull().sum()

<img width="175" height="626" alt="image" src="https://github.com/user-attachments/assets/ea09a6f2-48d1-48f4-9630-a9bf5a57426b" />

df.isnull().any()

<img width="199" height="629" alt="image" src="https://github.com/user-attachments/assets/62f0a5f5-66f1-4c84-8f71-deca4b91360d" />

df.dropna(axis=0)

<img width="1103" height="608" alt="image" src="https://github.com/user-attachments/assets/264d3775-fcd8-4869-9f35-402d7d787b04" />

df.dropna(axis=1)

<img width="304" height="941" alt="image" src="https://github.com/user-attachments/assets/ff9fbf4e-60fb-419f-9713-4e8f2376c722" />

df.fillna(0)

<img width="1108" height="952" alt="image" src="https://github.com/user-attachments/assets/e40f353d-a248-4abd-a8a8-610223f75299" />

df.fillna(method='ffill')

<img width="1119" height="947" alt="image" src="https://github.com/user-attachments/assets/e6c97dac-8d4d-454b-90a4-b678fc67e4cd" />

df.fillna(method='bfill')

<img width="1118" height="952" alt="image" src="https://github.com/user-attachments/assets/96ff843a-16b8-47b5-b02a-76e95ee6cafb" />

df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALLEE','M1':'82.0','M2':'81.0','M3':'90.0','M4':'56.6'})

<img width="1119" height="945" alt="image" src="https://github.com/user-attachments/assets/8af97e4e-4ba4-4543-ac6a-8dac80cd1220" />

import pandas as pd
ir=pd.read_csv("iris.csv")
ir

<img width="721" height="562" alt="image" src="https://github.com/user-attachments/assets/800a9923-9773-4b4d-af8b-db5c25030d6d" />

ir.describe()

<img width="637" height="393" alt="image" src="https://github.com/user-attachments/assets/29315b87-23c7-45a5-af12-110c3323e3de" />

import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)

<img width="750" height="630" alt="image" src="https://github.com/user-attachments/assets/fef2fb6c-a4e0-4598-83b6-d34d4c64384b" />

q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)

<img width="379" height="46" alt="image" src="https://github.com/user-attachments/assets/e9e427b4-8e2e-4d03-832a-04fd0623c527" />

rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']

<img width="228" height="282" alt="image" src="https://github.com/user-attachments/assets/e3a8cdfc-a24a-478c-bbe2-94a3822d4e88" />

derid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
derid['sepal_width']

<img width="283" height="629" alt="image" src="https://github.com/user-attachments/assets/647746a7-21a6-4b8d-bfb2-f307da479eb8" />

sns.boxplot(x='sepal_width',data=derid)

<img width="729" height="630" alt="image" src="https://github.com/user-attachments/assets/ff55f5c3-904b-45e2-a645-a941f545204e" />

import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("iris.csv")
dataset

<img width="719" height="575" alt="image" src="https://github.com/user-attachments/assets/ff10924c-5f6b-4fa4-ba9e-9d3c4bbd6fae" />

z=np.abs(stats.zscore(dataset['sepal_width']))
z

<img width="715" height="729" alt="image" src="https://github.com/user-attachments/assets/0cd9bc95-22ca-49eb-807e-02caa21803f9" />

dataset1=dataset[z<3]
dataset1

<img width="712" height="561" alt="image" src="https://github.com/user-attachments/assets/dcd5ecf0-c9e0-42fd-9cd6-0cb09dbfd1d1" />


# Result
The given data has been successfully read, cleaned by handling duplicates and missing values, and saved to a new file named cleaned_data.csv.
