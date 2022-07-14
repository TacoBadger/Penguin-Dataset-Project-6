# Penguin Dataset
Palmer Archipelago (Antarctica) penguin data in kaggle.
![](https://github.com/TacoBadger/Penguin-Dataset/blob/main/penguin.png?raw=true)

## Data Visualization with Python
We will explore and prepare data visualization for the penguin dataset. We will explore matplot lib and different types of data visualizations.

## Author
- [@TacoBadger](https://github.com/TacoBadger)

## Table of Contents
  - [Objectives](#objectives)
  - [Dataset](#dataset)
  - [Summary](#summary)
  - [Important Definitions](#important-definitions)
  - [Importing the packages](#importing-the-packages)
  - [Processing the data for analysis](#processing-the-data-for-analysis)
  - [Checking the Dataset with Data Visualizations](#checking-the-dataset-with-data-visualizations)
  - [Analysis of Culmen Length and Depth in penguins](#analysis-of-culmen-length-and-depth-in-penguins)
  - [Relationship between culmen length and culmen depth](#relationship-between-culmen-length-and-culmen-depth)
  - [Analysis of Flipper Length and Body Mass in penguins](#analysis-of-flipper-length-and-body-mass-in-penguins)
  - [Analyzing of mass with respective of species](#analyzing-of-mass-with-respective-of-species)
  - [In Summary](#in-summary)

## Objectives
We will do some data visualization with data analysis about the penguin dataset in kaggle.
- Basic EDA (Exploratory Data Analysis)
- Matplotlib (Data Visualization)

## Dataset
Here is the dataset used: [Palmer Archipelago (Antarctica) penguin data](https://www.kaggle.com/datasets/parulpandey/palmer-archipelago-antarctica-penguin-data)

Palmer Archipelago (Antarctica) penguin data
Data were collected and made available by Dr. Kristen Gorman and the Palmer Station, Antarctica LTER, a member of the Long Term Ecological Research Network.

Thank you to Dr. Gorman, Palmer Station LTER and the LTER Network! Special thanks to Marty Downs (Director, LTER Network Office) for help regarding the data license & use.

License & citation
Data are available by CC-0 license in accordance with the Palmer Station LTER Data Policy and the LTER Data Access Policy for Type I data.

Please cite this data using: Gorman KB, Williams TD, Fraser WR (2014) Ecological Sexual Dimorphism and Environmental Variability within a Community of Antarctic Penguins (Genus Pygoscelis). PLoS ONE 9(3): e90081. [doi:10.1371/journal.pone.0090081](doi:10.1371/journal.pone.0090081).

## Summary
The data folder contains two CSV files. For intro courses/examples, you probably want to use the first one (penguins_size.csv).
- penguins_size.csv: Simplified data from original penguin data sets. Contains variables:
- species: penguin species (Chinstrap, Adélie, or Gentoo)
- culmen_length_mm: culmen length (mm)
- culmen_depth_mm: culmen depth (mm)
- flipper_length_mm: flipper length (mm)
- body_mass_g: body mass (g)
- island: island name (Dream, Torgersen, or Biscoe) in the Palmer Archipelago (Antarctica)
- sex: penguin sex

## Important Definitions
**Python**  is a computer programming language often used to build websites and software, automate tasks, and conduct data analysis. Python is a general-purpose language, meaning it can be used to create a variety of different programs and isn't specialized for any specific problems.

We will use the following packages:
- **pandas** *is mainly used for data analysis and associated manipulation of tabular data in Dataframes.*
- **numpy** *a Python library used for working with arrays. It also has functions for working in domain of linear algebra, fourier transform, and matrices.*
- **seaborn** *is a library that uses Matplotlib underneath to plot graphs. It will be used to visualize random distributions.*
- **matplotlib** *is a cross-platform, data visualization and graphical plotting library for Python and its numerical extension NumPy. As such, it offers a viable open source alternative to MATLAB.*

## Importing the packages
We will import all the packages that we need to load the dataset and create our visualization.

```bash 
import pandas as pd 
import numpy as np
import seaborn as sns 
import matplotlib.pyplot as plt 
%matplotlib inline

import warnings
warnings.filterwarnings('ignore')
```

**Pandas and numpy** for EDA, **Seaborn and matplotlib** for data viz.

The **filter warnings** is just to ignore the red text boxes when running an output.

**Load the dataset**

```bash 
penguin = pd.read_csv("../input/palmer-archipelago-antarctica-penguin-data/penguins_size.csv")
```

We will have a look at the first 5 rows of the dataset.

```bash 
penguin.head(5)
```
![](https://github.com/TacoBadger/Penguin-Dataset/blob/main/penguin.png?raw=true)

We will have a look at the last 5 rows of the dataset.

```bash 
penguin.tail(5)
```
![](https://github.com/TacoBadger/Penguin-Dataset/blob/main/penguin.png?raw=true)

We can also take a look at the summary of the dataset, which includes number of rows and columns.
```bash 
penguin.shape
```
**The dataset has a total of 344 rows and 7 columns.**

We can also take a peak at column names.
```bash 
penguin.columns
```

**The dataset consists of 7 columns.**

- species: penguin species (Chinstrap, Adélie, or Gentoo)
- island: island name (Dream, Torgersen, or Biscoe) in the Palmer Archipelago (Antarctica)
- culmen_length_mm: culmen length (mm)
- culmen_depth_mm: culmen depth (mm)
- flipper_length_mm: flipper length (mm)
- vbody_mass_g: body mass (g)
- sex: penguin sex
