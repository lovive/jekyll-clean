---
layout: post
title: "The data visualization tools using python"
date: 2017-07-19 16:27:06 -0701
comments: true
---

The commonly-used tools to visualize the data using python programming. Here list three differents tools and the gallary for each tool
	
	a. matplotlib : http://matplotlib.org/gallery.html 

	b. seaborn : http://seaborn.pydata.org/examples/index.html

	c. bokeh: http://bokeh.pydata.org/en/latest/

The gallery of these tools show a lot of examples, and use different methods to show the data

we can use the "pip install xxx" code to install these tools.

In addition, the bokeh is generally used to visulaize the data on the websites.

Notes:

For the matplotlib, there are different methods to support the Chinese Language. A most convernient methods is that add the following code in your programing code. 

```
plt.rcParams['font.sans-serif'] = ['SimHei']  # 指定默认字体
plt.rcParams['axes.unicode_minus'] = False  # 解决保存图像是负号'-'显示为方块的问题
```


