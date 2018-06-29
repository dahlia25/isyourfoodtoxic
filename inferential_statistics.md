# Inferential Statistics

We did not perform inferential statistics because it is ineffective to practice it on categorical data.
Instead, we performed the **chi-squared independence test** on a couple hypotheses.

---

## Hypothesis

### Null Hypotheses (H0):

1. Ingredient and Species are independent.
2. Ingredient and Location are independent.
3. Ingredient and State are independent.
4. Species and Serotype/Genotype are independent.
5. Species and Month are independent.
6. Species and State are independent.

### Alternative Hypotheses (H1):

1. Ingredient and Species are not independent.
2. Ingredient and Location are not independent.
3. Ingredient and State are not independent.
4. Species and Serotype/Genotype are not independent.
5. Species and Month are not independent.
6. Species and State are not independent.

---

## Performing Chi-Squared Test on Hypotheses

### Define a Chi-Squared Function
This function needs to be able to take in the DataFrame and 2 Features as inputs, and create a contingency table.
The contingency table should show the observed frequencies of all variables for the two given features.

> Chi-Squared Independence Test function

`def chi_sq(dataframe, firstfeature, secondfeature):`  
  `col = list(dataframe[secondfeature])`  
  
  `grp_size = dataframe.groupby([firstfeature, col]).size()`  
  
  `c_sum = grp_size.unstack(firstfeature).fillna(0)`  
  `chi_stats = chi2_contingency(c_sum)`  
  
  `return(chi_stats)`  

> Example:

Input: `chi_sq(df, 'Species', 'State')`  
Output:
`1019.3890740730609, #chi-squared value`  
 `9.4171399169721465e-35, #p-value`  
 `520, #degrees of freedom`  
 `array([[  1.42450142e-03,   5.69800570e-03,   8.54700855e-03,   #Expected frequency matrix/array`  
           `1.42450142e-03,   1.42450142e-03,   1.26780627e-01,`  
           `2.27920228e-02,   7.83475783e-02,   1.42450142e-03,`  
           `7.42165242e-01,   4.27350427e-03,   1.42450142e-03,`  
           `1.42450142e-03,   2.84900285e-03],`  
        `[  2.84900285e-03,   1.13960114e-02,   1.70940171e-02,`  
           `2.84900285e-03,   2.84900285e-03,   2.53561254e-01,`  
           `4.55840456e-02,   1.56695157e-01,   2.84900285e-03,`  
           `1.48433048e+00,   8.54700855e-03,   2.84900285e-03,`  
           `2.84900285e-03,   5.69800570e-03],`  
           `...`  
        `[  1.70940171e-02,   6.83760684e-02,   1.02564103e-01,`  
           `1.70940171e-02,   1.70940171e-02,   1.52136752e+00,`  
           `2.73504274e-01,   9.40170940e-01,   1.70940171e-02,`  
           `8.90598291e+00,   5.12820513e-02,   1.70940171e-02,`  
           `1.70940171e-02,   3.41880342e-02]]))`  

**The alpha or significance value is set at 0.01.**

Since we have a p-value of 9.4171399e-35 that is smaller than the alpha, we reject the null hypothesis that
states Species and State are independent of each other.
