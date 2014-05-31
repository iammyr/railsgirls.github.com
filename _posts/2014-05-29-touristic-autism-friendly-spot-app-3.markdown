---
layout: default
title: Touristic Autism-friendly Spots App 
permalink: touristic-autism-friendly-spot-app-3
---

# Resource Modeling

*Created by Myriam Leggieri, [@iammyr](https://twitter.com/iammyr)*
*for [Rails Girls Galway](https://github.com/RailsGirlsGalway)*
The basic guides that have been merged and adapted are the [Ruby on Rails Tutorial](http://www.railstutorial.org/book), the [basic RailsGirls app](http://guides.railsgirls.com/app/) and the tutorials for [creating thumbnails](http://guides.railsgirls.com/thumbnails), [authenticating users](http://guides.railsgirls.com/devise/), [adding design](http://guides.railsgirls.com/design), [deploying to OpenShift](http://guides.railsgirls.com/openshift/) and [adding comments](http://guides.railsgirls.com/commenting).

What do we want our app to do? As a first thing, we would like to 
* create representations of touristic places and 
* allow registered tourists to
* review those places marking them as autism-friendly or not.


## Touristic Places

We now use Rails' scaffold functionality to generate and set up all that is necessary to list, add, remove, edit, and view our first resource: "touristic places".

<div class="os-specific">
  <div class="nix">
{% highlight sh %}
rails generate scaffold place name:string address:string latitude:decimal longitude:decimal description:text picture:string
{% endhighlight %}
</div>
</div>

The scaffold creates new files in your project directory. However, we have defined (modeled) a "structure" for our "place" resource and we want all the future instances of this resource to stick to this structure and get stored somewhere, i.e., in a database. 
We are already using a database (see `gem 'sqlite'` in your Gemfile). Let's add the structure of "place" as a table to our database with the following.

<div class="os-specific">
  <div class="nix">
{% highlight sh %}
bin/rake db:migrate
{% endhighlight %}
  </div>

  <div class="win">
{% highlight sh %}
ruby bin/rake db:migrate
{% endhighlight %}
  </div>
Then start the server again. Open [http://localhost:3000/places](http://localhost:3000/places) in your browser and check out all the new functionalities that our web application is now providing to handle "place" resources. All thanks to what Ruby on Rails automatically generates with `generate scaffold`.
Each new instance of "place" that will be stored in the database, will be automatically assigned a unique identifier called "primary key", with no need for us to specify it as one of the fields (along with picture, name, etc.)
</div>

**Coach:** What is Rails scaffolding? What are migrations and why do you need them?
Note the pages that have been created to manipulate the "place" resources and their naming convention.
Look at the server logging and explain it as a report of the following interaction (in the context of the MVC pattern):
* The browser issues a request for the /places URL.
* Rails routes /places to the index action in the Places controller.
* The index action asks the Place model to retrieve all places (Place.all).
* The Place model pulls all the places from the database.
* The Place model returns the list of places to the controller.
* The controller captures the users in the @users variable, which is passed to the index view.
* The view uses embedded Ruby to render the page as HTML.
* The controller passes the HTML back to the browser

Let's add-commit-push to your GitHub repo! See how nicely all the changes are now on your GitHub profile? :)

## Authenticated Tourists/Users

## Step 0: Add devise gem

Open up your `Gemfile` and add this line

{% highlight ruby %}
gem 'devise'
{% endhighlight %}
and run
{% highlight sh %}
bundle install
{% endhighlight %}
to install the gem. **Also remember to restart the Rails server**.

## Step 1: Set up devise in your app

Run the following command in the terminal.

{% highlight sh %}
rails g devise:install
{% endhighlight %}


## Step 2: Configure Devise

Ensure you have defined default url options in your environments files. Open up `config/environments/development.rb` and add this line:
{% highlight ruby %}
   config.action_mailer.default_url_options = { :host => 'localhost:3000' }
{% endhighlight %}

before the `end` keyword.

Open up `app/views/layouts/application.html.erb` and add:

{% highlight erb %}
<% if notice %>
  <p class="alert alert-success"><%= notice %></p>
<% end %>
<% if alert %>
  <p class="alert alert-danger"><%= alert %></p>
<% end %>
{% endhighlight %}
right above
{% highlight ruby %}
   <%= yield %>
{% endhighlight %}

Open up `app/views/ideas/show.html.erb` and remove the line that says:

{% highlight erb %}
<p id="notice"><%= notice %></p>
{% endhighlight %}

Do the same for `app/views/comments/show.html.erb`. These lines are not necessary as we've put the notice in the `app/views/layouts/application.html.erb` file.

## Step 3: Setup the User model

We'll use a bundled generator script to create the User model.
{% highlight sh %}
   rails g devise user
   rake db:migrate
{% endhighlight %}

**Coach:** Explain what user model has been generated. What are the
fields?

## Step 4: Create your first user

Now that you have set everything up you can create your first user. Devise creates all the code and routes required to create accounts, log in, log out, etc.

Make sure your rails server is running, open [http://localhost:3000/users/sign_up](http://localhost:3000/users/sign_up) and create your user account.

## Step 5: Add sign-up and login links

All we need to do now is to add appropriate links or notice about the user being logged in in the top right corner of the navigation bar.

In order to do that, edit `app/views/layouts/application.html.erb` add:
{% highlight erb %}
<p class="navbar-text pull-right">
<% if user_signed_in? %>
  Logged in as <strong><%= current_user.email %></strong>.
  <%= link_to 'Edit profile', edit_user_registration_path, :class => 'navbar-link' %> |
  <%= link_to "Logout", destroy_user_session_path, method: :delete, :class => 'navbar-link'  %>
<% else %>
  <%= link_to "Sign up", new_user_registration_path, :class => 'navbar-link'  %> |
  <%= link_to "Login", new_user_session_path, :class => 'navbar-link'  %>
<% end %>
{% endhighlight %}
right after
{% highlight erb %}
<ul class="nav">
  <li class="active"><a href="/ideas">Ideas</a></li>
</ul>
{% endhighlight %}

Finally, force the user to redirect to the login page if the user was not logged in. Open up `app/controllers/application_controller.rb` and add:

{% highlight ruby %}
  before_action :authenticate_user!
{% endhighlight %}

after `protect_from_forgery with: :exception`.

Open your browser and try logging in and out from.

**Coach:** Talk about the `user_signed_in?` and `current_user` helpers. Why are they useful?



## Place's Review

In the same way as for the "place" resource, we can create a "place's review" resource.

<div class="os-specific">
  <div class="nix">
{% highlight sh %}
rails generate scaffold review comment:text autism_friendly:integer
bin/rake db:migrate
{% endhighlight %}
  </div>
Start the server, check out the new service in your browser, add-commit-push to github.
</div>

## Relationship between our Resources

One tourists can publish several reviews. One place can receive several reviews. One review has only one tourist as the author. 
Let's represent these relationship in our app.
