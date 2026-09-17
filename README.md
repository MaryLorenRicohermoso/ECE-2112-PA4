# ECE-2112-PA4

Ricohermoso, Mary Loren P. | 2ECE-B

This repository contains the Programming Assignment  for "Advance Computer Programming" this A.Y. 2026-2027. This project covers Experiment 4: Data Wrangling and Data Visualization using Pandas and Matplotlib to filter tabular datasets, compute category group means, construct focused DataFrames, and plot side-by-side bar charts.

## A. VISAYAS COMMUNICATION DATAFRAME
  Create a DataFrame named `VisComm` containing examinees whose `Hometown` is "Visayas" and whose `Track` is "Communication". Retain only the columns `Name`, `Gender`, `Math`, `Electronics`, and `Average` in that specified order.

These are the Functions that are used in this Problem:

• `df.mean(axis=1)` - A  method used to compute row-wise arithmetic means across specified numeric subject columns `(Math, Electronics, GEAS, Communication)` to derive the overall score Average.

Example: 

       Average = df['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)

• `Bitwise AND (&)` - An operator used to combine multiple boolean filtering conditions per element.

Example: 

      ['Hometown'] == 'Visayas') & (df ['Track'] == 'Communication')
 
• `.loc` - Label based indexing method used to filter rows matching logical conditions while selecting specific column labels. 

Example: 

      VisComm = df.loc[(df ['Hometown'] == 'Visayas')


Combining all these Functions, the code used for this is: 

```Python

import pandas as pd

Average = df['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)
Average

VisComm = df.loc[(df ['Hometown'] == 'Visayas') & (df ['Track'] == 'Communication'), ['Name', 'Gender', 'Math', 'Electronics', 'Average']]
Viscomm

```

## B. VISAYAS FEMALE DATAFRAME

  Create a DataFrame named `VisFemale` containing examinees whose `Hometown` is "Visayas" and `Gender` is "Female", retaining `Name, Track, GEAS, Electronics, and Average`. Display VisFemale, then separately display a subset where Average is at least 60 without modifying `VisFemale`.

These are the Functions that are used in this Problem:

• `.loc` - Fiters the rows based on combined categorical equality checks and retrieves specified columns.

Example:

        VisFemale = df.loc[(df ['Hometown'] == 'Visayas') & (df ['Gender'] == 'Female')

• `Boolean Indexing ([VisFemale['Average'] >= 60)` - uses a greater than or equal relational relationship (>=) on the `Average` column to extract matching records.

Example:

      VisFemale_60 = VisFemale [VisFemale['Average']>= 60]

Combining all these Functions, the code used for this is: 

```Python

import pandas as pd 

VisFemale = df.loc[(df ['Hometown'] == 'Visayas') & (df ['Gender'] == 'Female'), ['Name', 'Track', 'GEAS', 'Electronics', 'Average']]
VisFemale

VisFemale_60 = VisFemale [VisFemale['Average']>= 60]
VisFemale_60

```





