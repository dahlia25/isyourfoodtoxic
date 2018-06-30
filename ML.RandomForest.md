# Machine Learning with RandomForest Classifier

I selected the RandomForest Classifier (RF) to predict whether a specified feature caused hospitalizations.
The 5-fold cross validation was implemented into the RF model, and I set the test size to be 20 percent.
Below is the code.

---

`from sklearn.grid_search import GridSearchCV`  
`from sklearn.cross_validation import train_test_split`  
`from sklearn.ensemble import RandomForestClassifier`  
`from sklearn.metrics import mean_squared_error, r2_score, accuracy_score`  
`from sklearn.tree import DecisionTreeClassifier` 
`import pprint as pp`  

> Set up features & labels

`labels = np.array(df['Hospitalizations'])`  

`features = df.drop('Hospitalizations', axis=1)`  
`feature_list = list(features.columns)`  
`features = np.array(features)`  

> Split training and testing data

`train_features, test_features, train_labels, test_labels = train_test_split(features, labels, test_size = 0.2, random_state = 55)`  

I printed the shape of the training and test sets to see the sample size.

`print('Training Features Shape:', train_features.shape)`  
`print('Training Labels Shape:', train_labels.shape)`  
`print('Testing Features Shape:', test_features.shape)`  
`print('Testing Labels Shape:', test_labels.shape)`  

> Set up the RF Classifier and its parameters, and fit the training set

`rf = RandomForestClassifier(criterion = 'gini',`    
`                            max_depth = 1,`    
`                            max_features = 'sqrt',`    
`                            max_leaf_nodes = 3,`    
`                            min_samples_leaf = 1,`    
`                            min_samples_split = 2,`    
`                            n_estimators = 50,`    
`                            random_state = 55,`    
`                            class_weight = {0:2, 1:1}`    
`                           )`  

`fit = rf.fit(train_features, train_labels)`  
`predict = rf.predict(test_features)`  

`importances = list(rf.feature_importances_)`  

> List of tuples with variable and importance  

`feature_importances = [(feature, round(importance, 2)) for feature, importance in zip(feature_list, importances)]`  

> Sort the feature importances by most important first  

`feature_importances = sorted(feature_importances, key = lambda x: x[1], reverse = True)`  

> Print out the feature and importances  

`[print('Variable: {:30} Importance: {}'.format(*pair)) for pair in feature_importances]`  

`print("Accuracy: ")`  
`print(rf.score(test_features, test_labels))`  

`print(result0.Hospitalizations.value_counts()) # actual numbers of 1's (yes) and 0'2 (no) in whole dataset`  
`print(pd.Series(predict).value_counts()) # actual numbers of 1's and 0's predicted`  
`print(pd.Series(test_labels).value_counts()) # actual numbers of 1's and 0's in test set`  

If you're not sure what the parameters are for RF, use this:  

`RandomForestClassifier.get_params(rf).keys()`  

> Tuning Parameters for Hospitalizations w/ GridSearchCV (RandomForestClassifier)  

`labels = np.array(df['Hospitalizations'])`  

`features = df.drop('Hospitalizations', axis=1)`  
`feature_list = list(features.columns)`  
`features = np.array(features)`  

`param = {'n_estimators': [1, 5, 10, 25, 50, 75, 100],`    
`         'criterion': ['gini', 'Entropy],`    
`         'max_depth': [1, 2, 3, 4, 5],`    
`         'max_features': ['sqrt', 'log2'],`    
`         'max_leaf_nodes': [1, 2, 3, 4, 5],`    
`         'min_samples_leaf': [1, 2, 3, 4, 5],`    
`         'min_samples_split': [1, 2, 3, 4, 5]`    
`        }`  

`GSclf = GridSearchCV(estimator = RandomForestClassifier(random_state = 55, class_weight = {0:2, 1:1}),`    
`                     param_grid = param,`    
`                     cv = 5,`    
`                     refit = True,`    
`                     error_score = 0,`    
`                     n_jobs = -1`    
`                    )`  

`GSclf.fit(train_features, train_labels)`  

`scores = GSclf.grid_scores_`  

`cvresults = sorted(GSclf.cv_results_.keys())`  
`bestparams = GSclf.best_params_`   
`pp.pprint(bestparams)`  
