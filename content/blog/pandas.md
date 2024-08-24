---
title: "Introduction to pandas 🧑🏻"
summary: "Overview of pandas for new users"
description: "Overview of pandas for new users"
date: 2024-08-08T02:41:01+09:00
author: "Kanato Nishiura"
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
hideSummary: false
ShowReadingTime: true
ShowPostNavLinks: true
---
Hi there👋🏻  
I hope you doing well.

Today, I would like to explain the basic knowledge of pandas based on the official tutorial.

# What is pandas ?

Pandas is a fast, powerful, flexible and easy to use open source data analysis and manipulation tool, built on top of the Python programming language.

# Basic data structures in pandas

* `Series`:  a one-dimensional labeled array holding data of any type such as integers, strings, Python objects etc.

* `DataFrame`: a two-dimensional data structure that holds data like a two-dimension array or a table with rows and columns.

# Read and write data
### Read data from file

``` python
import pandas as pd
import numpy as np
data = pd.read_csv('data.csv', index_col=False) 
```
* `import pandas`: Make pandas available
* `as pd`: The part to write "pandas" can be written by omitting "pd"
* `pd.read_csv('name of file')`: `pd.read_csv` is a pandas function and is used to read CSV files.
* `index_col=False`: If there is no index column in the read file, add index_col=False. Then the index will be automatically added on loading.

### Read data by direct description

``` python
import pandas as pd
import numpy as np
series = pd.Series([1,2,3])
df = pd.DataFrame([['sato', 18], ['suzuki', 20]])
```
* `pd.Series`: a pandas function to convert a list or array into a one-dimensional labeled array.
* `pd.Dataframe`: a pandas function to convert lists, arrays, dictionaries, etc. into two-dimensional labeled tables.

### Write data to CSV file

``` python
data.to_csv('sample.csv', index=False)
```
* `to_csv`: a pandas function to convert the data variable to a csv file and save it.
* `index=False`: index is not needed for data analysiss, so it is not saved.

# Viewing data
### a concise summary of a DataFrame
``` python
data.info()
```
It provides the following information: 
1. **Index (RangeIndex)**: Shows the index range (starting and ending) of the DataFrame.
2. **Column names**: Lists all the column names in the DataFrame.
3. **Non-null count**: Displays the number of non-null (non-missing) values in each column.
4. **Data type (Dtype)**: Shows the data type of each column (e.g., int64, float64, object, datetime64, etc)

### show the type of the object
``` python
type(data)
```
When working with Pandas, if data is a DataFrame or a Series, type(data) will return:

* pandas.core.frame.DataFrame if data is a DataFrame.
* pandas.core.series.Series if data is a Series.

### Change the data type for each column
``` python
data['name of column'].astype(float)
#Change data type of 'name of column' to float
```
### Display the number of matrices
``` python
data(shape)
#Example result (5,5)
#(number of rows, columns) can be obtained
```
### Display the number of rows
``` python
len(data)
```
### Dispaly the number of columns
``` python
len(data.columns)
```
### Display total number of elements
``` python
data.size
#Equal to number of rows * number of columns
```
### Display the first row
``` python
data.head()
#Display 5 lines of data from the top

data.head(2)
#Display 2 lines of data from the top
```
### Dispaly the last row
``` python
data.tail()
#Display 5 lines of data from the end

data.tail(2)
#Display 2 lines of data from the end
```
### Dispaly optional rows
``` python
data[10:20]
#Display data from rows 10 to 19

data[:5]
#Display 5 lines of data from the top

data[-5:]
#Display 5 lines of data from the end

data.loc['name of row', 'name of column']
#Display data for specified row/column name

data,loc['name of row', 'name of column'] = 'Data you want to insert'
#Data can be inserted into specified rows and columns

data.iloc[0]
#Display data from row with index 0 (first row)

data.iloc[-1]
#DIsplay the data of the last row

data[data['name of column'] >= 100]
#Display rows with a value of 100 or more in the specified column

data[data['name of column'].max()]
#Display rows with the largest value in the specified column
```
### Display optional columns
``` python
data[['name of column']]
#Dispaly data for specified column name

data[['name of column 1', 'name of column 2']]
#Display data in multiple specified columns
```
### Display optional value
``` python
data.iloc[0]['name of column']
#Displays the value of the 'column name' element in the first row
```
### Counting unique elemants
``` python
data.unique()
#Display list of unique element values

data.value_counts()
#Displays unique element values and their number of appearances

data.nunique()
#Display the number of unnique elements

data.nunique(axis=1)
#Display the number of unique elements for each row
```
`axis=0`: Default value. Vertical, in other words, an operation on each column.   
`axis=1`: Operate horizontally, in other words, for each row.
# Data totalization
### Data connection
``` python
data = pd.concat((data, add_data), axis=0, sort=True)
#Concatenate data and add_data

data = data.reset_index()
#Reassign the index. The original index is stored in the column `index`

data.drop(['index'], axis=1, inplace=True)
#Delete the `index` column created above
```
`sort=True`: Specifies whether the concatenated columns should be sorted in dictionary order.   
`how='inner'`: Adding this option when concatenating results in an inner join and duplicate columns/rows are deleted.   
`.drop`: Deletes rows and columns with specified labels.   
`inplace=True`: Manipulates the current data directly; if False, new data is created.   
### Caluculaion
``` python
data.sum()
#Displays the sum of each column of data

data.sum(axis=1)
#Displays the sum of each row of data

data.mean(axis=1)
#Displays the mean of each row of data   

data.describe().round(1)
#Calculate summary statistics for each column of data to one decimal place   

data.corr()
#Calculate the correlation coefficient for each column of data
```
# Data formatting
### Duplicate/Unique value
```  python
data['name of column'].unique()
#Display unique values for specified columns

data[~data['name of column'].duplicated()]
#Extract only unique values for a given column

data.drop_duplicates('name of column', inplace=True)
#Delete rows with duplicate values in the specified column
```
`.duplicated()`: A method that returns a boolean value as to whether the element is a duplicate or not.   
`~`: Tilde. A method to invert boolean values.   
`.drop_duplicates()`: Method to delete duplicate rows.   
### Missing value
``` python
data.isnull()
#Checks all values and returns a boolean value depending on the existence of missing values

data.isnull().all()
#Determine if there are missing values in each column. Returns False if there is even one missing value in a column

data.isnull().all(axis=1)
#Determine if there are missing values in each row. Returns False if there is even one missing value in a row

data.isnull().any()
#Display columns with at least one missing value

data.isnull().any(axis=1)
#Display rows with at least one missing value

data.dropna(how='any')
#Rows that contain even one missing value are deleted

data.dropna(how='all')
#Rows that are all missing values are deleted

data.dropna(how='all', axis=1)
#Columns that are all missing values are deleted
```
`.isnull()`, `.isna()`: Determine for each element and display True if there is a missing value.   
`.notnull()`, `.notna()`: Determine for each element and display True if the value exists.   

# String processing
### Data processing for optional strings
``` python
data.str.startswith('text string')
#Returns True for elements beginning with 'text string'

data[data.str.startswith('text string')]
#Display rows including elements beginning with 'text string'

data.str.endswith('text string')
#Returns True for elements ending in 'text string'.

data.str.containswith('text tring')
#Returns True for elements including 'text string'.

data['name of column'].str[0:2]
#Slices the string contents of a column with the specified column name to the first two characters of that string only.

data = data.str.strip()
#Delete leading and trailing blank characters in data.

data = data.str.strip('x')
#Delete 'x' in data.

data['name of column'][index] = data['name of column'][index].strip('x')
#Deletes the string 'x' from the value of the specified column name * index.
```

I hope you will make use of this article in your studies!   
Thanks for reading this far!   
See you in the next post!   