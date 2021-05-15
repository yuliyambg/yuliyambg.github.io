---
layout: post
title:      "React / Redux Project"
date:       2021-05-15 17:42:27 +0000
permalink:  react_redux_project
---


My final project during this course is a React / Redux application with a Rails API backend. 

**The Backend:**

Setting up the API was straightforward, as I had done this for my last project. This app uses a Rails API back-end with PostgreSQL for the database as I am planning to host my app on Heroku later on. 

**Models and relations:**

I have two models, respectively two tables for my backend.

1.	Art model- has a title, artist_name, and image_url. 
Art `has_many :comments`
2.	Comment model- has content, name, art_id. 
Comment `belongs_to :art`

For my API, I am getting the ‘arts’ data for the front-end from ArtsController `index` action. I also have `create` action in order to create art using fetch POST. I am getting the comments data from CommentsController `index` action, also added `create` action in order to create comments using fetch POST. 

**Validations:**

* Art model validates presence of title, artist name and image url.
* Comment model validates presence of content and name.

**Controllers:**
* ArtsController - Actions include `index` -renders arts data from the database, `show`- renders data for a single art, `create`- allows new art to be created and saved to the database.
* CommentsController - Actions include `index` -renders comments data from the database for given art and `create`- allows new comments to be created and saved to the database.

**React / Redux:**

For this simplicity of the organization for project the Frontend and Backend are under one monorepo hosted on GitHub. 
I used the `npx create-react-app` command to set up the Frontend.

**The components:**

The app has five class components and five functional components. I used class components when my component needed local state or used one of the lifecycle methods such as `componentDidMount`. 

**Redux:**

My redux store ended up with the following actions:

* *fetchArts*: data about all arts is fetched from the API when ArtsContainer mounts 
*  *addArt*: art is created and persisted to the database
* *fetchArt*: data about single art is fetched from the API before Art Component will mount. 
* *fetchComments*: data about all comments for given art is fetched from the API when ArtContainer mounts 
* *addComment*: comment is created and persisted to the database

I created separate reducers for each of these pieces of state and used the `combineReducers` function to combine them and pass them to `createStore`.

I am using the Thunk middleware when creating the store in order to have my action creators dispatch asynchronous fetch requests to the database. These dispatched functions returned actions to update my redux store when fetch is successful. 

**React Router:**

The app currently has 3 routes. 
* Route  `/`  renders the home page.
* Route  `/arts` renders page with all arts. 
* Route  `/arts/:id` renders page showing single art with section to add comments and also showing comments underneath.
