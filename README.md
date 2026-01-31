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
```
import pandas as pd  
df=pd.read_csv("SAMPLEIDS.csv")
df
```
<img width="765" height="668" alt="image" src="https://github.com/user-attachments/assets/fdcb6a99-a118-4929-b903-a17baa8adff5" />

```
df.head()
```

<img width="746" height="179" alt="image" src="https://github.com/user-attachments/assets/055f1fda-d9d7-4e34-92f1-a6734559be7f" />

```
df.tail()
```
<img width="752" height="183" alt="image" src="https://github.com/user-attachments/assets/dffc16ba-7ab6-497b-8aaf-8b48280b4911" />

```
df.info()
```
<img width="293" height="320" alt="image" src="https://github.com/user-attachments/assets/4181641e-4488-4734-886d-e391d515e86d" />

```
df.describe()
```

<img width="700" height="271" alt="image" src="https://github.com/user-attachments/assets/4c977183-baaf-4923-8aa3-c46265507aea" />

```
df.isnull().sum()
```

<img width="109" height="419" alt="image" src="https://github.com/user-attachments/assets/c791df4b-e2b2-4556-9ab2-fc5b94160fb7" />

```
df.isnull().any()
```

<img width="135" height="421" alt="image" src="https://github.com/user-attachments/assets/0ad5020f-3de5-4547-8c14-9711508f4d71" />

```
df.dropna()
```
<img width="761" height="421" alt="image" src="https://github.com/user-attachments/assets/3d548c5d-a37d-46db-9b84-7a08e6686c86" />

```
df.fillna(0)
```
<img width="769" height="660" alt="image" src="https://github.com/user-attachments/assets/d16b4621-1d41-476d-906f-af98af062601" />

```
df.fillna(method='ffill')
```

<img width="1245" height="684" alt="image" src="https://github.com/user-attachments/assets/7afc56eb-5d5d-46d0-821a-47dc78006e56" />

```
df.fillna({'GENDER':'MALE','NAME':'SRI'})
```
<img width="771" height="660" alt="image" src="https://github.com/user-attachments/assets/a0aebf65-5b42-4c9e-9e95-a05e3109d142" />

```
ir=pd.read_csv("iris.csv")
ir
```

<img width="493" height="390" alt="image" src="https://github.com/user-attachments/assets/d019e255-aed1-407a-a5ef-294cd2e20d54" />

```
ir.describe()
```

<img width="450" height="277" alt="image" src="https://github.com/user-attachments/assets/5bc5952c-04f5-4f63-9b82-35b8f36abda5" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

<img width="508" height="434" alt="image" src="https://github.com/user-attachments/assets/56ddf13c-d9fc-4a8d-a1d2-ad9d460417a5" />

```
Q1=ir.sepal_width.quantile(0.25)
Q3=ir.sepal_width.quantile(0.75)
(IQR)=Q3-Q1
print(IQR)
```

<img width="58" height="27" alt="image" src="https://github.com/user-attachments/assets/8a06acbc-6a97-42dd-85bc-2c1c01c4384f" />

```
ran=ir[((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']
```

<img width="136" height="200" alt="image" src="https://github.com/user-attachments/assets/b6959795-2bdb-47c5-ae35-925abc89c4ef" />

```
ran=ir[~((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']
```

<img width="163" height="428" alt="image" src="https://github.com/user-attachments/assets/b965fcc4-7963-43ca-81f2-5c1e8680d44c" />

```
sns.boxplot(x='sepal_width',data=ran)
```

<img width="502" height="433" alt="image" src="https://github.com/user-attachments/assets/18553315-559b-489d-9403-d713806c20ed" />

```
import numpy as np
import scipy.stats as stats
```

```
z=np.abs(stats.zscore(ir['petal_length']))
z
```

<img width="501" height="500" alt="image" src="https://github.com/user-attachments/assets/f7c45841-3bba-45af-bb0d-5b1ae0b068fe" />

```
ir1=ir[z<3]
ir1
```
<img width="500" height="380" alt="image" src="https://github.com/user-attachments/assets/f2ff67de-2f1c-4abe-9c1f-b902ac5492f7" />


 <h2 align="center"><u>PROGRAM END</u></h2>




# Result

Thus, the given dataset was successfully read and cleaned.
Missing values were identified and handled using different techniques such as removal, replacement, and forward fill.
Outliers were detected and removed using the Interquartile Range (IQR) and Z-Score methods.
The cleaned data obtained is accurate, consistent, and suitable for further analysis.

<img width="1000" height="110" alt="image" src="https://github.com/user-attachments/assets/778d1bc4-0c0d-4492-8c58-a9c672c0fcdf" />

