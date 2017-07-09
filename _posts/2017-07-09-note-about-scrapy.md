---
layout: post
title: "Scrapy installation and use method"
date: 2017-07-09 16:25:06 -0700
comments: true
---

1: install scrapy on Mac
	sudo pip install scrapy 
	scrapy --version  : test wherther install successfully

2: The steps to constuct a scrapy project

	(1) build the project
		scrapy startproject project-name     // code will generate some files
		scrapy genspider project_name_spider https://www.google.com 
		// generated a standarlization modula scrapy file

	(2) define the Item in item.py file
		use scrapy.Field() to define the items

	(3) write the code for spider.py file

	(4) write the code in Pipeline.py file and configuration this file in setting.py
		delete the annotation before the following code in setting file
		'''
			ITEM_PIPELINES = {'projec.pipelines.ProjecItemCsvPipline':300}
		'''
	(5) excute the code
		scrapy crawl project_name_spider 


