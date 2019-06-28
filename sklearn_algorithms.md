# step. 1 #classify the modeling you want to use & import the class you want to use

from sklearn.neighbors import KNeighborsClassifier

#step 2. Instantiate the estimator

knn = KNeighborsClassifier(n_neighbors = 1)

#step 3. Fit or train model with Data

knn.fit(X,y)

#4 predict the response and probability with new observation or observations

knn.predict(test_dataframe)

knn.predict_proba(test_dataframe)


- Advantages of KNN:
- Simple to understand and explain
- Model training is fast
- Can be used for classification and regression!
- Disadvantages of KNN:
- Must store all of the training data
- Prediction phase can be slow when n is large
- Sensitive to irrelevant features
- Sensitive to the scale of the data
- Accuracy is (generally) not competitive with the best supervised learning methods



