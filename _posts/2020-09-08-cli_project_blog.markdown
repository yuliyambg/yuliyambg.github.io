---
layout: post
title:      "CLI Project Blog"
date:       2020-09-09 01:58:48 +0000
permalink:  cli_project_blog
---


Building the CLI Project was challenging and extraordinary experience. The CLI Data Gem project helped me to connect the dots of what I have learnt the past couple of weeks. I started my preparation and process by watching the live build videos, watching them again and again. 


The most intimidating part as “Avi” says is the “Blank file” when you have no idea where to start. The outline provided in the live build video’s helped me greatly how to plan and work on the Gem. 


I started the project by thinking what would be a useful tool that user can use and what type of problem will solve and who would be the user of my Gem. Considering the impact of Covid-19, I though wouldn’t be great if I can build a Gem helping people to find clinics that are providing Covid-19 treatment, by inputting different search criteria’s. This Gem could be also used from a different type of users – larger vaccine/medication distribution companies who can easily find clinics in certain area’s by inputting search criteria’s and supply their vaccine/medicine to particular clinics/ targeted areas. I am located in NY and after research decided to scrape : https://www.health.ny.gov/regulations/hcra/provider/provcdtc.htm


For this project I used Ruby mine IDE. The first step was to make sure the web site is scrapable. I used TheGingertonic ScraperChecker tool.  The next step was to set up the Gem skeleton by using Bundle gem. With this all folders and structure were set up. The most challenging part for me throughout the entire project was to set up correctly “ny_clinics.gemspec” file and environment file with the dependencies  where I spent a lot of time to require_relative files.  After I was set with the environment and gemspec I started to code.


It was clear that I need separate class for CLI, separate class for Scraper and separate class for Clinic object. As suggested in the CLI Gem Walkthrough video I decided to make the file in my bin folder the executable file.
The scraping part was relatively smooth. I did one level scraping. The information I scraped was in a table with several lines of records. I iterated over each row to extract information regarding name of each clinic, address, state, zip code, status. With this information I instantiated my Clinic class and initialized with name, street address, city, zip_code, status. I set up the class variable to empty array and stored the instances inside of this array at time of initialization.   Under the Clinic class I set up class methods to find clinics by zip_code, find by name, find by city, find my status, list all.
I structured my CLI class based on guidance provided in the CLI Gem walkthrough video, I used methods: call, welcome, menu, check_if_empty, run.


I believe the interface is simple and easy to follow. This project helped me to connect the pieces of information/knowledge learnt for the past couple of weeks and understand how object-oriented programing works.

