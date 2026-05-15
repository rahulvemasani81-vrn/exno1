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

#### DEVELPOED BY : RAHUL  
#### REG NO : 212225230294
```
     import pandas as pd
     df=pd.read_csv('D:Data_set (1).csv')
     print(df)
     print(data)
```

<img width="609" height="661" alt="591729354-6733c7cc-81bb-4700-a842-1323abe8b2d8" src="https://github.com/user-attachments/assets/43ad292b-ba53-442c-877a-1ca469a23570" />


```
df.describe()
```

<img width="609" height="236" alt="591729758-cbf4f1cb-e026-4c4e-a87e-868204ba7cda" src="https://github.com/user-attachments/assets/55c189a3-2be4-48ec-a144-00a1a676c44e" />


```
df=pd.DataFrame(df)
print(df.isnull())
```

<img width="672" height="449" alt="591730484-da53dcea-8590-4184-8fe4-4df73d96477d" src="https://github.com/user-attachments/assets/995cd1a8-6383-4beb-9622-482582d671ec" />

```
import pandas as pd
data = pd.read_csv("C:/Users/acer/Downloads/Data_set (1).csv")
df = pd.DataFrame(data)
dfd = df.dropna()
print("AFTER DROPNA")
print(dfd)
```

<img width="702" height="674" alt="591731496-a95bfb3b-c33f-4d42-8274-54639f027f28" src="https://github.com/user-attachments/assets/e370ca60-2255-4bfa-b666-485b28d2c1ff" />

```
dfd = df.dropna(axis=1)

print("AFTER DROPNA")
print(dfd)
```

<img width="471" height="254" alt="591732561-b1362da2-f70f-4445-9f33-3b9fb8bf3f58" src="https://github.com/user-attachments/assets/c3c48c0f-e707-416a-b74c-3295c4a1855f" />


```
dfd=df.dropna(axis=1,inplace=True)
```

<img width="635" height="59" alt="591734021-190597ac-f545-4e6c-88af-f5766dc1e90c" src="https://github.com/user-attachments/assets/d7c895c1-862a-4938-bdd3-715a83102f08" />


```
print("AFTER DROPNA") dfd=df.dropna(axis=0)

print("AFTER DROPNA")

print(dfd)
```

<img width="426" height="264" alt="591745780-48b5e4e7-0a22-47aa-bc09-da382857da31" src="https://github.com/user-attachments/assets/779ec8a2-7c1f-425f-9fa7-5c4ba290553e" />
<img width="806" height="397" alt="591745569-c159e5f7-a818-4ab7-8bb0-11725b04da7f" src="https://github.com/user-attachments/assets/bea62111-5e92-4219-ad5a-b57aaff99c48" />


```
import pandas as pd

# Read the dataset
data = pd.read_csv("C:/Users/acer/Downloads/Data_set (1).csv")

# Convert into DataFrame
df = pd.DataFrame(data)

# Fill missing values using forward fill method
dfd = df.fillna(method="ffill")

# Display output
print("AFTER FILLNA")

print(dfd)
```

<img width="698" height="671" alt="591760529-2a8c1655-8104-44f0-9ead-0c02d3331792" src="https://github.com/user-attachments/assets/ddd258f1-1bb0-41e5-b75a-9758ddcf659d" />


```
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Read the dataset
data = pd.read_csv("C:/Users/acer/Downloads/iris.csv")

# Convert into DataFrame
df = pd.DataFrame(data)

# Display dataset
print(df)

# Select columns
x = df["petal_length"]
y = df["sepal_length"]

# Create histogram
plt.hist(x)

# Display graph
plt.show()

# Create another histogram
plt.hist(y)

# Display graph
plt.show()
```

<img width="565" height="882" alt="591761201-288267a3-86a5-48f0-9230-f4bddf9fa28a" src="https://github.com/user-attachments/assets/79015997-7cca-49b0-bbd1-8678aa37c6cc" />

```
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Read dataset
data = pd.read_csv("iris.csv")

# Convert into DataFrame
df = pd.DataFrame(data)

# Display dataset
print(df)

# Select columns
x = df["petal_length"]
y = df["sepal_length"]

# Label axes
plt.xlabel('X-axis')
plt.ylabel('Y-axis')

# Plot graph
plt.plot(x, y)

# Display graph
plt.show()
```

<img width="604" height="580" alt="591762240-d7f34551-63ca-4dec-a2e3-46d691ff0bac" src="https://github.com/user-attachments/assets/449af97c-d75d-4390-8e33-e7f1a6ceb53d" />


```
 import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Read dataset
data = pd.read_csv("iris.csv")

# Convert into DataFrame
df = pd.DataFrame(data)

# Display dataset
print(df)

# Create boxplot
dff = plt.boxplot(df["petal_width"])

# Display graph
plt.show()

print(dff)

```

<img width="916" height="643" alt="591763228-a92cd39d-4c24-4b2e-aa39-a63a3809dc7f" src="https://github.com/user-attachments/assets/68028a05-72a8-4982-ab57-ea4f9a9d5e3e" />


### IQR(Inter Quartile Range)

```
\import pandas as pd
import numpy as np
from scipy import stats

data = pd.read_csv("iris.csv")

df = pd.DataFrame(data)

z_scores = np.abs(stats.zscore(df.select_dtypes(include=[np.number])))

df_cleaned = df[(z_scores < 3).all(axis=1)]

print(df_cleaned)
```

<img width="608" height="217" alt="591764248-a39e373a-7ebf-494c-8277-f4e73ffa823a" src="https://github.com/user-attachments/assets/35254128-e152-4b69-960f-a3314782ab75" />


```
import pandas as pd
import numpy as np

data = pd.read_csv("C:/Users/acer/Downloads/iris (1).csv")
df = pd.DataFrame(data)

Q1 = df["sepal_width"].quantile(0.25)

Q3 = df["sepal_width"].quantile(0.75)

IQR = Q3 - Q1

lower_bound = Q1 - 1.5 * IQR

upper_bound = Q3 + 1.5 * IQR

print("The Original DataSet")

print(df)

outliers = df[
    (df['sepal_width'] < lower_bound) |
    (df['sepal_width'] > upper_bound)
]

print("The Outliers")

print(outliers)

df_clean = df[
    (df['sepal_width'] >= lower_bound) &
    (df['sepal_width'] <= upper_bound)
]

print("The Dataset after removing the outliers")

print(df_clean)
```

<img width="605" height="521" alt="591764949-82cc528f-f488-4a40-b668-53ca733a4e85" src="https://github.com/user-attachments/assets/4fcea3c0-da7d-45de-9fd4-e37375763659" />

Result
THUS DATA CLEANING IS PERFORMED
