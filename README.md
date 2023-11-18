# Mini-Project

# Description :

Leveraging data analysis with Python to study the Gross Domestic Product (GDP) of world countries involves delving into datasets that capture economic indicators. Python, being a versatile programming language, offers powerful tools and libraries for processing, analyzing, and visualizing economic data. Analysts can explore trends, disparities, and correlations within global GDP data. Through statistical analyses and machine learning techniques, Python enables the extraction of valuable insights, aiding policymakers and economists in making informed decisions. The language's data visualization capabilities also facilitate the creation of compelling charts and graphs to represent complex economic patterns and comparisons among countries. Overall, Python serves as a robust tool for economists and data scientists seeking to gain a comprehensive understanding of the economic landscape through the lens of GDP for various nations.

# KEY FEATURES :

Analyzing temporal trends to understand how GDP evolves over time for various countries.
Exploring regional variations in GDP and sectoral contributions for comprehensive economic insights.
Investigating correlations with population growth, trade balances, and policy changes using Python for data-driven analysis.

# CODE :

DEVELOPED BY : VINEESHA S

REGISTER NO : 212221040180

```
import numpy as np #linear algebra
import pandas as pd #data processing, CSV file I/O (e.g. pd.read_csv)
import seaborn as sns
from matplotlib import pyplot as plt

#data are available in the "../input/" directory

import os
print(os.listdir("../input/")) #for example, running this (click Shift+Enter) will list the files in the input directory

from sklearn.preprocessing import LabelEncoder
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.tree import DecisionTreeRegressor
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_squared_error, mean_squared_log_error
data = pd.read_csv('../input/countries of the world.csv', decimal=',')
print('number of missing data:')
print(data.isnull().sum())
data.describe(include='all')
```
```
plt.figure(figsize=(16,12))
sns.heatmap(data=data.iloc[:,2:].corr(),annot=True,fmt='.2f',cmap='coolwarm')
plt.show()
<img width="507" alt="image" src="https://github.com/Vineesha29031970/Mini-Project/assets/133136880/37357c19-847e-4102-afea-c9678945ab87">
fig, ax = plt.subplots(figsize=(16,6))
top_gdp_countries = data.sort_values('GDP ($ per capita)',ascending=False).head(20)
mean = pd.DataFrame({'Country':['World mean'], 'GDP ($ per capita)':[data['GDP ($ per capita)'].mean()]})
gdps = pd.concat([top_gdp_countries[['Country','GDP ($ per capita)']],mean],ignore_index=True)
sns.barplot(x='Country', y='GDP ($ per capita)', data=gdps, palette='Set1')
ax.set_xlabel(ax.get_xlabel(), labelpad=15)
ax.set_ylabel(ax.get_ylabel(), labelpad=30)
ax.xaxis.label.set_fontsize(16)
ax.yaxis.label.set_fontsize(16)
plt.xticks(rotation=90)
plt.show()
```


```
fig, axes = plt.subplots(nrows=3, ncols=3, figsize=(20,20))
plt.subplots_adjust(hspace=0.4)

corr_to_gdp = pd.Series()
for col in data.columns.values[2:]:
    if ((col!='GDP ($ per capita)')&(col!='Climate')):
        corr_to_gdp[col] = data['GDP ($ per capita)'].corr(data[col])
abs_corr_to_gdp = corr_to_gdp.abs().sort_values(ascending=False)
corr_to_gdp = corr_to_gdp.loc[abs_corr_to_gdp.index]

for i in range(3):
    for j in range(3):
        sns.regplot(x=corr_to_gdp.index.values[i*3+j], y='GDP ($ per capita)', data=data,
                   ax=axes[i,j], fit_reg=False, marker='.')
        title = 'correlation='+str(corr_to_gdp[i*3+j])
        axes[i,j].set_title(title)
axes[1,2].set_xlim(0,102)
plt.show()
```

<img width="632" alt="image" src="https://github.com/Vineesha29031970/Mini-Project/assets/133136880/e8c7668c-b09c-47b0-bc02-51a05d2e4677">


<img width="637" alt="image" src="https://github.com/Vineesha29031970/Mini-Project/assets/133136880/fcb71575-0ceb-46af-8261-7a4d3ed4a9d6">


<img width="630" alt="image" src="https://github.com/Vineesha29031970/Mini-Project/assets/133136880/acc0f3b7-493c-4a4a-8231-7a073388e7f8">


```
LE = LabelEncoder()
data['Regional_label'] = LE.fit_transform(data['Region'])
data['Climate_label'] = LE.fit_transform(data['Climate'])
data.head(10)
```


<img width="611" alt="image" src="https://github.com/Vineesha29031970/Mini-Project/assets/133136880/33f0479e-7077-4fc9-af5d-081574a13a73">


<img width="303" alt="image" src="https://github.com/Vineesha29031970/Mini-Project/assets/133136880/811b76d1-0004-441e-aa2d-6ca8a31bea31">

# OUTPUT :

<img width="240" alt="image" src="https://github.com/Vineesha29031970/Mini-Project/assets/133136880/ecd54477-9d1b-4863-bcea-6b0157e26393">


<img width="645" alt="image" src="https://github.com/Vineesha29031970/Mini-Project/assets/133136880/045f84d5-9cd7-47f8-9970-41093f4ae03f">


<img width="544" alt="image" src="https://github.com/Vineesha29031970/Mini-Project/assets/133136880/5a2c71f8-6390-4466-bc09-aa334552836e">


<img width="572" alt="image" src="https://github.com/Vineesha29031970/Mini-Project/assets/133136880/31fc7ed8-7933-404f-8c37-d7e94bd847da">



