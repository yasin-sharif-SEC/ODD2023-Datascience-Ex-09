# Ex 9 Data Visualization 2

# Aim
To Perform data visualization on a complex dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# Algorithm
### Step 1
Read the given data.
### Step 2
Clean the data set using data cleaning process.
### Step 3
Apply feature generation and selection techniques to all the features of the data set.
### Step 4
Apply data visualization techniques to identify the patterns of the data.

# Code
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sb
import numpy as np
from scipy import stats

db=pd.read_csv('tips.csv')
cols=['size','tip','total_bill']
q1=db[cols].quantile(0.25)
q3=db[cols].quantile(0.75)
iqr=q3-q1
db=db[~((db[cols]<(q1-1.5*iqr))|(db[cols]>(q3+1.5*iqr))).any(axis=1)]

# 1.which day of the week has the highest total bill amount?
plt.title('Highest total bill amount by day of the week')
sb.barplot(x=db['day'],y=db['total_bill'],hue=db['day'])
plt.legend(loc='center')

# 2.what is the average tip amount given by smokers and non-smokers?
plt.title('Average tip amount given by smokers and non-smokers')
sb.boxplot(x=db['smoker'],y=db['tip'],hue=db['smoker'])

# 3.how does the tip percentage vary based on the size of the dining party?
db['tip_percent']=db['tip']/db['total_bill']
plt.title('Tip percentage by dining party size')
sb.scatterplot(x='size',y='tip_percent',data=db)

# 4.which gender tends to leave higher tips?
plt.title('Tips based on gender')
sb.boxplot(x=db['sex'],y=db['tip'],hue=db['sex'])

# 5.is there any relationship between the total bill amount and the day of the week?
plt.title('Relationship between total bill amount and day of the week')
sb.scatterplot(x='day',y='total_bill',hue='day',data=db)

# 6.how much does the distribution of total bill amounts vary across different time periods(lunch vs. dinner)?
plt.title('Distibution of total bill amount by time of day')
sb.histplot(x='total_bill',hue='time',element='step',stat='density',data=db)

# 7.which dining paty size group tends to have the highest avearge total bill amount?
plt.title('Avearage total bill amount by dining party size')
sb.barplot(x='size',y='total_bill',hue='size',data=db)

# 8.what is the distribution of tip amount for each day of the week?
plt.title('Tip amount by the day of the week')
sb.boxplot(x='day',y='tip',data=db)

# 9.how does the amount vary based on the types of service (lunch vs. dinner)?
plt.title('Tip amount by time of the day')
sb.violinplot(x='time',y='tip',data=db)

# 10.is there any correlation between the total bill amount and the tip amount?
plt.title('Correlation between total bill amount and tip amount')
sb.scatterplot(x='total_bill',y='tip',data=db)
```
# Output
### 1.which day of the week has the highest total bill amount?
![download](https://github.com/yasin-sharif-SEC/ODD2023-Datascience-Ex-09/assets/142985837/4fe73cb1-e7d3-4dac-a667-c0c54d917bbf)

### 2.what is the average tip amount given by smokers and non-smokers?
![download](https://github.com/yasin-sharif-SEC/ODD2023-Datascience-Ex-09/assets/142985837/e99f5c7e-5f75-49b3-8d0a-f04edb38640f)

### 3.how does the tip percentage vary based on the size of the dining party?
![download](https://github.com/yasin-sharif-SEC/ODD2023-Datascience-Ex-09/assets/142985837/ecd19583-e6d5-4759-a26f-ce46d0c262c8)

### 4.which gender tends to leave higher tips?
![download](https://github.com/yasin-sharif-SEC/ODD2023-Datascience-Ex-09/assets/142985837/c39a2f9c-260e-494e-b6d3-963adf556188)

### 5.is there any relationship between the total bill amount and the day of the week?
![download](https://github.com/yasin-sharif-SEC/ODD2023-Datascience-Ex-09/assets/142985837/ce662c54-bb17-4db0-812f-4efdfef7ef95)

### 6.how much does the distribution of total bill amounts vary across different time periods(lunch vs. dinner)?
![download](https://github.com/yasin-sharif-SEC/ODD2023-Datascience-Ex-09/assets/142985837/e1af1847-2651-4b10-a481-4bbe692b73fd)

### 7.which dining paty size group tends to have the highest avearge total bill amount?
![download](https://github.com/yasin-sharif-SEC/ODD2023-Datascience-Ex-09/assets/142985837/2ff07d54-5531-47b7-8ad9-004fed1a301c)

### 8.what is the distribution of tip amount for each day of the week?
![download](https://github.com/yasin-sharif-SEC/ODD2023-Datascience-Ex-09/assets/142985837/ced45254-d463-4c20-8a4d-ea004c68dfe3)

### 9.how does the amount vary based on the types of service (lunch vs. dinner)?
![download](https://github.com/yasin-sharif-SEC/ODD2023-Datascience-Ex-09/assets/142985837/ebaa6536-c0d7-4e67-96e1-7103f13846e1)

### 10.is there any correlation between the total bill amount and the tip amount?
![download](https://github.com/yasin-sharif-SEC/ODD2023-Datascience-Ex-09/assets/142985837/76a8cf7f-7344-4c9a-ba6e-8e4a61ba02df)

# Result
Thus, the given dataset is analyzed to get various insights using data visualization techniques.
