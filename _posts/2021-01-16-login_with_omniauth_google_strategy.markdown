---
layout: post
title:      "Login with Omniauth Google Strategy"
date:       2021-01-16 22:57:53 +0000
permalink:  login_with_omniauth_google_strategy
---


One of the project requirements for Rails portfolio project was adding login from other service, such as Facebook, Github, Twitter, Google etc.
The regular login to my App is using email address and password.
I initially tried to implement authentication with Github, however noticed that the user email comes as nil/undefined. Regardless what I tried the Omniauth Info hash was returning the email address info as nil.
At that point I decided to implement authentication with Google, and although the process was straight forward, there wasn’t a clear guide online how to implement it. I hope you find below step-by-step guidance helpful and saves you time:

Add to your Gemfile the following gems:

```
gem 'omniauth'
gem 'omniauth-google-oauth2'
gem 'dotenv-rail

```

Next run bundle. 

In 'config/initializers', create a file called 'omniauth.rb' and put in the following lines:

```
Rails.application.config.middleware.use OmniAuth::Builder do
  provider :developer unless Rails.env.production?
  provider :google_oauth2, ENV['GOOGLE_OAUTH_CLIENT_ID'], ENV['GOOGLE_OAUTH_CLIENT_SECRET']
end

```

Under  'config/routes.rb' :

```

get '/auth/:provider/callback', to: 'session#create'

```

Create a link in your app that will initiate the Google OAuth process.
We need to link to ‘auth/google_oauth2’

In my App, the link is located under: view/session/new.html.erb

```
<%= link_to "Log in with Google", '/auth/google_oauth2' %>
```

Under root directory of the app, create file called .env and add the ‘Secure keys’

```
GOOGLE_OAUTH_CLIENT_ID= XXXXXXXXXXX
GOOGLE_OAUTH_CLIENT_SECRET=XXXXXXX
```

Add .env to your .gitignore file to make sure you don’t commit your secure keys to GitHub and make sure they don’t become public.



How to get your API ‘Secure keys- Client ID and Client Secret’?

Step by Step guidance:

Go to:

https://console.cloud.google.com

•	Click “Create” to set up a new Project. 
![Click!](https://doc-0k-8o-docs.googleusercontent.com/docs/securesc/7aa7j20sm6bejrd8dbp7tqlp9t6956ed/8e4oofqiahiufce1i5g4db7o253o8kvm/1610837775000/05285008826416365287/17784173641635347597Z/1nFU97Z30OG8_gmvHTQ8gBaFz13zD1ww0?nonce=3bq6hslunif50&user=17784173641635347597Z&hash=57s8v1uefj4pjreg1etitjjvep3f7jqd)!
 
