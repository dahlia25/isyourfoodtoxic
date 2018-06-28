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

> Remove all leading white spaces in cell entries for all Dataframe columns

`result0 = result.drop_duplicates(subset=['Year','Month','State','Location','Ingredient','Species','Serotype/Genotype','Illnesses'])`  
`result0['Ingredient'] = result0['Ingredient'].str.lstrip(' ')`  
`result0['Species'] = result0['Species'].str.lstrip(' ')`  
`result0['Serotype/Genotype'] = result0['Serotype/Genotype'].str.lstrip(' ')`  
`result0['Location'] = result0['Location'].str.lstrip(' ')`  
`result0['State'] = result0['State'].str.lstrip(' ')`  

> Convert all *Month* names into numbers, using dictionary

`month_dict = {'January':'01','February':'02','March':'03','April':'04','May':'05','June':'06','July':'07','August':'08','September':'09','October':'10','November':'11','December':'12',}`  
`result['Month'] = result['Month'].apply(lambda x: month_dict[x])`  

> Change Status to binary numbers: Confirmed (1) and Suspected (0)

`status_dict = {'Confirmed':'1', 'Suspected':'0'}`  
`result['Status'] = result['Status'].apply(lambda x: status_dict[x])`  

> Change all values in Illnesses, Hospitalizations & Fatalities to 1 or 0 (yes or no)

`result0.loc[result0.Illnesses > 0, 'Illnesses'] = 1`  
`result0.loc[result0.Hospitalizations > 0, 'Hospitalizations'] = 1`  
`result0.loc[result0.Fatalities > 0, 'Fatalities'] = 1`  

> Transform all cateogrical data to One Hot Encoding (OHE)

`del result0['Food'] #do not neet this feature since we have Ingredient`  

`month = result0['Month']`  
`states = result0['State']`  
`location = result0['Location']`  
`ingt = result0['Ingredient']`  
`ssp = result0['Species']`  
`sgt = result0['Serotype/Genotype']`  

`result0_month = pd.get_dummies(month)`  
`result0_states = pd.get_dummies(states)`  
`result0_location = pd.get_dummies(location)`  
`result0_ingt = pd.get_dummies(ingt)`  
`result0_ssp = pd.get_dummies(ssp)`  
`result0_sgt = pd.get_dummies(sgt)`  

`combine = pd.concat([result0_states, result0_location, result0_ingt, result0_ssp, result0_sgt], axis=1)`  
`combine = pd.concat([result0_location, result0_ingt, result0_ssp, result0_sgt], axis=1)` 
`combine = result0_location`  

`combine.insert(loc=0, column='Year', value=result0['Year'])`  
`combine.insert(loc=1, column='Month', value=result0['Month'])`  
`combine.insert(loc=2, column='Population', value=result0['Population'])`  
`combine.insert(loc=3, column='Status', value=result0['Status'])`  
`combine.insert(loc=4, column='Illnesses', value=result0['Illnesses'])`  
`combine.insert(loc=5, column='Hospitalizations', value=result0['Hospitalizations'])`  
`combine.insert(loc=6, column='Fatalities', value=result0['Fatalities'])`  
**I can manipulate feature vs. label (i.e. Hospitalizations) any time be coming back to this section.
