*KNeighborsClassifier works for classification and regression problem prediction*

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

*Model Evaulation Metrics*

from sklearn import metrics

print (metrics.accuracy_score(y, y_pred))  y_pred is the outcome of knn.predict(test_dataframe)

*Model Selection aka train_test_split*

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

### Linear regression: machine learning model that can be used for regression problems*

from sklearn.linear_model import LinearRegression

#compute correlation matrix
ads.corr()

DISPLAY CORRELATION MATRIX IN A SEABORN USING A HEATMAP

sns.heatmap(ads.corr(), annot=True)

LET'S ESTIMATE THE MODEL COEFFICIENTS

Simple linear regression is an approach for predicting a continuous response using a single feature. It takes the following form: 

𝑦=𝛽0+𝛽1𝑥

y is the response

x is the feature

β0 is the intercept

β1 is the coefficient for x

β0 and β1 are called the model coefficients:

We must "learn" the values of these coefficients to create our model.

And once we've learned these coefficients, we can use the model to predict Sales.

#create X and y

feature_cols = ['TV']

X = ads[feature_cols]

y = ads.Sales

#step 2. instantiate and 
#step 3. fit

linreg = LinearRegression()

linreg.fit(X, y)

#step 4.  print the coefficients

print (linreg.intercept_)

print (linreg.coef_)

#step5. # calculate the R-squared value for the model

y_pred = linreg.predict(X)

metrics.r2_score(y, y_pred)

#pair the feature names with the coefficients
dict(zip(feature_cols, linreg.coef_))

#define a function that accepts X and y and computes testing RMSE

def train_test_rmse(X, y):

    X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=1)
    
    linreg = LinearRegression()
    
    linreg.fit(X_train, y_train)
    
    y_pred = linreg.predict(X_test)
    
    return np.sqrt(metrics.mean_squared_error(y_test, y_pred))


PART 8: COMPARING LINEAR REGRESSION WITH OTHER MODELS

Advantages of linear regression:

Simple to explain

Highly interpretable

Model training and prediction are fast

No tuning is required (excluding regularization)

Features don't need scaling

Can perform well with a small number of observations

Disadvantages of linear regression:

Presumes a linear relationship between the features and the response

Performance is (generally) not competitive with the best supervised learning methods due to high bias

Sensitive to irrelevant features

Can't automatically learn feature interactions

