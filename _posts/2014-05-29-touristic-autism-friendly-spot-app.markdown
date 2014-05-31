---
layout: default
title: Touristic Autism-friendly Spots App 
permalink: touristic-autism-friendly-spot-app
---

# Rails Girls Touristic Autism-friendly Spots App Tutorial

*Created by Myriam Leggieri, [@iammyr](https://twitter.com/iammyr)*
*for [Rails Girls Galway](https://github.com/RailsGirlsGalway)*


This guide merges, adapts and extends some of the basic RailsGirls guides **for the scenario**: visualization of touristic places in Galway (Ireland) that are autism-friendly. This application was requested by the [Galway Autism Partnership](http://www.galwayautismpartnership.com/). 

The extension comprises of the following **new features**:
<ul>
<li>Version control with Git</li>
<li>Continuous Deployment on OpenShift<li>
<li>Unit Testing<li>
<li>Google Places collection<li>
<li>Google Places visualization in a Google Map<li>
<li>Google Map visualization<li>
<li>Google Map bookmarks customization.<li>
</ul>

The basic guides that have been merged and adapted are the [Ruby on Rails Tutorial](http://www.railstutorial.org/book), the [basic RailsGirls app](http://guides.railsgirls.com/app/) and the tutorials for [creating thumbnails](http://guides.railsgirls.com/thumbnails), [authenticating users](http://guides.railsgirls.com/devise/), [adding design](http://guides.railsgirls.com/design), [deploying to OpenShift](http://guides.railsgirls.com/openshift/) and [adding comments](http://guides.railsgirls.com/commenting).



### [*1.*Installation](/install)

**Make sure you have Rails and Git installed.** [**Follow the installation guide**](/install), the [**Installing Git section of Pro Git**](http://www.git-scm.com/book/en/Getting-Started-Installing-Git) to get set up. Then configure GitHub by typing the following in your terminal:
<div class="os-specific">
  <div class="nix">
{% highlight sh %}
$ git config --global user.name "Your Name"
$ git config --global user.email your.email@example.com
{% endhighlight %}

    <div>
<p>one-time setup steps for GitHub.</p>
    </div>
Sign up for a [free GitHub account](https://github.com/signup/free) if you don’t have one already. 


### [*2.*Basic Web Application](/touristic-autism-friendly-spot-app-1)

### [*3.*Version control with Git](/touristic-autism-friendly-spot-app-2)

## [*4.*Resource Modeling](/touristic-autism-friendly-spot-app-3)

## [*5.*Continuous Deployment](/touristic-autism-friendly-spot-app-4)

## [*6.*Design](/touristic-autism-friendly-spot-app-5)

## [*7.*Image upload and Thumbnails](/touristic-autism-friendly-spot-app-6)

## [*8.*Show All Places in a Google Map](/touristic-autism-friendly-spot-app-7)


To-Do: add tests and deploying reminders at the end of each step.



## *9.*Finetune the routes

If you try to open [http://localhost:3000](http://localhost:3000) it still shows the "Welcome aboard" page. Let's make it redirect to the ideas page.

Open `config/routes.rb` and after the first line add

{% highlight ruby %}
root :to => redirect('/ideas')
{% endhighlight %}

Test the change by opening the root path (that is, http://localhost:3000/) in your browser.

**Coach:** Talk about routes, and include details on the order of routes and their relation to static files.

**Rails 3 users:** You will need to delete the index.html from the `/public/` folder for this to work.

## *10.*Create static page in your app

Lets add a static page to our app that will hold information about the author of this application — you!

{% highlight sh %}
rails generate controller pages info
{% endhighlight %}

This command will create you a new folder under `app/views` called `/pages` and under that a file called `info.html.erb` which will be your info page.

It also adds a new simple route to your routes.rb.

{% highlight ruby %}
get "pages/info"
{% endhighlight %}

Now you can open the file `app/views/pages/info.html.erb` and add information about you in HTML and then take your browser to [http://localhost:3000/pages/info](http://localhost:3000/pages/info) to see your new info page.

## *11.*What next?

* Add design using HTML &amp; CSS
* Add ratings
* Use CoffeeScript (or JavaScript) to add interaction
* Add picture resizing to make loading the pictures faster


## Additional Guides

* Guide 0: [Handy cheatsheet for Ruby, Rails, console etc.](https://github.com/PragTob/rails-beginner-cheatsheet)
* Guide 1: [Add commenting by Janika Liiv](/commenting)
* Guide 2: [Put your app online with Heroku by Terence Lee](/heroku) / [Put your app online with OpenShift by Katie Miller](/openshift) / [Put your app online with Ninefold](/ninefold) / [Put your app online with Shelly Cloud](/shellycloud) / [Put your app online with anynines](/anynines) / [Put your app online with Trucker.io](/trucker)
* Guide 3: [Create thumbnail images for the uploads by Miha Filej](/thumbnails)
* Guide 4: [Add design using HTML &amp; CSS by Alex Liao](/design)
* Guide 5: [Add Authentication (user accounts) with Devise by Piotr Steininger](/devise/)
* Guide 6: [Adding profile pictures with Gravatar](/gravatar)
* Guide 7: [Test your app with RSpec](/testing-rspec)
* Guide 8: [Continuous Deployment with Travis-CI](/continuous-travis) / Continuous Deployment with Codeship](/continuous)
* Guide 9: [Go through additional explanations for the App by Lucy Bain](https://github.com/lbain/railsgirls)

