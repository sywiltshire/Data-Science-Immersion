
### scatter plot in Seaborn
sns.pairplot(ads, x_vars=['TV','Radio','Newspaper'], y_vars='Sales', size=6, aspect=0.7)

### scatter plot in Seaborn with regression line
sns.pairplot(ads, x_vars=['TV','Radio','Newspaper'], y_vars='Sales', size=6, aspect=0.7, kind='reg')

### scatter matrix in Seaborn
sns.pairplot(ads)

sns.distplot(ads.Newspaper)

sns.distplot(ads.TV)

sns.distplot(ads.Radio)

