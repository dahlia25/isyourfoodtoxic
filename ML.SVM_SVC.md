# Machine Learning with SVM SVC

I also selected the SVM SVC for the purpose of comparing it with the RandomForest Classifier. 
One of the pros of SVM SVC is that it can process data with high dimensionality.

---

`from sklearn import svm, tree`  
`from sklearn.grid_search import GridSearchCV`  
`from sklearn.cross_validation import train_test_split`  
`import pprint as pp`  

> Set up features & labels  

`labels = np.array(df['Hospitalizations'])`  

`features = df.drop('Hospitalizations', axis=1)`  
`feature_list = list(features.columns)`  
`features = np.array(features)`  

> Split training and testing data  

`train_features, test_features, train_labels, test_labels = train_test_split(features, labels, test_size = 0.2, random_state = 66)`  

Take a look at the sample sizes for training and test data:

`print('Training Features Shape:', train_features.shape)`  
`print('Training Labels Shape:', train_labels.shape)`  
`print('Testing Features Shape:', test_features.shape)`  
`print('Testing Labels Shape:', test_labels.shape)`  

> Set up SVM SVC model and its parameters  

`svm_clf = svm.SVC(random_state=66,`  
`                  C = 1.0,`  
`                  cache_size = 0.2,`  
`                  coef0 = 1,`  
`                  decision_function_shape = 'ovr',`  
`                  gamma = 0.7,`  
`                  kernel = 'poly')`  

`svm_fit = svm_clf.fit(train_features, train_labels)`  
`svm_predict = svm_clf.predict(test_features)`  

`print("Accuracy: ")`  
`print(svm_clf.score(test_features, test_labels)) # accuracy score`  
`print(result0.Hospitalizations.value_counts()) # numbers of 1's (yes) and 0's (no) in whole dataset`  
`print(pd.Series(svm_predict).value_counts()) # numers of 1's and 0's the model predicted`  
`print(pd.Series(test_labels).value_counts()) # nubers of 1's and 0's in test set`  

> I used the following code to find all parameters of SVM SVC model:

`svm.SVC.get_params(svm_clf).keys()`  

> Tuning Parameters for Hospitalizations w/ GridSearchCV (SVM SVC)  

`labels = np.array(df['Hospitalizations'])`  

`features = df.drop('Hospitalizations', axis=1)`  
`feature_list = list(features.columns)`  
`features = np.array(features)`  

`param = {'C': [0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1.0],`  
`         'cache_size': [0.0, 0.2, 0.4, 0.6, 0.8, 1.0],`  
`         'coef0': [1, 3, 5, 10],`  
`         'decision_function_shape': ['ovr', 'ovo'],`  
`         'gamma': [0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1.0],`  
`         'kernel': ['linear', 'rbf', 'poly', 'sigmoid],`  
`        }`  

`GSclf = GridSearchCV(estimator = svm.SVC(random_state = 66),`  
`                    param_grid = param,`  
`                    cv = 5,`  
`                    refit = True,`  
`                    error_score = 0,`  
`                    n_jobs = -1`  
`                    )`  

`GSclf.fit(features, labels)`  

`cvresults = sorted(GSclf.cv_results_.keys())`  
`bestparams = GSclf.best_params_`  
`pp.pprint(bestparams)`  
