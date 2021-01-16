---
layout: post
title:      "Login with Omniauth Google Strategy"
date:       2021-01-16 17:57:54 -0500
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
<kbd><img src="https://drive.google.com/uc?id=1nFU97Z30OG8_gmvHTQ8gBaFz13zD1ww0" ></kbd>
 
