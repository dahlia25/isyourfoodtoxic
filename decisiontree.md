# How to visualize Decision Trees for RandomForest

We visualize Decision Trees improve feature engineering and increase accuracy of our tree models.

---

## Graphviz is a great Python package to visualize Decision Trees. 

### How to download the Graphviz package onto Anaconda for PC (since I am a Windows 10 user)

1. Open **Anaconda Prompt**.  
2. Enter *conda search graphviz*, and you should see something similar to this:  

> &nbsp;  Name       &nbsp;&nbsp;&nbsp;           Version   &nbsp;&nbsp;&nbsp;        Build  Channel  
> graphviz     &nbsp;&nbsp;            2.38.0      &nbsp;&nbsp;&nbsp;&nbsp;        2  pkgs/free  
> graphviz     &nbsp;&nbsp;            2.38.0      &nbsp;&nbsp;&nbsp;&nbsp;        4  pkgs/free  

3. Enter *conda install graphviz=2.38.0*.  
4. Enter *y* to say yes to install package.

---

## Graphing RF Classifier Decision Tree  

`from sklearn.tree import DecisionTreeClassifier`  
`from sklearn import tree`  
`import graphviz`  

`dt_clf = tree.DecisionTreeClassifier(criterion = 'gini',`  
`                                  max_depth = 1,`  
`                                  max_features = 'sqrt',`  
`                                  max_leaf_nodes = 2,`  
`                                  min_samples_leaf = 5,`  
`                                  min_samples_split = 2,`  
`                                  random_state = 55,`  
`                                  class_weight = {0:2, 1:1}`  
`                                 )`  

`dt_clf.fit(train_features, train_labels)`  

`dot_data = tree.export_graphviz(dt_clf, out_file = None)`  
`graph = graphviz.Source(dot_data)`  
`graph`  

Output:  

![](https://raw.githubusercontent.com/dahlia25/isyourfoodtoxic/master/location.RFcw.png)
