# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them



## Aim:
  TO detect and remove the outliers in the given data set and save the final data.

## Algorithm:

### Step 1:
Import the required packages(pandas,numpy,scipy)

### Step 2:
Read the given csv file

### Step3:
Convert the file into a dataframe and get information of the data.

### Step 4:
Remove the non numerical data columns using drop() method.

### Step 5:
Detect the outliers in the data set using z scores method.

### Step 6:
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

### Step 7:
Check if the outliersare removed from data set using graphical methods.

### Step 8:
Save the final data set into the file.

## Program:
1) & (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.

```
import pandas as pd
import numpy as np
import seaborn as sns
df = pd.read_csv("/content/bhp.csv")
df
df.head()
df.describe()
df.info()
df.isnull().sum()
df.shape
sns.boxplot(x="price_per_sqft",data=df)
q1 = df['price_per_sqft'].quantile(0.25)
q3 = df['price_per_sqft'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)
IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR
df1 =df[((df['price_per_sqft']>=ll)&(df['price_per_sqft']<=ul))]
df1
df1.shape
sns.boxplot(x="price_per_sqft",data=df1)
```

(3)Examine price_per_sqft column and use zscore of 3 to remove outliers.
```
from scipy import stats
z = np.abs(stats.zscore(df['price_per_sqft']))
df2 = df[(z<3)]
df2
print(df2.shape)
sns.boxplot(x="price_per_sqft",data=df2)
```
(4)(i) For the data set height_weight.csv detect weight outliers using IQR method.
import pandas as pd
import numpy as np
import seaborn as sns
df = pd.read_csv("/content/height_weight - Sheet1.csv")
df
df.head()
df.info()
df.describe()
df.isnull().sum()
df.shape
print("First Quantile =",q1,"\nSecond Quantile =",q3)
IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR
df1 =df[((df['weight']>=ll)&(df['weight']<=ul))]
df1
df1.shape
sns.boxplot(x="weight",data=df1)
```
(4)(ii) For the data set height_weight.csv detect height outliers using IQR method.
```
sns.boxplot(x="height",data=df)
q1 = df['height'].quantile(0.25)
q3 = df['height'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)
IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR
df2 =df[((df['height']>=ll)&(df['height']<=ul))]
df2
df2.shape
sns.boxplot(x="height",data=df2)
```

##OUTPUT:
(1)(2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.

### DATASET:
![Screenshot 2023-04-03 084713](https://user-images.githubusercontent.com/120232371/229403770-172953eb-cf29-4b11-8a50-afb1fccc40cf.png)

### DATASET HEAD:
![Screenshot 2023-04-03 084942](https://user-images.githubusercontent.com/120232371/229403949-ccc5068b-783c-40f9-ab37-05133c77a41c.png)

### DATASET INFO:
![Screenshot 2023-04-03 085152](https://user-images.githubusercontent.com/120232371/229404214-c8d744df-0ec7-4665-b32b-15d977ab49dc.png)

### DATASET DESCRIBE:
![Screenshot 2023-04-03 085320](https://user-images.githubusercontent.com/120232371/229404357-0a764538-9f77-44f7-b912-b12bc380d8d4.png)

### NULL VALUE:
![Screenshot 2023-04-03 085450](https://user-images.githubusercontent.com/120232371/229404492-3ed075df-7e06-4210-9753-b073c863cb7b.png)

### DATASHAPE:
![Screenshot 2023-04-03 085559](https://user-images.githubusercontent.com/120232371/229404658-3bf98451-8ccf-4fce-b755-5187b1527c97.png)

### BOX PLOT OF PRICE_PER_SQFT COLUMN WITH OUTLIERS:
![Screenshot 2023-04-03 085732](https://user-images.githubusercontent.com/120232371/229404960-06fdf107-3c8e-4dd0-b23b-5e4eab5558d7.png)

### price_per_sqft - Dataset after removing outliers:
![Screenshot 2023-04-03 090027](https://user-images.githubusercontent.com/120232371/229405160-65fafc90-2d74-4625-8c37-5516a238f9ee.png)

### price_per_sqft - Shape of Dataset after removing outliers :
![Screenshot 2023-04-03 090741](https://user-images.githubusercontent.com/120232371/229405890-18d3e6a9-8fc8-470a-89f0-bb972a583fb1.png)

### Box Plot of price_per_sqft column without outliers:
![Screenshot 2023-04-03 090857](https://user-images.githubusercontent.com/120232371/229406106-86b5633c-b352-40af-8960-a2713446d1d6.png)

### Examine price_per_sqft column and use zscore of 3 to remove outliers.
### Dataset after removal of outlier using z score:
![Screenshot 2023-04-03 091107](https://user-images.githubusercontent.com/120232371/229406306-de33d331-6af7-4b81-8cf3-10b710e883a1.png)

### Shape of Dataset after removal of outlier using z score:
![Screenshot 2023-04-03 091220](https://user-images.githubusercontent.com/120232371/229406479-c7a81cf4-10e3-4b82-a1bd-b19b37428b23.png)

### (4) For the data set height_weight.csv detect weight and height outliers using IQR method:
### Dataset:
![Screenshot 2023-04-03 091349](https://user-images.githubusercontent.com/120232371/229406649-bf170091-d277-4247-9bf1-915b8f175b96.png)

### Dataset Head:
![Screenshot 2023-04-03 091559](https://user-images.githubusercontent.com/120232371/229406931-81124433-c6e4-44a9-8f35-c6edd32029a6.png)

### Dataset Info:
![Screenshot 2023-04-03 091710](https://user-images.githubusercontent.com/120232371/229407023-f6c77503-d7a3-4a1d-a665-c12fbcb46d64.png)

### Dataset describe:
![Screenshot 2023-04-03 091800](https://user-images.githubusercontent.com/120232371/229407137-73b7110a-9f3c-4a4b-b674-343424ef9d3d.png)

### Nullvalues:
![Screenshot 2023-04-03 091904](https://user-images.githubusercontent.com/120232371/229407657-36cd32dc-4499-43e6-91b7-98ce557e37f4.png)

### Dataset shape:
![Screenshot 2023-04-03 092331](https://user-images.githubusercontent.com/120232371/229407763-bea4b141-95ce-4d98-ad38-518390c5748a.png)

### Weight- with outliers:
![Screenshot 2023-04-03 092435](https://user-images.githubusercontent.com/120232371/229407878-8086f4bd-c2a4-4cba-84ac-2a03f62f5f71.png)

### Weight - Dataset after removing Outliers using IQR method:
![Screenshot 2023-04-03 092559](https://user-images.githubusercontent.com/120232371/229408050-15778196-57f4-4424-95cd-665fa54c94da.png)

### Weight - Shape of Dataset after removing Outliers using IQR method:
![Screenshot 2023-04-03 092725](https://user-images.githubusercontent.com/120232371/229408248-5ab1408f-e493-4a8b-a88c-fda4fd991892.png)

### Weight - Without Outliers using IQR method:
![Screenshot 2023-04-03 092903](https://user-images.githubusercontent.com/120232371/229408449-f663e757-31a4-4340-85e6-053bea5e544b.png)

### Height - With outliers:
![Screenshot 2023-04-03 093053](https://user-images.githubusercontent.com/120232371/229408580-f415525f-85cf-40ed-a8e3-18e3a1f0893d.png)

### Height - Dataset after removing Outliers using IQR method:
![Screenshot 2023-04-03 093256](https://user-images.githubusercontent.com/120232371/229408718-80bb463a-5bf7-4d36-9dd0-ada112403b77.png)

### Height - Shape of Dataset after removing Outliers using IQR method:
![Screenshot 2023-04-03 093351](https://user-images.githubusercontent.com/120232371/229408846-7a856556-bbee-493d-8018-1a3786971eea.png)

### Height - Without Outliers using IQR method:
![Screenshot 2023-04-03 093520](https://user-images.githubusercontent.com/120232371/229408967-81d59935-f774-4650-a290-7421671dd75f.png)
## Result:
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
















