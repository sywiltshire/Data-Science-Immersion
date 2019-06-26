### grouping_fictional_army_answers

*Group the entire dataframe by regiment and company*
- reg.groupby(['regiment','company']).mean()

*What is the number of observations in each regiment and company*
- reg.groupby(['regiment','company'])[['preTestScore']].count()

*Iterate over a group and print the name and the whole data from the regiment*
-for name, grp in reg.groupby('regiment'):
    print(name)
    print(grp)


import pandas as pd

import numpy as np

%matplotlib pyplot as plt
