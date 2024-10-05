## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:

### IMPORT THE PANDAS LIBRARY AND READ THE CSV FILE:
```PYTHON
import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df
```
### OUTPUT:
![image](https://github.com/user-attachments/assets/ea049370-9224-4a03-8e12-de5866a8dac9)

## PERFORMING THE ORDINAL ENCODER:
```PYTHON
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
```

### TRANSOFORMING THE CATEGORICAL DATA INTO ORDINAL FORM:
```PYTHON
pm=['Hot','Warm','Cold']

el=OrdinalEncoder(categories=[pm])

el.fit_transform(df[["ord_2"]])
```
### OUTPUT:
![image](https://github.com/user-attachments/assets/b48669ec-d1e9-4093-a986-e50ac1f0ee8b)

### TRANSFORMS THE COLUMN:
```PYTHON
df['bo2']=el.fit_transform(df[["ord_2"]])

df
```
### OUTPUT:
![image](https://github.com/user-attachments/assets/29b54693-1173-4eeb-8a69-4fb587d77ca9)

### CHANGE THE CATEGORICAL INTO NUMERICAL COLUN:
```PYTHON
df['ord_2']=el.fit_transform(df[["ord_2"]])

df
```
### OUTPUT:
![image](https://github.com/user-attachments/assets/9ba7cb65-61dd-4aad-a1f5-cf235d0f3dd8)

## PERFORMING THE ONEHOTENCODER:
```PYTHON
from sklearn.preprocessing import OneHotEncoder
```
```PYTHON
ohe=OneHotEncoder(sparse=False)
df2=df.copy()

df2
```
### OUTPUT:

![image](https://github.com/user-attachments/assets/43ea86d4-16ce-4b4d-8d89-a54aa9a0a937)

```PYTHON
enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))
enc
```

### OUTPUT:
![image](https://github.com/user-attachments/assets/c069be75-2df3-41b5-bc23-d48bd1dad4a9)

### ADDING THE ONEHOTENCODER DATA TRANSFORMED INTO THE ORIGINAL DATASET:
```PYTHON
df2=pd.concat([df2,enc],axis=1)

df2
```
### OUTPUT:
![image](https://github.com/user-attachments/assets/408986f0-2895-4a33-9f24-2b854be3385d)

### KNOW THE PRESENCE AN ABSENCE OF DATA VALUES:
```PYTHON
pd.get_dummies(df2,columns=["nom_0"])
```
### OUTPUT:
![image](https://github.com/user-attachments/assets/15b36198-c055-4096-a91f-55fa24602559)

### INSTALLED THE CATEGORY ENCODERS:
```PYTHON
pip install --upgrade category_encoders
```

### IMPORT BINARY ENCODER FROM CATEGORY ENCODERS:
```PYTHON
from category_encoders import BinaryEncoder
```
### READ THE CSV FILE:
```PYTHON
df=pd.read_csv("data.csv")

df
```
### OUTPUT:
![image7](https://github.com/user-attachments/assets/29f8480d-6e8f-4689-abb1-e32f1cc6a9e6)

### TRANSFORMING THE CATEGORICAL DATA INTO BINARY ENCODER:
```PYTHON
be=BinaryEncoder()

nd=be.fit_transform(df['Ord_2'])

dfb=pd.concat([df,nd],axis=1)

dfb1=dfb.copy()

dfb1
```
### OUTPUT:
![image8](https://github.com/user-attachments/assets/4626ad74-872c-4c7b-9733-36cfe36005bc)

### IMPORT THE TARGET ENCODER FROM CATEGORY ENCODERS
```PYTHON
from category_encoders import TargetEncoder
te=TargetEncoder()
cc=df.copy()
new=te.fit_transform(X=cc["City"],y=cc["Target"])
cc=pd.concat([cc,new],axis=1)
cc
```
### OUTPUT:
![image9](https://github.com/user-attachments/assets/55110afc-39f9-48b5-b242-a832708683f1)

### IMPORT PANDAS, SCIPY AND NUMPY TO PERFORM FEATURE TRANFORMATION:
```PYTHON
import pandas as pd
from scipy import stats
import numpy as np
```
### READ THE CSV FILE:
```PYTHON
df=pd.read_csv("Data_to_Transform.csv")
df
```
### OUTPUT:
![image10](https://github.com/user-attachments/assets/eb6c7aac-67ae-4d08-ac64-62603dcfa273)

### FIND THE SKEWNESS OF THE DATASETS:
```PYTHON
df.skew()
```
### OUTPUT:
![image11](https://github.com/user-attachments/assets/31b726ec-dd69-4585-861f-fe31a08c6b4b)

## PERFORMING MATHEMATICAL OPERATIONS FOR THE GIVEN DATASET TO FIND THE SKEWNESS:
### LOGARITHM:
```PYTHON
np.log(df["Highly Positive Skew"])
```
### OUTPUT:
![image12](https://github.com/user-attachments/assets/31ca4b3c-1f70-4a1c-9acd-e85fcdb12bec)

### SQUARE ROOT:
```PYTHON
df["Highly Positive Skew"]=np.sqrt(df["Highly Positive Skew"])
df
```
### OUTPUT:
![image13](https://github.com/user-attachments/assets/97a1d795-ae43-4185-b072-96a523b15a06)

### SQUARE: 
```PYTHON
df["Moderate Negative Skew"]=np.square(df["Moderate Negative Skew"])
df
```
### OUTPUT:
![image14](https://github.com/user-attachments/assets/446d4cf9-747b-4f4b-9bf3-2cd03579cdf9)

### SQUARE ROOT:
```PYTHON
np.sqrt(df["Highly Negative Skew"])
```
### OUTPUT:
![image15](https://github.com/user-attachments/assets/d517084a-3ad4-40e3-bd84-30cc0bec125c)

### FIND THE SKEWNESS:
```PYTHON
df.skew()
```
### OUTPUT:
![image16](https://github.com/user-attachments/assets/b7299afd-f64c-4dad-a973-26b205aeb6c6)

## TRANSFORMS NON-NORMAL DATA INTO A NORMAL DISTRIBUTION:(ONLY POSITIVE VALUE)
### BOXCOX TRANFORMATION:
```PYTHON
df['Highly Positive Skew_boxcox'],parameters=stats.boxcox(df['Highly Positive Skew'])
df
```
### OUTPUT:
![image17](https://github.com/user-attachments/assets/83367045-7751-4bdd-8d9a-ecaec998380a)

## TRANSFORMS NON-NORMAL DATA INTO A NORMAL DISTRIBUTION:(BOTH NEGATIVE AND POSTIVE VALUES):
### YEO JOHNSON TRANSFORMATION:
```PYTHON
df["Moderate Negative Skew_YEOJOHNSON"],parameters=stats.yeojohnson(df["Moderate Negative Skew"])
df
```
### OUTPUT:
![image18](https://github.com/user-attachments/assets/dbde3010-634c-474b-8008-6fe0fe583fc9)

### FIND THE SKEWNESS:
```PYTHON
df.skew()
```
### OUTPUT:
![image19](https://github.com/user-attachments/assets/5032ee52-44bd-49f3-8759-adc9181c05b0)

### ANALYSING THE DATA IN THE VISUALIZATION WAY:
```PYTHON
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt


sm.qqplot(df['Moderate Negative Skew'],line='45')
plt.show()
```
### OUTPUT:
![image20](https://github.com/user-attachments/assets/2bcf3711-2db6-43a3-9388-42281ab5dda8)

### VISUALISE THE DATA INTO THE RECIPROCAL FORM:
```PYTHON
sm.qqplot(np.reciprocal(df['Moderate Negative Skew']),line='45')
plt.show()
```
### OUTPUT:
![image21](https://github.com/user-attachments/assets/9bbd2871-4794-431c-9566-088329ac8cd0)

### PERFORMS QUANTILE TRANSFORMER(Dataset into a uniform or normal data distribution):
```PYTHON
from sklearn.preprocessing import QuantileTransformer

qt=QuantileTransformer(output_distribution='normal')

df["Moderate Negative Skew_1"] = qt.fit_transform(df["Moderate Negative Skew"].values.reshape(-1, 1))
```
### OUTPUT:
![image22](https://github.com/user-attachments/assets/e2cfb5b4-d3fc-4dd6-9531-8ee9173f440b)

### CHECK WHETHER IT IS NORMALIZED FORM:
```PYTHON
sm.qqplot(df['Moderate Negative Skew_1'],line='45')
plt.show()
```
### OUTPUT:
![image23](https://github.com/user-attachments/assets/14acde5c-5319-405b-8165-ed77708fa020)

### PERFORMS QUANTITLE TRANFORMER:
```PYTHON
df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df['Highly Negative Skew'],line='45')
plt.show()
```
### OUTPUT:
![image24](https://github.com/user-attachments/assets/5a19ee23-3381-488e-aa46-692d9b75e61f)

### CHECK WHETHER IT IS NORMALIZED FORM:
```PYTHON
sm.qqplot(df['Highly Negative Skew_1'],line='45')
plt.show()
```
### OUTPUT:
![image25](https://github.com/user-attachments/assets/2300df51-b4fb-46c4-b51b-2279a7ee4d20)

### DISPLAY THE FINALIZED DATASET FOR THE TRANSFOMRED DATASET:
```PYTHON
df
```
### OUTPUT:
 ![image26](https://github.com/user-attachments/assets/32ba3d59-c3ef-4014-9268-71af672db83b)
 
# RESULT:
 Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.     
