# eda_utils_py 

[![build](https://github.com/UBC-MDS/eda_utils_py/actions/workflows/build.yml/badge.svg)](https://github.com/UBC-MDS/eda_utils_py/actions/workflows/build.yml) ![](https://github.com/chuangw46/eda_utils_py/workflows/build/badge.svg) [![codecov](https://codecov.io/gh/UBC-MDS/eda_utils_py/branch/main/graph/badge.svg)](https://codecov.io/gh/UBC-MDS/eda_utils_py) [![Deploy](https://github.com/UBC-MDS/eda_utils_py/actions/workflows/deploy.yml/badge.svg)](https://github.com/UBC-MDS/eda_utils_py/actions/workflows/deploy.yml) [![Documentation Status](https://readthedocs.org/projects/eda_utils_py/badge/?version=latest)](https://eda_utils_py.readthedocs.io/en/latest/?badge=latest)

## Overview 

As data rarely comes ready to be used and analyzed for machine learning right away, this package aims to help speed up the process of cleaning and doing initial exploratory data anslysis (EDA). The package focuses on the tasks of dealing with outlier and missing values, scaling and correlation visualization.

## Installation

```bash
$ pip install -i https://test.pypi.org/simple/ eda_utils_py
```

## Functions

The four functions contained in this package are as follows:
- `imputer`: A function to impute missing values
- `outlier_identifier`: A function to identify and deal with outliers
- `cor_map`: A function to plot a correlation matrix of numeric columns in the dataframe
- `scale` A function to scale numerical values in the dataset


## Our Place in the Python Ecosystem

While Python packages with similar functionalities exist, this package aims to simplify the amount of code necessary for these functions and outputs. Packages with similar functionality are as follows:

- [Sklearn.preprocessing]( https://scikit-learn.org/stable/modules/preprocessing.html)
- [Altair Heatmap](https://altair-viz.github.io/gallery/layered_heatmap_text.html)

## Dependencies

- Please see a list of dependencies [here](pyproject.toml).

## Usage
The eda_utils_py package will help you in your exploratory data analysis portion of your work.

eda_utils_py includes multiple custom functions to perform initial exploratory analysis on any input data describing the structure and the relationships present in the data. Depending on the function, the generated output can be obtained in object or graphical form. 

```python
import pandas as pd
from eda_utils_py import eda_utils_py

data = pd.DataFrame({
         'SepalLengthCm':[5.1, 4.9, 4.7],
         'SepalWidthCm':[1.4, 1.4, 1.3],
         'PetalWidthCm':[0.2, 0.1, 0.2],
         'Species':['Iris-setosa','Iris-virginica', 'Iris-germanica']
         })

data_with_NA = pd.DataFrame({
         'SepalLengthCm':[5.1, 4.9, 4.7],
         'SepalWidthCm':[1.4, 1.4, 1.3],
         'PetalWidthCm':[0.2, 0.1, None]
         })

data_with_outlier = pd.DataFrame({
         'SepalLengthCm':[5.1, 4.9, 4.7, 5.2, 5.1, 5.2, 5.1, 4.8],
         'SepalWidthCm':[1.4, 1.4, 1.3, 1.2, 1.2, 1.3, 1.6, 1.3],
         'PetalWidthCm':[0.2, 0.1, 30, 0.2, 0.3, 0.1, 0.4, 0.5]
         })
         
data_with_scale = pd.DataFrame({'SepalLengthCm':[1, 0, 0, 3, 4], 
         'SepalWidthCm':[4, 1, 1, 0, 1], 
         'PetalWidthCm':[2, 0, 0, 2, 1],
         'Species':['Iris-setosa','Iris-virginica', 'Iris-germanica', 'Iris-virginica','Iris-germanica']})      
```

The eda_utils_py package contains functions that will help you to:
- **Impute**: Resolve skewed data by identifying missing data and outlier and provide corresponding remedy.

```python
imputer(data_with_NA)
```
Output of `imputer()`:

![imputer_output](images/imputer_output.png)

- **Identify Outliers**: Identify and deal with outliers in the dataset.

```python
outlier_identifier(data_with_outlier, method = "median")
```
Output of `outlier_identifier()`:

![outlier_output](images/outlier_output.png)

- **Correlation Heatmap Plotting**: Easily plot a correlation matrix along with its values to help explore data.

```python
numerical_columns = ['SepalLengthCm','SepalWidthCm','PetalWidthCm']

cor_map(data, numerical_columns, col_scheme = 'purpleorange')

```
Output of `cor_map()`:

![cor_map_output](images/cor_map.output.png)

- **Scaling**: Scale the data in preperation for future use in machine learning projects.

```python
numerical_columns = ['SepalLengthCm','SepalWidthCm','PetalWidthCm']

scale(data, numerical_columns, scaler="minmax")

```
Output of `scale()`:

![scale_output](images/scale_output.png)

## Documentation

The official documentation is hosted on Read the Docs: https://eda_utils_py.readthedocs.io/en/latest/

## Contributors

This package is authored by Chuang Wang, Fatime Selimi, Jiacheng Wang, and Micah Kwok as part of the course project in DSCI-524 (UBC-MDS program). You can see the list of all contributors in the [contributors tab](https://github.com/UBC-MDS/eda_utils_py/graphs/contributors).

We welcome and recognize all contributions. If you wish to participate, please review our [contributing guidelines](https://github.com/UBC-MDS/eda_utils_py/blob/main/CONTRIBUTING.rst). 

### Credits

This package was created with Cookiecutter and the UBC-MDS/cookiecutter-ubc-mds project template, modified from the [pyOpenSci/cookiecutter-pyopensci](https://github.com/pyOpenSci/cookiecutter-pyopensci) project template and the [audreyr/cookiecutter-pypackage](https://github.com/audreyr/cookiecutter-pypackage).
