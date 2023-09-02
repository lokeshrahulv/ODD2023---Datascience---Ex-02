# Ex02-Outlier
## AIM:
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

## ALGORITHM:
### STEP 1:
Read the given Data.

### STEP 2:
Get the information about the data.

### STEP 3:
Detect the Outliers using IQR method and Z score.

### STEP 4:
Remove the outliers:

### STEP 5:
Plot the datas using box plot.

## PROGRAM:
```python
DEVELOPED BY: LOKESH RAHUL V V
REGISTER NUMBER: 212222100024

import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)

### removing ouliers of bhp.csv file using IQR
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)   #new dataframe.
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)


### removing ouliers of bhp.csv file using Zscore of 3

from scipy import stats
import numpy as np
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)

import pandas as pd
dataset=pd.read_csv("/content/height_weight.csv")
dataset.shape
dataset.describe()
dataset.info()
import seaborn as sns
sns.boxplot(x='height',data=dataset)

### Using IQR detect height outliers and print them( height_weight.csv)

Q1_height=dataset['height'].quantile(0.25)
Q3_height=dataset['height'].quantile(0.75)
IQR_HEIGHT=Q3_height-Q1_height
l_height=Q1_height-1.5*IQR_HEIGHT
u_height=Q3_height+1.5*IQR_HEIGHT
outliers_height=dataset[(dataset['height']<l_height) | (dataset['height']>u_height)]
print(outliers_height)
newdata_height=dataset[(dataset['height']>=l_height) & (dataset['height']<=u_height)]
print(newdata_height)
sns.boxplot(x='height',data=newdata_height)


### Using IQR, detect weight outliers and print them( height_weight.csv)

Q1_weight=dataset['weight'].quantile(0.25)
Q3_weight=dataset['weight'].quantile(0.75)
IQR_WEIGHT=Q3_weight-Q1_weight
l_weight=Q1_weight-1.5*IQR_WEIGHT
u_weight=Q3_weight+1.5*IQR_WEIGHT
outliers_weight=dataset[(dataset['weight']<l_weight) | (dataset['weight']>u_weight)]
print(outliers_weight)
newdata_weight=dataset[(dataset['weight']>=l_weight) & (dataset['weight']<=u_weight)]
print(newdata_weight)
sns.boxplot(x='weight',data=newdata_weight)
```
## OUTPUT:
### bhp.csv:
### df.head():
![Screenshot 2023-09-02 093401](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/4e314b3c-05b0-4907-aaed-4924bf1e808f)

### df.describe():
![Screenshot 2023-09-02 093541](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/953b4538-7d46-42e5-b3d9-6b2ea3b07c89)

### df.info():
![Screenshot 2023-09-02 093621](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/595aefb2-eb19-4840-b1e1-338da4710359)

### df.shape:
![263435504-8139bab9-cd3a-4396-8d59-37cdabccc16c](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/926e4cc7-6fb6-4c10-8be0-84887c4c2b03)

### BOXPLOT BEFORE REMOVING OUTLIERS:
![263435525-9b85c1c1-d59c-4068-8497-560661b960cd](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/d47f2495-7344-44a0-88ab-306ed1a482ac)

### NEWDATA USING IQR:
![263435555-2f5a6116-63c8-484c-98c0-52705044c8d8](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/3d3592e1-250f-40f0-b8e2-d7dddb532250)

### OUTLIERS:
![263435582-488128f1-b53a-4b30-89f4-dd930754c3cc](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/7880f687-7ae1-4c4c-af5b-a3b2207a35da)

### newdata.shape: 
![263435613-c43cd0f5-574a-4314-a6ef-918bc03e755a](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/842c7703-1b40-49e5-9a72-cfb2f54d9ba0)

### BOXPLOT AFTER REMOVING OUTLIERS USING IQR:
![263435648-7caaa273-3482-4cc5-89c0-dd4c525dc4cb](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/06c8968e-3b65-4fbb-b3bb-ccd6987554fe)

### NEWDATA USING Zscore:
![263435770-51c6341b-adb9-44f2-857b-63772b8e7e4c](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/e94b8539-1376-4b28-96ef-60af6f64eb2c)

### OUTLIERS:
![263435892-dd314c16-30d1-4b5c-b462-d5714c880331](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/7bbc90bb-e0ab-4124-80ba-0070a5e05f78)

### newdata2.shape:
![263435990-470146b4-e231-4ade-b647-f6baedba8ff8](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/81f3d73a-b1b6-4876-8c64-65783c3b11eb)

### BOXPLOT AFTER REMOVING OUTLIERS USING Zscore:
![263436107-4be8e577-943e-4cfe-8dc9-387d8f2f7a89](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/2d272e58-3229-47c5-bd38-f942dedae6b2)

### height_weight.csv:
![263436237-65fcf50e-edc0-4150-b698-6602e71a0538](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/7116c094-6648-4057-b2fe-d57124fb22b6)

### dataset.describe():
![263436440-3cb91f70-073e-4666-9d60-6f7d3e623a53](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/43c98585-7aa3-4f4d-abc8-77eec662ff73)

### BOXPLOT BEFORE REMOVING OUTLIERS:
![263436575-13eb60bd-58a8-4f44-8709-76c82cc274f2](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/3fe33e2d-bc7d-42c7-911f-64dce7e775ba)

### HEIGHT OUTLIERS:
![263436596-333887dc-eb45-4768-b9c3-28b2580ad410](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/e70ae5e9-ab96-4c5f-ad88-8a5f1d6be6b8)

### DATASET AFTER REMOVING HEIGHT OUTLIERS:
![263436613-2d37472f-f3a5-4d92-8e4d-ce41319a8aed](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/08c5f0e0-b615-433c-85c1-dbba24754298)

### BOXPLOT AFTER REMOVING HEIGHT OUTLIER:
![263436639-174e6731-27d7-40aa-9ba6-44c4ba834ef8](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/591245c4-6e4b-414f-ab41-7a880b80066a)

### WEIGHT OUTLIERS:
![263436646-46c1c529-072f-4cc3-948d-062553f3b6c4](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/980890b1-3296-4230-9a0a-fc4d456760c7)

### DATASET AFTER REMOVING WEIGHT OUTLIERS:
![263436665-72eb0591-5827-472e-a270-f511f31d2323](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/0e0fd6a5-9a19-4a48-b514-6a2842dd57bd)

### BOXPLOT AFTER REMOVING WEIGHT OUTLIERS:
![263436680-03588439-3aab-44fb-882e-5de2af00ce39](https://github.com/lokeshrahulv/ODD2023---Datascience---Ex-02/assets/118423842/61d14c1a-0c8f-4761-b7d4-37a0eed8eda6)

## RESULT:
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
