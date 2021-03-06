---

layout: post

title: My First Python Project

---


Programming is a much needed tool in every Data Analyst/Scientist toolset. You apply your programming skills in your daily data processes as administrate, clean and data analysis in order to achieve their simplification, automatization and optimization. It is a skill that I need to improve and the best way to learn is to practice. This is the main purpose of this project, to practice the competencies that I’m learning on MOOCs, books and articles. 

There are a lot of programming languages that are used on Data Analysis/Science and the most popular are [R]( https://www.r-project.org/about.html), [Python]( https://www.python.org/about/) and [SQL]( https://www.w3schools.com/sql/sql_intro.asp). For this project, I chose Python because it’s a versatile language that can be applied in many domains and I will take this fact as an advantage to improve my learning experience. 

## The project

A few weeks ago I found out [IKEA BY SIZE](http://ikeabysize.com/), which searches IKEA's web catalog and allows to search for items/furniture by Height, Width and Depth. Based on this, I will try recreating this website adding some features to the search menu and improving its performance. 

## First challenge: Retrieve the data

Data will be the fuel of this project as there is a need for it on the items/furniture characteristics: ID, Name, Description, Price, Size, Department and Availability by Store. In this step, the information will be scraped from the [IKEA’s catalog]( https://www.ikea.com/pt/pt/catalog/allproducts/department/). This will possible by using a [Scrapy]( https://scrapy.org/) and developing a Spider.

![Hi Spider](https://thumbs.gfycat.com/CommonImperturbableBullfrog-size_restricted.gif)

## Second challenge: Automate the processes and data storage

The Spider developed in the previous step will run every week and this task will be automated. For this purpose, the Spider script will be located on a [Raspberry Pi]( https://www.raspberrypi.org/) or in the Google Cloud Platform so it will be available 24/7. Also, in this step the data will be stored in the most suitable solution.

![Running Spider](https://media.giphy.com/media/8B3ClOcitdvCE/giphy.gif)

## Third challenge: Showing the data

Using the data stored in the previous step, a website will be made show the information on the searched dimensions. In it’s core it will be very similar to the [IKEA BY SIZE](http://ikeabysize.com/), although I also want to limit the number of items shown by adding extra options on the search form. 
In this step I intend to explore the [Django]( https://www.djangoproject.com/) framework.

## Conclusion

This project will help me to learn Python while exploring its versatility in different areas. In the meantime, I will learn how to scrap data, how to automate scripts, how to store data to be 24/7 available and, finally, how to show the acquired data. 

