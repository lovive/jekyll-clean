---
layout: post
title: "Some basic introduction to pandas and an example to set the parameter in a figure ploted by matplotlib in python"
date: 2017-07-21 22:28:06 -602
comments: true
---

Note for some basic code to plot the histogram for different data using matplotlib.pyplot 

```python
from numpy.random import beta
import matplotlib.pyplot as plt
import pandas as pd
import math

# use 'bmh' sheet style
plt.style.use('bmh')

# setting the font and size style
font = {'family' : 'serif',  
        'color'  : 'darkred',  
        'weight' : 'normal',  
        'size'   : 20,  
        } 

# read the csv data
data = pd.read_csv('GFP_PEST_FACS_data_log.csv')

# define a function to plot hist
def plot_beta_hist(a):  
    
    # drop the NaN data
    a1 = a.dropna()
    
    # plot the histogram 
    ax.hist(a1, histtype="stepfilled",
            bins=100, alpha=0.8, normed=True)

# get the plot property
fig, ax = plt.subplots()

# obtain the different column to plot 
plot_beta_hist(data['10min'])
plot_beta_hist(data['40min'])
plot_beta_hist(data['80min'])
plot_beta_hist(data['120min'])

# set the title name and fontsize
ax.set_title("FACS: GFP-PEST protein level distribution",fontsize=16)

# set the x xlabel plot range
plt.xlim(1.8,3.6) 

# set the legend and the text location, 2 for up left, general using 'best' common
plt.legend(loc=2,fontsize=16)

# set the x and y ticks fontsize
plt.xticks(fontsize=16)
plt.yticks(fontsize=16)

# set the x and y label and fontsize
plt.xlabel('Log10(Protein Level)(a.u.)',fontdict=font)
plt.ylabel('Probability density',fontdict=font)

# show the figure
plt.show()
```
Here used the pandas to import data, show some notes about the pandas comments

```
df_obj = DataFrame() # construct the dataFrame object
df_obj.dtypes # obtain the data types
df_obj['columns'].astype(int)# change the data types form one column
df_obj.head() # show the data, default for 5 lines
df_obj.tail() # show the data begain the tail of data
df_obj.index # show the index of data
df_obj.columns # show the name of columns
df_obj.values # show the value of data
df_obj.describe() # show the data decription
df_obj.T # transform
df_obj.sort_values(by=['',''])# transform

# read data from file
read_csv('LQJ.csv',sep=';',nrows=2) 
df.to_excel('foo.xlsx',sheet_name='Sheet1');pd.read_excel('foo.xlsx', 'Sheet1', index_col=None, na_values=['NA']) # save the data to excel
df.to_hdf('foo.h5','df');pd.read_hdf('foo.h5','df') # save the data to hdf5

# clean the data 

df[df.isnull()]
df[df.notnull()]
df.dropna() # drop all the row, which contains the Nan
df.dropna(axis=1,thresh=3) # drop the nan data in columns
df.dropna(how='ALL') 
df.fillna(0)
df.fillna({1:0,2:0.5}) # set the first nan as 0, the seconde as 0.5
df.fillna(method='ffill') # set the value of before to the next nan value

```





