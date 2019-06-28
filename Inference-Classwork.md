### grouping_fictional_army_answers


*What is the mean preTestScore from the regiment Nighthawks?*
- reg.groupby(['regiment']).mean()

*Present general statistics by company*
- reg.groupby(['company']).describe().stack()

*What is the mean each company's preTestScore?*
- reg.groupby(['company'])[['preTestScore']].mean()

*Present the mean preTestScores grouped by regiment and company*
- reg.groupby(['regiment','company'])[['preTestScore']].mean()

*Present the mean preTestScores grouped by regiment and company without heirarchical indexing*
- reg.groupby(['regiment','company'])[['preTestScore']].mean().unstack()

*Group the entire dataframe by regiment and company*
- reg.groupby(['regiment','company']).mean()

*What is the number of observations in each regiment and company*
- reg.groupby(['regiment','company'])[['preTestScore']].count()

*Iterate over a group and print the name and the whole data from the regiment*
- for name, grp in reg.groupby('regiment'):
    print(name)
    print(grp)


### 04_apply_student_alcohol_consumption_answers

*For the purpose of this exercise slice the dataframe from 'school' until the 'guardian' column*
- df.columns
- df.info()
- df.loc[:,'school':'guardian']

*Create a lambda function that captalize strings.  Suggested to put function name in CAPITAL LETTERS for readability*
- def word_up(x):
-    return x.upper()


*Capitalize both Mjob and Fjob*
- df.Mjob.apply(word_up),df.Fjob.apply(word_up)
or
- word_up = (lambda x: x.upper())
or
- df.Mjob.str.upper()
- df.Fjob.str.upper()

* Print the last elements of the data set.*
- df.tail()

- df.Mjob = df.Mjob.apply(word_up)
- df.Fjob = df.Fjob.apply(word_up)

*Create a function called majority that return a boolean value to a new column called legal_drinker*
- df.legal_drinker = df.legal_drinker.astype('bool')
- df.info()
- def majority(x):
-    if x > 17:
-       return True
-     else:
-        return False
        
- df['legal_drinker'] = df.age.apply(majority)
- df.legal_drinker


*Multiply every number of the dataset by 10. *
- applymap() Apply a function to a Dataframe elementwise
- df.applymap(lambda x: x*10)

### 05_merge_cars_answers

*Ops it seems our first dataset has some unnamed blank columns, fix cars1*
- cars1 = []
- specific_cols = ['mpg', 'cylinders', 'displacement', 'horsepower', 'weight', 'acceleration', 'model', 'origin', 'car']
- cars1 = pd.read_csv('../data/cars1.csv', usecols=specific_cols)
- cars1.head()

*Join cars1 and cars2 into a single DataFrame called cars*
- cars = []
- cars = pd.concat([cars1, cars2])
- cars

### Frequently used features
*MAPexisting values to a different set of values*
- users['is_male'] = users.gender.map({'F':0, 'M':1})

*# change the data type of a column*
- drinks['beer'] = drinks.beer.astype('float')

*# GET DUMMIES create dummy variables for 'continent' and exclude first dummy column*
- continent_dummies = pd.get_dummies(drinks.continent, prefix='cont').iloc[:, 1:]

*# CONCATENATE two DataFrames (axis=0 for rows, axis=1 for columns)*
- drinks = pd.concat([drinks, continent_dummies], axis=1)

*# display a cross-tabulation of two Series*
- pd.crosstab(drinks.country, drinks.beer_level)

- drinks.loc[drinks.beer.between(101, 200), 'beer_level'] = 'med'     # change 101-200 to 'med'
- drinks.loc[drinks.beer.between(201, 400), 'beer_level'] = 'high'    # change 201-400 to 'high'

*# convert 'beer_level' into the 'CATEGORY' data type*
- drinks['beer_level'] = pd.Categorical(drinks.beer_level, categories=['low', 'med', 'high'])

*Ops there is a column missing, called owners. Create a random number Series from 15,000 to 73,000.*
- cars.shape
- cars['owners'] = np.random.randint(15000, 73000, cars.shape[0])

*Import the necessary libraries*

import pandas as pd

import numpy as np

%matplotlib pyplot as plt
