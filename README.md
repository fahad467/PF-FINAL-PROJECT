# PF-FINAL-PROJECT

PF project ( GPU data analysis )  

import pandas as pd
df = pd.read_csv("youtube data.csv")
df.shape

## Data Cleaning

df.info()

### Columns

column = list(df.columns)
column

##### Check Empty values

df.isna().sum()

#### Cleaning empty set

df.dropna
df.dropna(inplace=True)

## Replace Empty values

df.fillna(40)

### Replace specific columns

df['Subscribers'].fillna(20)
### Mean,Mode,Median

mean_rankings = df['Ranking'].mean()
print(mean_rankings)
df['Country'].mode() # common
median_uploads = df['Uploads'].median()  
print(median_uploads)

## Data Duplications
df.duplicated()
#### Drop 
df.drop_duplicates()
#### Describe
df.describe()
#### iloc
df.describe(include = "all").iloc[[0,5]] # includes all and tell the index and positions
#### loc
df.describe(include = "all").loc[["min","max"]] # includes all and tell the minimum and maximum values

## Adding a column

df['col'] = 6
df

## Remove a column

df.drop(columns=['col'], inplace=True, errors='ignore')
df

## Adding a row
data = {
    'Rank': [1, 2, 3], 
    'Channel Name': ['T-Series', 'Cocomelon', 'MrBeast'],
    'Subscribers (Millions)': [250, 160, 150],
    'Total Views (Billions)': [230, 140, 25], 
    'Videos Uploaded': [19000, 800, 750 ], 
    'Country': ['India', 'USA', 'USA'],  
    'Category': ['Music', 'Kids', 'Entertainment']  
}
df = pd.DataFrame(data)
print(df)

## Remove a row

df.drop(1,inplace=True) # it removed my 0,50,51 and 53 index
df

## Slicing 

df[2:20:2]

### columns slicing

df[['Username']][4:12]

## Flowcharts

df['Country'].value_counts().plot(kind="bar")
df['Subscribers'].value_counts().plot(kind="barh")
df['Uploads'].value_counts().plot(kind="box")
df['Views'].value_counts().plot(kind="density")
df['Username'].value_counts().plot(kind="pie")
df['Ranking'].value_counts().plot(kind="line")
df['Country'].value_counts().plot(kind="kde")
df['Subscribers'].value_counts().plot(kind="hist")

## Data Aggretion

# Aggregating numeric columns

numeric_aggregates = df.select_dtypes(include='number').agg(['sum', 'min',])
print(numeric_aggregates)

#### sum()

df['Ranking'].sum()

#### std() (Standard Deviation)

df['Ranking'].std()

#### var() Variance Calculation

df['Ranking'].var()

## Data Preprocessing

df.isnull().sum() # it only shows the empty values and taking the sum of the dataframe

#### rename() Rename Columns

df.rename(columns={'Username':'Name'}, inplace=True)
df

## Data Saving

df = pd.read_csv("youtube data.csv")

# Save the DataFrame to an Excel file
df.to_excel("project.xlsx", index=False)
