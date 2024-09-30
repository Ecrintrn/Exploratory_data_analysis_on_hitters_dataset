# Exploratory Data Analysis On Hitters Dataset

# Business Problem

This study aims to perform exploratory data analysis using the ditters baseball dataset

# Dataset Story

Description Major League Baseball Data from the 1986 and 1987 seasons.

Usage Hitters

Format A data frame with 322 observations of major league players on the following 20 variables.

AtBat: Number of times at bat in 1986

Hits: Number of hits in 1986

HmRun: Number of home runs in 1986

Runs: Number of runs in 1986

RBI: Number of runs batted in in 1986

Walks: Number of walks in 1986

Years: Number of years in the major leagues

CAtBat: Number of times at bat during his career

CHits: Number of hits during his career

CHmRun: Number of home runs during his career

CRuns: Number of runs during his career

CRBI: Number of runs batted in during his career

CWalks: Number of walks during his career

League: A factor with levels A and N indicating player's league at the end of 1986

Division: A factor with levels E and W indicating player's division at the end of 1986

PutOuts: Number of put outs in 1986

Assists: Number of assists in 1986

Errors: Number of errors in 1986

Salary: 1987 annual salary on opening day in thousands of dollars

NewLeague: A factor with levels A and N indicating player's league at the beginning of 1987

Source This dataset was taken from the StatLib library which is maintained at Carnegie Mellon University. This is part of the data that was used in the 1988 ASA Graphics Section Poster Session. The salary data were originally from Sports Illustrated, April 20, 1987. The 1986 and career statistics were obtained from The 1987 Baseball Encyclopedia Update published by Collier Books, Macmillan Publishing Company, New York.

References Games, G., Witten, D., Hastie, T., and Tibshirani, R. (2013) An Introduction to Statistical Learning with applications in R, www.StatLearning.com, Springer-Verlag, New York

Examples summary(Hitters)

lm(Salary~AtBat+Hits,data=Hitters) Dataset imported from https://www.r-project.org.

# Import Necessary Libraries

```
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import math

# Settings
pd.set_option("display.max_columns", None)
pd.set_option("display.max_rows", None)
pd.set_option("display.width", 500)
pd.set_option("display.float_format", lambda x: "%.3f" % x)
```

# Import Dataset

```
df = pd.read_csv(path)
return df
```

# General Information About to Dataset

## Checking the Data Frame

```
print(20*"#","HEAD",20*"#")
print(dataframe.head(head))
print(20*"#","Tail",20*"#")
print(dataframe.tail(head))
print(20*"#","Shape",20*"#")
print(dataframe.shape)
print(20*"#","Types",20*"#")
print(dataframe.dtypes)
print(20*"#","NA",20*"#")
print(dataframe.isnull().sum().sum())
print(dataframe.isnull().sum())
print(20*"#","Quartiles",20*"#")
print(dataframe.describe([0, 0.01, 0.05, 0.10, 0.20, 0.30, 0.40, 0.50, 0.6, 0.7, 0.8, 0.9, 0.95, 0.99, 1]).T)
```

## Analysis of Categorical and Numerical Columns

To summarize and visualize the referred column we create a other function called num_summary.

```
cat_cols = [col for col in datraframe.columns if str(datraframe[col].dtypes) in ["category", "object", "bool"]]
num_but_cat = [col for col in datraframe.columns if datraframe[col].nunique()< cat_th and datraframe[col].dtypes in ["uint8", "int64", "float64"]]
cat_but_car = [col for col in datraframe.columns if datraframe[col].nunique() > car_th and str(datraframe[col].dtypes) in ["category", "object"]]
cat_cols = cat_cols + num_but_cat
num_cols= [col for col in datraframe.columns if datraframe[col].dtypes in ["uint8", "int64", "float64"]]
num_cols = [col for col in num_cols if col not in cat_cols]
```

![League-Ratio](https://github.com/user-attachments/assets/f97fc94a-5874-4a3f-a1bd-534e3b338be9)
![League-Ratio-Photo](https://github.com/user-attachments/assets/8d967921-c8a0-40d7-bbd4-ee5b1a3c2f6c)

We create another plot function called plot_num_summary(dataframe) to see the whole summary of numerical columns due to the high quantity of them:

![Plot_All_Numerical_Variables](https://github.com/user-attachments/assets/19d358d8-9aa7-4757-b9c0-feed63e0bc6f)

---

## Target Analysis

For target analysis, we examined the relationship between the target variable and numerical or categorical features to understand how different numeries or categories impact the target outcomes.

[Target Analysis with numerical](https://github.com/user-attachments/assets/3523dd34-4880-422d-9669-7e53d4b52e9f)

![Target Analysis with categorical](https://github.com/user-attachments/assets/23af65f0-721b-4732-b669-1604722cb8a0)

## Correlation Analysis

To analyze correlations between numerical columns we create a function called correlated_cols(dataframe):

![Correlation Analysis](https://github.com/user-attachments/assets/335d6d40-5e68-444e-9ce8-d22c60380aca)

# Pipeline

"This pipeline combines time-based and user-based averages into a single process for efficient rating calculation."

```
df = load_dataset(path_dataset)
print(20*"#", "General Information About To Dataset")
check_df(df, head)
print(20*"#", "Analysis of Categorical and Numerical Variables")
cat_cols, num_cols, cat_but_car, num_but_cat = grab_col_names(df, cat_th=cat_th, car_th=car_th, report=report)
cat_summary_df(df)
num_summary_df(df)
print(20*"#", "Target Analysis", 20*"#")
if len(num_cols)>1:
    print(20*"#", "Target Analysis - Numerical", 20*"#")
    target_summary_with_num_df(df, target)
if len(cat_cols)>1:
    print(20*"#", "Target Analysis - Categorical", 20*"#")
    target_summary_with_cat_df(df, target)
print(20*"#", "Correlation Analysis", 20*"#")
drop_list = high_corralated_cols(df, corr_th=corr_th, plot=plot, remove=remove)
print(20*"#", "Plot All Numerical Variables", 20*"#")
plot_num_summary(df)
```
