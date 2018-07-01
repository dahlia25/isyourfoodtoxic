Here are the most optimized parameters from GridSearchCV for RandomForest Classifier and SVM SVC for each feature.

Target: Hospitalizations

# RandomForest Classifier

## Ingredients: (train_data shape [yes:no] = 478:224) 

(w/o class_weight)--accuracy = 0.709, precision = 141:0  
criterion = gini  
max depth = 2  
max_features = sqrt  
max_leaf_nodes = 4  
min_samples_leaf = 2  
min_samples_split = 2   
n_estimators = 10  

(w/ class_weight)--accuracy = 0.730, precision = 130:11  
criterion = gini  
max depth = 1  
max_features = sqrt  
max_leaf_nodes = 3  
min_samples_leaf = 1  
min_samples_split = 2  
n_estimators = 50  

## Species: (train_data shape [yes:no] = 478:224) 

(w/o class_weight)--accuracy = 0.773, precision = 124:17  
criterion = gini  
max depth = 2  
max_features = sqrt  
max_leaf_nodes = 4  
min_samples_leaf = 2  
min_samples_split = 2  
n_estimators = 10  

(w/ class_weight)--accuracy = 0.773, precision = 124:17  
criterion = gini  
max depth = 3  
max_features = sqrt  
max_leaf_nodes = 5  
min_samples_leaf = 1  
min_samples_split = 2  
n_estimators = 10  

## Sero- Geno-type: (train_data shape [yes:no] = 478:224)

(w/o class_weight)--accuracy = 0.744, precision = 132:9  
criterion = gini  
max depth = 3  
max_features = sqrt  
max_leaf_nodes = 5  
min_samples_leaf = 2  
min_samples_split = 2  
n_estimators = 10  

(w/ class_weight)--accuracy = 0.787, precision = 124:17  
criterion = gini  
max depth = 3  
max_features = sqrt  
max_leaf_nodes = 5  
min_samples_leaf = 1  
min_samples_split = 5  
n_estimators = 10  

## Month: (train_data actual [yes:no] = 478:224)

(w/o class_weight)--accuracy = 0.695, precision = 135:6  
criterion = gini  
max depth = 1  
max_features = sqrt  
max_leaf_nodes = 3  
min_samples_leaf = 1  
min_samples_split = 2  
n_estimators = 1  

(w/ class_weight)--accuracy = 0.581, precision = 86:55  
criterion = gini  
max depth = 2  
max_features = sqrt  
max_leaf_nodes = 4  
min_samples_leaf = 1  
min_samples_split = 2  
n_estimators = 5  

## Location: (train_data actual [yes:no] = 478:224)

(w/o class_weight)--accuracy = 0.709, precision = 141:0  
criterion = gini  
max depth = 3  
max_features = sqrt  
max_leaf_nodes = 5  
min_samples_leaf = 1  
min_samples_split = 2  
n_estimators = 10  

(w/ class_weight)--accuracy = 0.411, precision = 118:23  
criterion = gini  
max depth = 1  
max_features = sqrt  
max_leaf_nodes = 2  
min_samples_leaf = 5  
min_samples_split = 2  
n_estimators = 10  

## State: (train_data actual [yes:no] = 478:224)

(w/o class_weight)--accuracy = 0.723, precision = 137:4  
criterion = gini  
max depth = 3  
max_features = sqrt  
max_leaf_nodes = 5  
min_samples_leaf = 1  
min_samples_split = 3  
n_estimators = 5  

(w/ class_weight)--accuracy = 0.723, precision = 137:4  
criterion = gini  
max depth = 1  
max_features = sqrt  
max_leaf_nodes = 2  
min_samples_leaf = 1  
min_samples_split = 2  
n_estimators = 50  

---

# SVM SVC

## Ingredients: (train data shape [yes:no] = 478:224)
accuracy = 0.702, precision = 130:11  
C = 1.0  
cache_size = 0.2  
coef0 = 1  
decision_function_shape = ovr  
gamma = 0.1  
kernel = poly  


## Species: (train data actual [yes:no] = 478:224)
accuracy = 0.730, precision = 132:9  
C = 1.0  
cache_size = 0.2  
coef0 = 1  
decision_function_shape = ovr  
gamma = 0.1  
kernel = poly  

## Sero- Geno-type: (train data actual [yes:no] = 478:224)
accuracy = 0.766, precision = 121:20  
C = 1.0  
cache_size = 0.2  
coef0 = 1  
decision_function_shape = ovr  
gamma = 0.7  
kernel = poly  

## Month: (train data actual [yes:no] = 478:224)
accuracy = 0.688, precision = 130:11  
C = 1.0  
cache_size = 0.2  
coef0 = 1  
decision_function_shape = ovr  
gamma = 0.1  
kernel = poly  

## Location: (train data actual [yes:no] = 478:224)
accuracy = 0.702, precision = 140:1  
C = 1.0  
cache_size = 0.2  
coef0 = 1  
decision_function_shape = ovr  
gamma = 0.7  
kernel = poly  

## State: (train data actual [yes:no] = 478:224)
accuracy = 0.709, precision = 127:14  
C = 1.0  
cache_size = 0.2  
coef0 = 1  
decision_function_shape = ovr  
gamma = 0.1  
kernel = poly  
