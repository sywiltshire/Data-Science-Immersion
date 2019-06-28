KNeighborsClassifier works for classification and regression problem prediction

#step. 1 #classify the modeling you want to use & import the class you want to use

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

Model Evaulation

from sklearn import metrics

print (metrics.accuracy_score(y, y_pred))  y_pred is the outcome of knn.predict(test_dataframe)

Model Selection aka train_test_split

from sklearn.model_selection import train_test_split

#STEP 1: split X and y into training and testing sets (using random_state for reproducibility)

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.4, random_state=4)

STEP 2: train the model on the training set (using K=1)

knn = KNeighborsClassifier(n_neighbors=1)

STEP 3: test the model on the testing set, and check the accuracy

y_pred = knn.predict(X_test)

print(knn.predict_proba(X_test))

print (metrics.accuracy_score(y_test, y_pred))

Testing accuracy is a high-variance estimate of out-of-sample accuracy

K-fold cross-validation overcomes this limitation and provides more reliable estimates

But, train/test split is still useful because of its flexibility and speed










