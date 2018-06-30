# How to find Recall & Precision

In this case, recall is also the accuracy within classes. 
Classes for this data are the binary data: 1's and 0's; 1 is 'did cause hospitalization', and 0 is 'did not cause hospitalization'.

---

> Set up all variables for calculation  

`predict_values = list(rf_predict) or list(svm_predict)`  
`test_values = list(test_labels)`  
`value_range = range(0,len(test_values))`  

`correct_values = []`  

`for x in value_range:`  
`    if predict_values[x] == test_values[x]:`  
`        correct_values.append(1)`  
`    else:`  
`        correct_values.append(0)`  

`true_pos = 0`  
`false_pos = 0`  
`true_neg = 0`  
`false_neg = 0`  

`for x in value_range:`  
`    if predict_values[x] == 1.0 and correct_values[x] == 1:`  
`        true_pos += 1`  
`    elif predict_values[x] == 1.0 and correct_values[x] == 0:`  
`        false_pos += 1`  
`    elif predict_values[x] == 0.0 and correct_values[x] == 1:`  
`        true_neg += 1`  
`    else:`  
`        false_neg += 1`  

`recall_class1 = (true_pos / (true_pos + false_neg))*100`  
`recall_class0 = (true_neg / (true_neg + false_pos))*100`  
`prec_class1 = (true_pos / (true_pos + false_pos))*100`  
`prec_class0 = (true_neg / (true_neg + false_neg))*100`  

`print('True Positive: ' + str(true_pos))`  
`print('False Positive: ' + str(false_pos))`  
`print('True Negative: ' + str(true_neg))`  
`print('False Negative: ' + str(false_neg))`  
`print('Recall/Accuracy Class 1: ' + str(recall_class1))`  
`print('Recall/Accuracy Class 0: ' + str(recall_class0))`  
`print('Precision Class 1: ' + str(prec_class1))`  
`print('Precision Class 0: ' + str(prec_class0))`  
