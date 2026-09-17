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

## C. CATEGORY-AVERAGE VISUALIZATION

  Examine how board exam averages differ across categorical features `(Track, Gender, Hometown)`. Calculate the mean `Average` for each category, display three summary tables, render a figure containing three side-by-side bar charts, and identify the highest category mean for each feature using code.

These are the Functions that are used in this Problem:

•  `.mean()` - Filters the data set for specific values to compute their respective means.

Example: 

      Female = df[df['Gender'] == 'Female']['Average'].mean()

• `pd.DataFrame()` - Constructs structured summary tables mapping each category name to its computed average score. 

Example:

      TrackTable = pd.DataFrame({'Track': [...], 'Average': [Communication, Instrumentation, Microelectronics})

• `plt.subplots(1,3)` - A matplotlib function initializing a grid of 1 row and 3 columns to organize multiple plots in a single figure. 

Example:

      fig, axes = plt.subplots(1, 3, figsize=(15, 5))

• `.plot(kind=bar)` - Generates bar charts directly from Pandas DataFrame targeted at specific subplot axes.

Example: 

      TrackTable.plot(kind='bar', ax=axes[n])

• `.idmax() & .loc()` - It ocated the row index with the maximum `Average` value and retrieves its corresponding category level.

Example:

      Highest Track = TrackTable.loc[TrackTable['Average'].idxmax()


Combining all these Functions, the code used for this is: 

```Python

import pandas as pd
a. Track
Communication = df[df['Track'] == 'Communication']['Average'].mean()
print(Communication)

Instrumentation = df[df['Track'] == 'Instrumentation']['Average'].mean()
print(Instrumentation)

Microelectronics = df[df['Track'] == 'Microelectronics']['Average'].mean()
print(Microelectronics)

a.gender
Female = df[df['Gender'] == 'Female']['Average'].mean()
print(Female)

Male = df[df['Gender'] == 'Male']['Average'].mean()
print(Male)

a.hometown
Luzon = df[df['Hometown'] == 'Luzon']['Average'].mean()
print(Luzon)

Visayas = df[df['Hometown'] == 'Visayas']['Average'].mean()
print(Visayas)

Mindanao = df[df['Hometown'] == 'Mindanao']['Average'].mean()
print(Mindanao)

b. 
TrackTable = pd.DataFrame({
    'Track': ['Communication', 'Instrumentation', 'Microelectronics'],
    'Average': [Communication, Instrumentation, Microelectronics]
})
TrackTable

GenderTable = pd.DataFrame({
    'Gender': ['Female', 'Male'],
    'Average': [Female, Male]
})
GenderTable

HometownTable = pd.DataFrame({
    'Hometown': ['Luzon', 'Visayas', 'Mindanao'],
    'Average': [Luzon, Visayas, Mindanao]
})
HometownTable

c.
import matplotlib.pyplot as plt
fig, axes = plt.subplots(1, 3, figsize=(15, 5))

TrackTable.plot(kind='bar', ax=axes[0])
axes[0].set_title('Track Mean Average')
axes[0].set_xlabel('Track')
axes[0].set_ylabel('Mean Average')
axes[0].tick_params(axis='x', rotation=45)

GenderTable.plot(kind='bar', ax=axes[1])
axes[1].set_title('Gender Mean Average')
axes[1].set_xlabel('Gender')
axes[1].set_ylabel('Mean Average')
axes[1].tick_params(axis='x', rotation=0)


HometownTable.plot(kind='bar', ax=axes[2])
axes[2].set_title('Hometown Gender Mean')
axes[2].set_xlabel('Hometown')
axes[2].set_ylabel('Mean Average')
axes[2].tick_params(axis='x', rotation=45)

plt.tight_layout()
plt.show()

d. 
Highest_Track = TrackTable.loc[TrackTable['Average'].idxmax(), 'Track']
Highest_Gender = GenderTable.loc[GenderTable['Average'].idxmax(), 'Gender']
Highest_Hometown = HometownTable.loc[HometownTable['Average'].idxmax(), 'Hometown']

print(f"{Highest_Track} has the highest sample mean Average among the Track categories.")
print(f"{Highest_Gender} has the highest sample mean Average among the Gender categories.")
print(f"{Highest_Hometown} has the highest sample mean Average among the Hometown categories.")

df.groupby('Track')['Average'].mean()
df.groupby('Gender')['Average'].mean()
df.groupby('Hometown')['Average'].mean()

```

## Thank you for reading!

To see the main python program for Programming Assignment 4, click this link https://github.com/MaryLorenRicohermoso/ECE-2112-PA4/blob/main/Ricohermoso_2ECEB_PA4.ipynb  and download. Open on Jupyter Notebook, then run all cells.

# README file Version History:
September 17, 2026 - Initial README output uploaded








