# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them

# AIM:

TO detect and remove the outliers in the given data set and save the final data.

# Algorithm:

## Step 1

Import the required packages(pandas,numpy,scipy)

## Step 2

Read the given csv file

## Step 3

Convert the file into a dataframe and get information of the data.

## Step 4

Remove the non numerical data columns using drop() method.

## Step 5

Detect the outliers in the data set using z scores method.

## Step 6

Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

## Step 7

Check if the outliersare removed from data set using graphical methods.

## Step 8

Save the final data set into the file.

# Program:

## (1) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe

```py
import pandas as pd
import seaborn as sns
df = pd.read_csv("/content/bhp.csv")
df
sns.boxplot(data=df)
sns.boxplot(x="price_per_sqft",data=df)
q1 = df['price_per_sqft'].quantile(0.35)
q3 = df['price_per_sqft'].quantile(0.65)
print("First Quantile =",q1,"\nSecond Quantile =",q3)
IQR = q3-q1
high = q3+1.5*IQR
low = q1-1.5*IQR
df1 =df[((df['price_per_sqft']>=low)&(df['price_per_sqft']<=high))]
df1
sns.boxplot(x="price_per_sqft",data=df1)
df1.shape
```

## (1) & (2) Examine price_per_sqft column and use zscore of 3 to remove outliers.

```py
from scipy import stats
import numpy as np
z = np.abs(stats.zscore(df['price_per_sqft']))
df2 = df[(z<3)]
df2
df2.shape
sns.boxplot(x="price_per_sqft",data=df2)
```

## (4) (i)For the data set height_weight.csv detect weight outliers using IQR method

```py
df3 = pd.read_csv("/content/height_weight.csv")
df3
sns.boxplot(x="weight",data=df3)
q1 = df3["weight"].quantile(0.25)
q3 = df3['weight'].quantile(0.75)
print("First Quantile = ",q1,"\nSecond Quantile = ",q3)
IQR = q3-q1
low = q1-1.5*IQR
high = q3+1.5*IQR
df4 =df3[((df3['weight']>=low)&(df3['weight']<=high))]
df4
df4.shape
sns.boxplot(x="weight",data=df4)
```

## (4)(ii) For the data set height_weight.csv detect height outliers using IQR method.

```py
sns.boxplot(x="height",data=df3)
q1 = df3["height"].quantile(0.25)
q3 = df3['height'].quantile(0.75)
print("First Quantile = ",q1,"\nSecond Quantile = ",q3)
IQR = q3-q1
low = q1-1.5*IQR
high = q3+1.5*IQR
df5 =df3[((df3['height']>=low)&(df3['height']<=high))]
df5
df5.shape
sns.boxplot(x="height",data=df5)
```

# OUTPUT:

# DATASET FOR bhp.csv
![Screenshot 2023-05-29 214554](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/6eea1256-e6af-4ffb-be16-1b51cae6a1dd)



# bhp Boxplot
![Screenshot 2023-05-29 214603](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/a83d892a-9438-4b77-ae6e-ec218496f63a)



# DATASET BOXPLOT WITH OUTLIERS(BHP)

![Screenshot 2023-05-29 214610](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/8ebca5fb-5531-48f5-a8ae-12be0f03c072)


# DATASET WITHOUT OUTLIERS(BHP)

![Screenshot 2023-05-29 214622](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/6b98d503-ded1-4b08-b06a-733ea005b388)

![Screenshot 2023-05-29 214632](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/6fc7b5c2-8b0c-4e35-95dc-d35d6e81b880)



# DATASET BOXPLOT WITHOUT OUTLIERS(BHP)
![Screenshot 2023-05-29 214729](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/759267fb-366d-468c-b7d8-148283105dc4)


# Shape
![Screenshot 2023-05-29 214733](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/7ed07457-0b92-4488-b7c5-be2267ab6f9d)



# DATASET AFTER REMOVAL OF OUTLIERS USING Z-SCORE(BHP)

![Screenshot 2023-05-29 214740](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/cc461934-88b4-43db-9545-4b68ba147f4c)


# Shape
![Screenshot 2023-05-29 214746](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/71c1a6fd-7b35-4ad3-bb9b-8973cbc9eaf9)



# DATASET BOXPLOT AFTER REMOVAL OF OUTLIERS USING Z-SCORE(BHP)

![Screenshot 2023-05-29 214751](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/49f13f9b-7f03-4c4e-aadc-013f40d681be)

# DATASET FOR WEIGHT_HEIGHT_CSV

![Screenshot 2023-05-29 214759](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/81f84442-a80f-4c98-abda-bdf15d9da0de)


# DATASET BOXPLOT WITH OUTLIERS(WEIGHT_HEIGHT)
![Screenshot 2023-05-29 214804](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/68cfe534-71e8-4c26-b53f-0f12f5bbd627)



# DATASET AFTER REMOVING OUTLIERS USING IQR METHOD(WEIGHT_HEIGHT)

![Screenshot 2023-05-29 214808](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/dda54a89-a337-47d1-bb74-0922f47ba1b4)

![Screenshot 2023-05-29 214815](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/34c94dab-c0cf-4e65-b92c-de1eaaa0d3c0)



# SHAPE

![Screenshot 2023-05-29 214820](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/89dff744-2352-41b7-9ef2-f827217bc69e)


# DATASET BOXPLOT AFTER REMOVING OUTLIERS USING IQR METHOD(WEIGHT_HEIGHT)

![Screenshot 2023-05-29 214827](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/097b521f-1988-489b-b4e5-6a04cceace68)

# FOR HEIGHT COLUMN WITH OUTLIERS

![Screenshot 2023-05-29 214832](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/073565bc-a62f-415d-81bd-cf9f8acd006b)
![Screenshot 2023-05-29 214841](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/6d766ad8-b70a-432d-85f4-2cc062c0b458)


![Screenshot 2023-05-29 214849](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/a09d7046-3d53-4b24-91c3-28502d6f2ca2)




# Shape
![Screenshot 2023-05-29 214854](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/79da551e-14bf-4458-88c1-b05181be103c)


# AFTER REMOVING OUTLIERS BOXPLOT FOR HEIGHT
![Screenshot 2023-05-29 214859](https://github.com/Nagul71/Ex02-Outlier/assets/118661118/3e67923e-b6ae-4cf5-a103-ab5088b95185)



# Result:

Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
