# Ex. 1   Data Cleaning and Outlier Detection & Removal</h1>


## AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

## Explanation
 Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

## Algorithm
### STEP 1 :
Read the given Data

### STEP 2 :
Get the information about the data

### STEP 3 
Remove the null values from the data

### STEP 4
Save the Clean data to the file

### STEP 5
Remove outliers using IQR

### STEP 6
Use zscore of to remove outliers

## Coding and Outputs

```py
import pandas as pd
import numpy as np
import seaborn as sns
import os 
df=pd.read_csv("SAMPLEIDS.csv")
df
```
![1](https://github.com/user-attachments/assets/b542f729-e610-4c98-a8be-95298ce2ef63)


```py
df.isnull().sum()

```

![2](https://github.com/user-attachments/assets/d54c8cb3-9ef6-4ccc-98f4-2a23a9a8a135)




```py
df.isnull().any()
```
![3](https://github.com/user-attachments/assets/67da7123-3cbb-405b-899f-2f865bd90ef5)


```py
df.dropna()
```

![4](https://github.com/user-attachments/assets/15702c04-b806-4b0d-a9d4-5f9981e2c7d8)


```py
df.fillna(0)
```

![5](https://github.com/user-attachments/assets/c66bb7e9-f9b1-4dd4-b2c8-83b95d3b3603)

```py
df.fillna(method = 'ffill')
```
![6](https://github.com/user-attachments/assets/b401c42a-48ba-4be2-99c5-d14883553dd8)

```py

df.fillna(method = 'bfill')
```

![7](https://github.com/user-attachments/assets/83c5b807-9e17-4cf0-8d6e-c0922008de78)


```py
df_dropped = df.dropna()
df_dropped
```

![8](https://github.com/user-attachments/assets/95d3fb3e-1845-4c15-9d5f-34b7a46c012c)


```py
df.fillna({'GENDER':'FEMALE','NAME':'PRIYU','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![9](https://github.com/user-attachments/assets/a145008a-15ba-4c1e-a55d-11f4c917025c)


<hr><hr>


```py
import pandas as pd
```

```py
ir=pd.read_csv('iris.csv')
ir
```
![10](https://github.com/user-attachments/assets/aabb369f-d860-4b65-bf0d-ccf50383257c)


```py
ir.describe()
```

```py
import seaborn as sns
```![11](https://github.com/user-attachments/assets/4b0beb34-0062-4378-9882-b921aaf279d7)


```py

sns.boxplot(x='sepal_width',data=ir)
```


![12](https://github.com/user-attachments/assets/bc183937-6996-4577-856f-82c4a529cd46)



```py
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```

![13](https://github.com/user-attachments/assets/23369bcd-05fe-4f85-ab90-e669f014f443)


```py

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```

![14](https://github.com/user-attachments/assets/e967c31f-d30e-4618-8501-4a38401f345f)


```py
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![15](https://github.com/user-attachments/assets/cf005d9f-9a93-4b52-bef4-d4f663648fbe)

```py
sns.boxplot(x='sepal_width',data=delid)
```
![16](https://github.com/user-attachments/assets/fd5bb271-1227-4bea-a3e9-ecc02a7a509a)


<hr><hr>


```py
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
```
```py
dataset=pd.read_csv("heights.csv")
dataset
```
![17](https://github.com/user-attachments/assets/f6c817f9-2be7-401e-ae90-f3f1581e8d31)



```py
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```

```py
iqr = q3-q1
iqr
```

![18](https://github.com/user-attachments/assets/6ccb16a0-6741-4ad1-b129-7b9f103d9c20)



```py
low = q1 - 1.5*iqr
low
```

![19](https://github.com/user-attachments/assets/9559e502-adc8-46e5-b0fa-5e36c0589a7c)


```py
high = q3 + 1.5*iqr
high
```

![20](https://github.com/user-attachments/assets/0f0841fa-b15d-4be2-9772-9c61969dd883)



```py
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```

![21](https://github.com/user-attachments/assets/972b53f7-7d11-42f9-8435-aed66fde338b)


```py
z = np.abs(stats.zscore(df['height']))
z
```
![22](https://github.com/user-attachments/assets/f915dcba-c2f9-45dd-8be1-a8f7769c7f3e)


```py
df1 = df[z<3]
df1
```

![23](https://github.com/user-attachments/assets/965e9a1b-a0a8-4f4e-a987-28579d1a0a66)


<hr>

## Result
Hence the data was cleaned , outliers were detected and removed.
