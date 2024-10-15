
# See notebok - TASK 6 is extra credit

You are reproducing publised research in "Examining the feasibility of using open data to benchmark building energy usage in cities: A data science and policy perspective" [Roth et al 2019](https://www.researchgate.net/publication/337074109_Examining_the_feasibility_of_using_open_data_to_benchmark_building_energy_usage_in_cities_A_data_science_and_policy_perspective).

The model is a Random Forest (RF) and the goal is to (get a decent model and then) perform feature importance on the model
All of this we have done together in class (https://github.com/fedhere/PUS2022_FBianco/blob/main/classdemo/titanicdemo.ipynb, I added a cell of code at the end that finds the uncertainty in the feature importance)

There are however 2 data preparation tasks that I live for you to figure out how to do by using the sklearn respective methods:

- **Inpute missing data with KNN:**

KNN is K-nearest neighbor is a machine learning method that simply finds the k nearest neighbors of an object in the feature space, based on a chosen distance metric, and makes a prediction for the target variable based on the values for that variable of those neighbors. The prediction could be the average of the neighbors target variable, the median, or, commonly, the weighted average weighted by the distance (i.e. an average where the nearer neightbors count more than the farther away ones).

To implement it its the same framework as for most (all?) sklearn models: 
1. create the model and make decisions on the hyperparameters
2. fit the model to the data
3. predict the target variable

For example, if I wanted to classify something with KNN I would use the sklearn model `KNeighborsClassifier` ([see here](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html))
I would do something like:
```
knnmodel = KNeighborsClassifier()
knnmodel.fit(X, y)
print(knnmodel.predict([[X_to_be_predicted]]))
```

If I wanted to perform a regression (predict a continuous variable) I would use `KNeighborsRegressor` ([see here](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsRegressor.html#sklearn.neighbors.KNeighborsRegressor)) as

```
knnmodel_reg = KNeighborsRegressor(n_neighbors=3, weight="distance") #where I set the hyperparameter 3 neighbors (default is 5) and decided for a weighted average weighted by the distance that causes the nearer neighbors to be more influential in the result than the farther ones (default is just the mean).
knnmodel_reg.fit(X, y)
print(knnmodel_reg.predict([[X_to_be_predicted]]))
```

For _data imputation_ you can use the model [KNNImputer](https://scikit-learn.org/stable/modules/generated/sklearn.impute.KNNImputer.html) which works similarly to what I used above. Help yourself with the sklearn webpage instructions, and ask on slack if you get stuck.

The other thing I ask you to figure out on your own is how to "One Hot Encode" the categorical variables in the dataset. 
One hot encoding is the process of turning the N categories in a categorical feature (variable) into N binary features.
See slides https://slides.com/d/QJTgsWE/live#/7 and scroll down.




<img width="921" alt="Screen Shot 2022-11-17 at 8 41 19 AM" src="https://user-images.githubusercontent.com/1696902/202461622-bd0c2172-cab2-423e-8497-0d02ba0f74c8.png">
<img width="526" alt="Screen Shot 2022-11-17 at 8 41 33 AM" src="https://user-images.githubusercontent.com/1696902/202461706-0c2c5cf7-c4a3-4f10-a393-4312f7c251df.png">


To implement this preprocessing step in python you can use `sklearn.preprocessing.OneHotEncoder` ([see here](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html))
See the example in the webpage:

```#set the model
enc = OneHotEncoder(handle_unknown='ignore') # wise to set this: it means if there is an category that is causing an error the code wont break
enc.fit(X) # this is the full feature set: it does not have to be 
enc.categories_ # tells you which ones are the variables that will be transformed to one-hot
enc.transform().toarray()
array([[1., 0., 1., 0., 0.],
       [0., 1., 0., 0., 0.]])
>>> enc.inverse_transform([[0, 1, 1, 0, 0], [0, 0, 0, 1, 0]])
array([['Male', 1],
       [None, 2]], dtype=object)
>>> enc.get_feature_names_out(['gender', 'group'])
array(['gender_Female', 'gender_Male', 'group_1', 'group_2', 'group_3'], ...)
