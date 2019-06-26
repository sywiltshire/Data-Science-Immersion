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

*Import the necessary libraries*

import pandas as pd

import numpy as np

%matplotlib pyplot as plt
