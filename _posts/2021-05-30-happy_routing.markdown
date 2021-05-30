---
layout: post
title:      "Happy Routing!"
date:       2021-05-30 16:53:50 +0000
permalink:  happy_routing
---


My 10 months journey with Flatiron school is about to end. My final project is using React-Redux Front end. In some components of my project, I was using links with anchor elements, clicking on them caused the whole page to reload, which was sending new `GET` fetch request to the API each time the link was clicked, which in turn resulted to URL’s showing incorrectly on the browser. This is how I thought about blogging about the React-Router and Link to concept.

As React Router's documentation states: React Router is a routing library for React that allows us to link to specific URLs then show or hide various components depending on which URL is displayed. 

Let’s walk through a simple App example using React Router and Clickable Links.


•	Create the app:

`npx create-react-app myapp`


•	Install React Router Library:

`npm install react-router-dom –save`


// index.js

•	Import `BrowserRouter` (commonly renamed as Router) from react-router-dom

`import { BrowserRouter as Router } from 'react-router-dom`

•	Setting up our App to work with React Router. Rendering React Router.

In React, a component can return one child/html node, it makes sense to create `<App />` component that renders the rest of the application.  We can wrap our top-level component `<App />` with the `<Router>` element.

//index.js
```
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';
import { BrowserRouter as Router} from "react-router-dom";


ReactDOM.render(
    <Router>
        <App />
    </Router>,
  document.getElementById('root')
);
```


•	The next step is to add Switch element  

`<Switch>` element can be used to group `<Route />`s. The `<Switch>` will iterate over its children elements (the routes) and only render the first one that matches the current pathname. 

//App.js

`import { Switch, Route}  from 'react-router-dom'`
```
import React from 'react'
import {Switch, Route} from 'react-router-dom';
import Home from "./Home";
import About from "./About";
import Users from "./Users";

function App() {
  return (
          <div>
              <Switch>
                  <Route path="/about" component={About} />
                  <Route path="/users" component={Users} />
                  <Route path="/" component={Home} />
              </Switch>
      </div>
  );
}
export default App;

```

A `<Route />` component expects a path prop and a component prop.
Which is like saying : Hey! when the URL matches this specific path, render this specific component.

•	Add Link element

So far, the only way to navigate to our web site is to type each specific URL in the browser. Instead, we can use clickable Links to navigate our site. If we were to create links using anchor elements, clicking on them would cause the whole page to reload. React Router provides a `<Link>` component to prevent the whole page to reload. Link gets a prop with the location where to navigate to.

`import { Link}  from 'react-router-dom'`

```
import React from 'react'
import {Link, Switch, Route} from 'react-router-dom';
import Home from "./Home";
import About from "./About";
import Users from "./Users";

function App() {
  return (
          <div>
              <nav>
                  <ul>
                      <li>
                          <Link to="/">Home</Link>
                      </li>
                      <li>
                          <Link to="/about">About</Link>
                      </li>
                      <li>
                          <Link to="/users">Users</Link>
                      </li>
                  </ul>
              </nav>

              <Switch>
                  <Route path="/about" component={About} />
                  <Route path="/users" component={Users} />
                  <Route path="/" component={Home} />
              </Switch>
      </div>
  );
}
export default App;

```

Here is how our App looks with clickable links:


<img src="https://drive.google.com/uc?id=1vc_qHjZQm1Wc09nXfv6GZ2_WMJf1PQcn">


Happy Routing!
