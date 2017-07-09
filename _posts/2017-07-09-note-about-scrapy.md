---
layout: post
title: "Scrapy installation and use method"
date: 2017-07-09 16:25:06 -0700
comments: true
---

1: install scrapy on Mac

	```python
	sudo pip install scrapy 
	```

	```python
	scrapy --version  #test wherther install successfully
	```

2: The steps to constuct a scrapy project

a. build the project

	scrapy startproject project-name   

	// code will generate some files

	'''
	scrapy genspider project_name_spider https://www.google.com
	'''

	// generated a standarlization modula scrapy file

b. define the Item in item.py file

	use scrapy.Field() to define the items

c. write the code for spider.py file

d. write the code in Pipeline.py file and configuration this file in setting.py

	delete the annotation before the following code in setting file

	'''
		TEM_PIPELINES = {'projec.pipelines.ProjecItemCsvPipline':300}
	'''

e. excute the code

	'''
	scrapy crawl project_name_spider 
	'''


