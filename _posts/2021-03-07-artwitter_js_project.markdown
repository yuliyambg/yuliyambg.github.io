---
layout: post
title:      "Artwitter JS Project"
date:       2021-03-07 09:53:57 -0500
permalink:  artwitter_js_project
---

   I wanted to create an app where a user could post art and other users could post comments on the art. I thought it would be nice to have an app where people can meet to discuss about art, especially during the pandemic when a lot of galleries and museums are closed. 
This app uses a Rails API back-end with PostgreSQL for the database and asynchronous Javascript for the front-end. It is a single-page web app, with all requests to the API being made with asynchronous fetch requests.

**The Backend:**

For setting up the back-end of the app I used the `rails new` command with the --api. I added `database=postgresql` and `-T` for no testing. I also added the gem `rack-cors` for cross-origin resource sharing, under `config/initializers/cors.rb`, I set up the middleware to allow all(‘*’) origins. 
This was my first project using PostgreSQL, there was an additional step compared to SQLite that I used for my previous projects. I had to run `rails db:create` before migrating the database.
I have two models, respectively two tables for my backend.
1.	Art model- has a title, artist_name, and image_url. 
     Art has_many :comments
2.	Comment model- has content, name, art_id. 
    Comment belongs_to :art 
		
For my API, I am getting the ‘arts’ data for my front-end from ArtsController index action. I also have create action in order to create art using fetch POST. I am getting the comments data from CommentsController index action, also added create action in order to create comments using fetch POST. 

**The Frontend:**

I first created index.html page, index.js page, and a styles folder with a CSS file. I also set up src directory with two separate js files corresponding to my rails models: art.js and comment.js, that represent my JS classes.
Although I have created separate art and comment classes, most of the functionality of the app lays in index.js.

•	Art class - This class gets instantiated from the index.js file and creates a new instance of the Art class. Has renderArt() method, which function is to render arts from the API data and use that data to create HTML art cards to render.

•	Comment class - The main function of this class is to create comment objects from the API data, and use that data to create HTML to render as unordered list items.

•	Index.js - most of the functionality of the app lays in index.js, such as fetch requests, rendering form/rendering html, getting information from the form, event listeners. makes get and post fetch requests to the API and parses it to JSON for the other classes to use.

**Challenges:**

•	The first challenge was due to me using scaffolding when created the resources. I later realized that scaffolding didn’t set my routes correctly. The scaffolding set the routes for each resource independently, only when I start working on the front end, I realized had to correct the route declaration to make :arts parent of :comments (nested resources). For future projects I am planning to avoid using scaffolding and use `generate resource` instead.

•	The most challenging part was to organize my Javascript code. The more I progressed with coding the project, the more difficult it become to figure what functionality belongs to the classes and what functionality shall remain under the index.js. For future JS projects I will try to plan the structure more thoroughly.

**Conclusion:**
This was a challenging project that helped me to connect my rails knowledge (backend) with  Javascript, HTML, CSS (frontend).

