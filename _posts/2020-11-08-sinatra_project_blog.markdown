---
layout: post
title:      "Sinatra Project Blog"
date:       2020-11-09 03:53:41 +0000
permalink:  sinatra_project_blog
---

For my Flatiron Sinatra Project I built a real estate app that enables users to view property listing for sale and post their own listing to sell properties. This is a CRUD, MVC Sinatra app.

To start off my project I used “corneal” gem. This gem did set up the skeleton of the application, including gems, environment, dependences and routes. Installing gem was easy with corneal new #name_of_the_app.  I first decided what the models will be and the relations. Then created the migrations and run the migrations. Then simultaneously start building the controllers and views for each model. For the front end I used Bootstrap. 

I used Bcrypt gem and password_digest in DB to ensure user has_secure_password. Thanks to ActiveRecord I used validations provided by ActiveRecord, such as validations for presence of username and password, also uniqueness of username. Properties are validated for street address presence, validation that property price is validated numerically to be greater than 0. For the login enabled sessions and set session_secret.

Controllers are inheriting from the application controller. I also made sure controllers are mounted in config.ru. Controllers are handling the logic of the app and building the controllers I found to be the most challenging part of the project.

In conclusion, building this project was a great learning experience and seeing the finished project felt rewarding. 

