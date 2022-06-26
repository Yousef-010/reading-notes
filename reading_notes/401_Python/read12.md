# Reading 12

> What kind of data does pandas handle? 
- To load the pandas package and start working with it, import the package. The community agreed alias for pandas is pd, so loading pandas as pd is assumed standard practice for all of the pandas documentation.
  - DataFrame 
  - A DataFrame is a 2-dimensional data structure that can store data of different types (including characters, integers, floating point values, categorical data and more) in columns. It is similar to a spreadsheet, a SQL table or the data.frame in R.

```
df = pd.DataFrame(
    {
        "Name": [
            "Braund, Mr. Owen Harris",
            "Allen, Mr. William Henry",
            "Bonnell, Miss. Elizabeth",
        ],
        "Age": [22, 35, 58],
        "Sex": ["male", "male", "female"],
    }
)


df
Out[3]: 
                       Name  Age     Sex
0   Braund, Mr. Owen Harris   22    male
1  Allen, Mr. William Henry   35    male
2  Bonnell, Miss. Elizabeth   58  female
```

- Each column in a DataFrame is a Series¶ 
```
ages = pd.Series([22, 35, 58], name="Age")

ages
Out[6]: 
0    22
1    35
2    58
Name: Age, dtype: int64
```

> How do I read and write tabular data? 
- pandas provides the read_csv() function to read data stored as a csv file into a pandas DataFrame. pandas supports many different file formats or data sources out of the box (csv, excel, sql, json, parquet, …), each of them with the prefix read_*.
- Make sure to always have a check on the data after reading in the data. When displaying a DataFrame, the first and last 5 rows will be shown by default:
```
titanic.head(8)
Out[4]: 
   PassengerId  Survived  Pclass                                               Name     Sex  ...  Parch            Ticket     Fare Cabin  Embarked
0            1         0       3                            Braund, Mr. Owen Harris    male  ...      0         A/5 21171   7.2500   NaN         S
1            2         1       1  Cumings, Mrs. John Bradley (Florence Briggs Th...  female  ...      0          PC 17599  71.2833   C85         C
2            3         1       3                             Heikkinen, Miss. Laina  female  ...      0  STON/O2. 3101282   7.9250   NaN         S
3            4         1       1       Futrelle, Mrs. Jacques Heath (Lily May Peel)  female  ...      0            113803  53.1000  C123         S
4            5         0       3                           Allen, Mr. William Henry    male  ...      0            373450   8.0500   NaN         S
5            6         0       3                                   Moran, Mr. James    male  ...      0            330877   8.4583   NaN         Q
6            7         0       1                            McCarthy, Mr. Timothy J    male  ...      0             17463  51.8625   E46         S
7            8         0       3                     Palsson, Master. Gosta Leonard    male  ...      1            349909  21.0750   NaN         S

[8 rows x 12 columns]
```

> How do I select a subset of a DataFrame? 
- o select a single column, use square brackets [] with the column name of the column of interest.
```
ages = titanic["Age"]

ages.head()
Out[5]: 
0    22.0
1    38.0
2    26.0
3    35.0
4    35.0
Name: Age, dtype: float64
```

> How to create plots in pandas?
- To plot a specific column, use the selection method of the subset in combination with the plot() method. Hence, the plot() method works on both Series and DataFrame.
```
air_quality.plot()
Out[5]: <AxesSubplot:xlabel='datetime'>
```
```
air_quality["station_paris"].plot()
Out[6]: <AxesSubplot:xlabel='datetime'>
```

> How to create new columns derived from existing columns? 
- Example
```
air_quality["ratio_paris_antwerp"] = (
    air_quality["station_paris"] / air_quality["station_antwerp"]
)

```
- Rename : 
- The rename() function can be used for both row labels and column labels. Provide a dictionary with the keys the current names and the values the new names to update the corresponding names.


> How to calculate summary statistics? 
- on the data above we can
```
titanic["Age"].mean()
titanic[["Age", "Fare"]].median()
titanic[["Age", "Fare"]].describe()
titanic[["Age", "Fare"]].describe()titanic[["Sex", "Age"]].groupby("Sex").mean()

```
- split : the data into groups
- apply :  a function to each group independently
- combine : the results into a data structure


> How to reshape the layout of tables? 
- we can use sort and then group by pivot methods after each other will reshape the shape of the table of data


> How to combine data from multiple tables? 
- using Concat method 
```
for the date above 
air_quality = pd.concat([air_quality_pm25, air_quality_no2], axis=0)
air_quality.head()
```
- or merge like 
```
air_quality = pd.merge(air_quality, stations_coord, how="left", on="location")
air_quality.head()
```

> How to handle time series data with ease?
- Valid date strings can be converted to datetime objects using to_datetime function or as part of read functions.
- Datetime objects in pandas support calculations, logical operations and convenient date-related properties using the dt accessor.
- A DatetimeIndex contains these date-related properties and supports convenient slicing.
- Resample is a powerful method to change the frequency of a time series.
```
air_quality["datetime"] = pd.to_datetime(air_quality["datetime"])
air_quality["datetime"]
```


> How to manipulate textual data?
- String methods are available using the str accessor.
- String methods work element-wise and can be used for conditional indexing.
- The replace method is a convenient method to convert values according to a given dictionary.
  - make all the lowercase characters
```
titanic["Name"].str.lower()
```
- or we can 
  - split the string by comma 
```
titanic["Name"].str.split(",")
```
> ____________________________________ THANKS FOR READING _______________________  THE END  _____________________________ ^ _ ^________________________________________________


> Resources 
- https://pandas.pydata.org/pandas-docs/stable/getting_started/intro_tutorials/index.html 
- https://pandas.pydata.org/pandas-docs/stable/user_guide/10min.html
- https://realpython.com/learning-paths/pandas-data-science/ 


