---
layout: post
title: "Some basic introduction to NLTK"
date: 2017-08-28 15:28:06 -603
comments: true
---

Note for some basic knowledge about the NLTK (Natural Language Toolkit)

install: pip install nltk

install Toolkit: import nltk   nltk.download()

the steps to process the txt file to analysis emotion

1）：原始文本-> 2)：分词(tokenize) -> 3):词形归一化 (stem/lemma) -> 4):去除停用词， -> 5)处理好的单词列表 

在分词的过程中，可以对其进行词性标注 (POS tag), 之后使用词性标志去帮助第三步的过程

 ```python
 import nltk

(1) tokenize
sentence = "Note for some basic knowledge about the NLTK (Natural Language Toolkit)"
tokens = nltk.word_tokenize(sentence) # need download punkt module

# 或者使用结巴分词
import jieba  # install: pip install jieba 
seg_list = jieba.cut("这是一个美好的地方",cut_all= Ture) # Ture: 全模式, Fals: 精确模式

(2) stemming: 词干提取
from nltk.stem.porter import PorterStemmer

porter_stemmer = PorterStemmer()
print(porter_stemmer.stem('looking'))

# similar method : SnowballStemmer, LancasterStemmer

(3) lemmatization：词形归并
from nltk.stem import WordNetLemmatizer  # need download wordnet 

wordnet_lematizer = WordNetLemmatizer()
print(wordnet_lematizer.lemmatize('goes')) 

# or use the property to precisely lemma
print(wordnet_lematizer.lemmatize('goes',pos='v'))

(4) part of speech: 词性标注
words = nlkt.word_tokenize('Note for some basic knowledge about the NLTK (Natural Language Toolkit)')
print(nltk.pos_tag(words))

(5) delete stop words : 去掉停用词
from nltk.corpus import stopwords # need download stopwords

filters_word = [word for word in words if word not in stopwords.words('english')]

```

Here, gaving a simple demo code to analysis the text file


 ```python

 import nltk
 from nltk.stem import WordNetLemmatizer
 from nltk.corpus import stopwords

 # original file
 raw_text = 'Note for some basic knowledge about the NLTK Natural Language Toolkit'

 # tokienize
 raw_words = nltk.word_tokenize(raw_text)

 # stem and lemma
 wordnet_lemmatizer = WordNetLemmatizer()
 words = [wordnet_lemmatizer.lemmatize(raw_word) for raw_word in raw_words]

 # delete stopword
 filtered_words = [word for word in words if word not in stopwords.words('english')]

 print(filtered_words)

```

Document classification: the method TF-IDF 

TF: Term frequency, the number of a word in a file (一个词在一个文件中出现的次数)

IDF: Inverse Document Frequency (ratio between total file number and the number of file, which has the word)

TF-IDF: TF*IDF

TF = (the number of a word in a file)/(the total number of a word in total files)

IDF = log((total number of files)/(total number of files, which has the specific word))

We can use the TextCollection.tf_idf() to process this step

Here, giving a demo code 

 ```python

 from nltk.text import TextCollection

 text1 = 'That is a good movie'
 text2 = 'This is a bad movie'
 text3 = 'I like this movie'

 # construct the TextCollection object
 tc = TextCollection([text1,text2,text3])

 # test text
 new_text = 'That one is a good movie, it is so good !'

 word = 'good'
 tf_idf_val = tc.tf_idf(word,new_text)

```

Here, introduce a commonly used to analysis the words and classfication the file algorithm: Naive bayes method

This method is simple probabilistic classifiers based on applying bayes' theorem with strong (naive) independence assumptions between the features

在判断各个属性属于某一类时，假设每个属性之间是相互独立的

This method is very efficiency and very easy to be coded

Here, set F1, F2, ..., Fn are the independent feature (strong assumptions)

so assume a file has the features F1, F2, ..., Fn, we need predict which class belong to for this file, so we need caculate the probability:

formula: p(c|F1, F2, ..., Fn)， the c represent the class, p(c) is the probability of the class c

based on the bayes theorem： p(c|F1, F2, ..., Fn) = (p(c)p(F1, F2, ..., Fn|c))/(p(F1, F2, ..., Fn))

Here we need caculate the p(F1, F2, ..., Fn|c)), based on the independet property, 

we have: p(F1, F2, ..., Fn|c)) = p(F1|c)p(F2|c)...p(Fn|c)

it is very easy to caculate the above equation. so we can caculate the probability of the sample file in each class, 

and the sample belongs to the category, which has biggest probabiblity.

For continus variable, we assume that each feature satisfied a normal distribution (gaussian), we can caculate the mean and standard deviation

then similar to the discrete condition, we can caculate the probability  






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

```python
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






