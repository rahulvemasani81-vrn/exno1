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
            
## Data Cleaning

#### DEVELPOED BY : Saaru lakshmi.D
#### REG NO : 212223050040
```
import pandas as pd
data=pd.read_csv("SAMPLEIDS.csv")
data
```

<img width="820" height="632" alt="image" src="https://github.com/user-attachments/assets/ff3152b7-0823-4949-b635-276ad8fa1a44" />

```
data.head()

```

<img width="790" height="205" alt="image" src="https://github.com/user-attachments/assets/70aca704-601b-4741-b1ca-5a44b6b57278" />

```
data.tail()
```

<img width="671" height="157" alt="image" src="https://github.com/user-attachments/assets/465c5e69-71c0-4b34-acfe-2b0c16c40200" />

```
data.isnull()
```

<img width="575" height="520" alt="image" src="https://github.com/user-attachments/assets/010e9b38-5f42-4dc5-9082-b85fdbccebb6" />

```
data.isnull().sum()
```

<img width="122" height="217" alt="image" src="https://github.com/user-attachments/assets/07744a83-e508-404a-a926-605e0257457f" />

```
data.isnull().any()
```

<img width="132" height="227" alt="image" src="https://github.com/user-attachments/assets/40830cc6-8aa8-47a4-af44-15503a20ae67" />

```
data.dropna()
```

<img width="697" height="342" alt="image" src="https://github.com/user-attachments/assets/716e08fa-6b5a-4e08-b5f1-0d4724b581ee" />

```
data.fillna(0)

```

<img width="675" height="522" alt="image" src="https://github.com/user-attachments/assets/b07a3e94-d5ab-40bf-9d4f-f44c0415a098" />

```
data.fillna(method='ffill')
```

<img width="666" height="526" alt="image" src="https://github.com/user-attachments/assets/9de42f74-319a-4215-922d-4e0ea62203bf" />

```
data.fillna(method='bfill')
```

<img width="687" height="523" alt="image" src="https://github.com/user-attachments/assets/2a78ba3b-e773-4d4c-9454-86ee7167ce23" />

```
 data.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```

<img width="668" height="512" alt="image" src="https://github.com/user-attachments/assets/dd936d34-4498-4595-96a8-9bfcfe779ce4" />

### IQR(Inter Quartile Range)

```
import pandas as pd
ir=pd.read_csv("iris.csv")
ir
```

<img width="416" height="316" alt="image" src="https://github.com/user-attachments/assets/66304e97-df9f-44b4-8b15-dab4e70bf550" />

```
ir.describe()
```

<img width="362" height="230" alt="image" src="https://github.com/user-attachments/assets/523bf6aa-5b19-4c41-802f-cabbc630c825" />

```
ir.shape
```

<img width="87" height="42" alt="image" src="https://github.com/user-attachments/assets/59a33e96-7bc8-4cf4-b6f9-f4fce9f9bff3" />

```
ir.info()
```

<img width="312" height="196" alt="image" src="https://github.com/user-attachments/assets/94af2401-5109-46db-a355-e14fd8eaf0cf" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

<img width="496" height="428" alt="image" src="https://github.com/user-attachments/assets/05dacc6d-713f-4f92-8027-b939bbf0302b" />

```
 q1=ir.sepal_width.quantile(0.25)
 q3=ir.sepal_width.quantile(0.75)
 iqr=q3-q1
 print(iqr)
```

<img width="88" height="33" alt="image" src="https://github.com/user-attachments/assets/9ad5bf7f-c2fa-464f-b318-9777f5743cd1" />

```
 out=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
 out['sepal_width']

```

<img width="292" height="88" alt="image" src="https://github.com/user-attachments/assets/49c7a474-18de-4536-af68-08b00d712b74" />

```
 nor=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
 nor['sepal_width']
```

<img width="383" height="205" alt="image" src="https://github.com/user-attachments/assets/64b1869b-79aa-41fe-a39e-7bedcfbcb763" />

```
sns.boxplot(x='sepal_width',data=nor)
```

<img width="531" height="440" alt="image" src="https://github.com/user-attachments/assets/6331d207-4824-44c7-a0e4-497a1a10ae85" />

### Z-SCORE

```
import numpy as np
import pandas as pd
df=pd.read_csv("heights.csv")
df
```

<img width="177" height="361" alt="image" src="https://github.com/user-attachments/assets/cfc2a520-0c69-4f46-a97b-b603453fc681" />

```
import scipy.stats as stats
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr

```

<img width="166" height="41" alt="image" src="https://github.com/user-attachments/assets/77c50179-11e6-43bf-838e-89c9bc47baf5" />

```
low = q1 - 1.5*iqr
print(low)
high = q3 + 1.5*iqr
print(high)
```

<img width="147" height="47" alt="image" src="https://github.com/user-attachments/assets/3f4d3793-91a5-4bc9-8aa1-ef6393cea8e2" />

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```

<img width="147" height="308" alt="image" src="https://github.com/user-attachments/assets/ba2cfbfc-ddd9-499d-aeb7-2a44f00724fa" />

```
z = np.abs(stats.zscore(df['height']))
z
```

<img width="270" height="246" alt="image" src="https://github.com/user-attachments/assets/7ce477e6-e8c8-4908-9dd9-250c2119d535" />

```
df1 = df[z<3]
df1
```

<img width="191" height="336" alt="image" src="https://github.com/user-attachments/assets/94f0399e-1f9d-4f33-b6d2-b7730079e1a2" />

## Result
    
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
