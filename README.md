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
![](https://github.com/TacoBadger/Penguin-Dataset/blob/main/Tables/head.png?raw=true)

We will have a look at the last 5 rows of the dataset.

```bash 
penguin.tail(5)
```
![](https://github.com/TacoBadger/Penguin-Dataset/blob/main/Tables/tail.png?raw=true)

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

## Processing the data for analysis
We will fix null values and check for datatypes. 

We can also check for the datatypes, nullvalues and columns.
```bash 
penguin.info()
```
![](https://github.com/TacoBadger/Penguin-Dataset/blob/main/EDA/datatypes.png?raw=true)

We can also check for null values in the dataset.
```bash 
penguin.isna().sum()
```
![](https://github.com/TacoBadger/Penguin-Dataset/blob/main/EDA/null.png?raw=true)

In penguin data set, there are **7 columns and 344 rows**. There are few null values present in **culmen_length_mm, culmen_depth_mm, flipper_length_mm, body_mass_g and sex** columns.

We can fill in the missing values like the length and depth with the mean.
```bash 
penguin["culmen_length_mm"] = penguin["culmen_length_mm"].fillna(value = penguin["culmen_length_mm"].mean())
penguin["culmen_depth_mm"] = penguin["culmen_depth_mm"].fillna(value = penguin["culmen_depth_mm"].mean())
penguin["flipper_length_mm"] = penguin["flipper_length_mm"].fillna(value = penguin["flipper_length_mm"].mean())
penguin["body_mass_g"] = penguin["body_mass_g"].fillna(value = penguin["body_mass_g"].mean())
```

Let us work on missing values and let us see what we can do with it.
```bash 
penguin['sex'] = penguin['sex'].fillna('MALE')
penguin[penguin['sex']=='.']
```

```bash 
penguin.loc[336,'sex'] = 'MALE'
```

This adds a male to the missing sex in row 336.

Let's check if there are anymore missing values.

```bash 
penguin.isna().sum()
```
![](https://github.com/TacoBadger/Penguin-Dataset/blob/main/EDA/null1.png?raw=true)

**Congrats!** There are **no null values** in the data set now. So we can go ahead and **work on EDA!**

## Checking the Dataset with Data Visualizations
We will now do further EDA on the dataset we cleaned and processed.

Checking the dataset stats.
```bash 
penguin.describe()
```

Let's check count for each species.
```bash 
penguin['species'].value_counts()
```

The penguin dataset consists of **344 data instances**. There are **3 classes(species) - Adelie, Gentoo and Chinstrap.**

We can make a plot for this one.
```bash 
sns.countplot('species',data=penguin, palette=('Orange', 'Pink', 'Blue'))
plt.show()
```
![](https://github.com/TacoBadger/Penguin-Dataset/blob/main/Viz/species%20count.png?raw=true)

The penguins dataset has different number of samples for each species. **Adelie are the highest number followed by Gentoo and Chinstrap.**

Let's also check the island names and how many penguins are there in each island.
```bash 
penguin['island'].value_counts()
```

We can also plot a bar chart for this one.
```bash 
sns.countplot(x = "island", data = penguin)
```
![](https://github.com/TacoBadger/Penguin-Dataset/blob/main/Viz/island.png?raw=true)

**Most of the Penguins belong to Biscoe island and least are from Torgersen.**

## Analysis of Culmen Length and Depth in penguins
Let's find out the culmmen length and culmen depth among penguins.

First let's start with culmen length.
```bash 
sns.catplot(x="sex", y="culmen_length_mm", hue="species", data=penguin, kind="bar", palette=('Orange', 'Pink', 'Blue'))
```
![](https://github.com/TacoBadger/Penguin-Dataset/blob/main/Viz/culmen%20length.png?raw=true)

**Chinstrap penguins have highest culmen length in both male and female followed by Gentoo and Adelie.**

Then let's check out culmen depth.

```bash 
sns.catplot(x="sex", y="culmen_depth_mm", hue="species", data=penguin, kind="bar", palette=('Orange', 'Pink', 'Blue'))
```
![](https://github.com/TacoBadger/Penguin-Dataset/blob/main/Viz/culmen%20depth.png?raw=true)

**Chinstrap and Adelie penguins have almost same culmen depth in both male and female while Gentoo has the lowest.**

## Relationship between culmen length and culmen depth
Let us check the relationship of between the culmen_length and culmen_depth!

```bash 
sns.scatterplot(x = penguin.culmen_length_mm, y = penguin.culmen_depth_mm, hue = penguin.species, palette=('Orange', 'Pink', 'Blue'))
```
![](https://github.com/TacoBadger/Penguin-Dataset/blob/main/Viz/scatterplot%20relationship.png?raw=true)

**From the scatter plot above we can see that:**

- 3 groups of species can be identified based on culmen length and depth feature
- Each of the species culmen_length and culmen_depth fall in a certain range.

## Analysis of Flipper Length and Body Mass in penguins
Let's find out the Flipper Length and Body Mass among penguins.

```bash 
sns.catplot(x="sex", y="flipper_length_mm", hue="species", data=penguin, kind="bar", palette=('Orange', 'Pink', 'Blue'))
```
![](https://github.com/TacoBadger/Penguin-Dataset/blob/main/Viz/flipper%20length.png?raw=true)

**Gentoo penguins have highest flipper length in both male and female.**

```bash 
sns.catplot(x="sex", y="body_mass_g", hue="species", data=penguin, kind="bar", palette=('Orange', 'Pink', 'Blue'))
```
![](https://github.com/TacoBadger/Penguin-Dataset/blob/main/Viz/body%20mass.png?raw=true)

**Gentoo penguins have highest body weight in both male and female.**

And lastly we will analyze the mass of the species.

```bash 
sns.boxplot(x = penguin.sex, y = penguin.body_mass_g, hue = penguin.species, palette=('Orange', 'Pink', 'Blue'))
```
![](https://github.com/TacoBadger/Penguin-Dataset/blob/main/Viz/boxplot.png?raw=true)

**From the box plot above we can see that:**

- Male penguins of all species are heavier than female penguins.
- Gentoo penguins are heavier than Adelie and Chinstrap penguins.

## In Summary

We can see that penguins may differ with their culmen length and depth and especially their body mass, let's summarize everything we found out.

**Regarding the analysis of Culmen Length and Depth in penguins**
- Chinstrap penguins have highest culmen length in both male and female followed by Gentoo and Adelie.
- Chinstrap and Adelie penguins have almost same culmen depth in both male and female while Gentoo has the lowest.

**Regarding the relationship between culmen_length and culmen_depth**
- 3 groups of species can be identified based on culmen length and depth feature
- Each of the species culmen_length and culmen_depth fall in a certain range.

**Based on the analysis of Flipper Length and Body Mass in penguins**
- Gentoo penguins have highest flipper length in both male and female.
- Gentoo penguins have highest body weight in both male and female.

**And lastly regarding the analysis of mass with respective of species**
- Male penguins of all species are heavier than female penguins.
- Gentoo penguins are heavier than Adelie and Chinstrap penguins.

## Explore our Tableau Public
- [@TacoBadger](https://public.tableau.com/app/profile/taco.badger)

## Explore our Notebook
- [@TacoBadger](https://www.kaggle.com/code/cryptocosy/penguin-analysis)

## What is Next?
We have finished our practice! This dataset was the most interesting and fun out of all the dataset I worked with.
- I could have also improved my analysis by adding more relationships or correlations of different values.
- I could also practice more types of plot regarding the additional analysis.
- I can also need to learn more advanced functions about plots for the next practice.

Thank you for reading my case study!
