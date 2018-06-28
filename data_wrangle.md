# Data Wrangle & Feature Engineering

Here are the steps I took and codes for data cleaning and transforming.

---

### a. Import all libraries and packages that you may need

`import pandas as pd`  
`import numpy as np`  
`import matplotlib.pyplot as plt`

### b. Read in CSV file as a Pandas Dataframe, and remove all missing or 'NaN' values

`outbreaks = pd.read_csv("~outbreaks.csv")`  
`df = outbreaks.dropna().reset_index()`  

### c. Unstack all multiple cell entries into individual rows for each feature/column

> Separate multiple entries in 'Species' column cell into rows

`sp = df['Species'].str.split(';', expand=True).stack()`  
`i = sp.index.get_level_values(0)`  
`good_sp = df.loc[i].copy().reset_index()`  
`good_sp['Species'] = sp.values`  

`del good_sp['index']`  
`del good_sp['level_0']`  

> Separate multiple entries in 'Ingredient' column cell into rows

`ing = good_sp['Ingredient'].str.split(';', expand=True).stack()`  
`j = ing.index.get_level_values(0)`  
`good_ing = good_sp.loc[j].copy().reset_index()`  
`good_ing['Ingredient'] = ing.values`  

`del good_ing['index']`  

> Separate multiple entries in 'Location' column cell into rows

`loca = good_ing['Location'].str.split(';', expand=True).stack()` 
`k = loca.index.get_level_values(0)`  
`good_loca = good_ing.loc[k].copy().reset_index()`  
`good_loca['Location'] = loca.values`  

`del good_loca['index']`  

> Separate multiple entries in 'Food' column cell into rows

`fd = good_loca['Food'].str.split(';', expand=True).stack()`  
`l = fd.index.get_level_values(0)`  
`good_fd = good_loca.loc[l].copy().reset_index()`  
`good_fd['Food'] = fd.values`  

`del good_fd['index']`  

> Separate multiple entries in 'Serotype/Genotype' column cell into rows

`sg = good_fd['Serotype/Genotype'].str.split(';', expand=True).stack()`  
`m = sg.index.get_level_values(0)`  
`good_sg = good_fd.loc[m].copy().reset_index()`  
`good_sg['Serotype/Genotype'] = sg.values`  

> Separate multiple entries in 'Status' column cell into rows

`stat = good_sg['Status'].str.split(';', expand=True).stack()`  
`n = stat.index.get_level_values(0)`  
`good_stat = good_sg.loc[n].copy().reset_index()`  
`good_stat['Status'] = stat.values`  

`good_df = good_stat`  
`del good_df['level_0']`  
`del good_df['index']`  

> Standardize all cell entries

`good_df['Species'].str.replace(' ', '')`  
`good_df['Ingredient'].str.replace(' ', '')`  
`good_df['Location'].str.replace(' ', '')`  
`good_df['Food'].str.replace(' ', '')`  
`good_df['Serotype/Genotype'].str.replace(' ', '')`  
`good_df['Status'].str.replace(' ', '')`  

`good_df.drop_duplicates(subset=['Year','Month','State','Location','Food','Ingredient','Species','Serotype/Genotype','Illnesses'], inplace=True)`  
