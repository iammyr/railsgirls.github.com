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

* TDD using Guide
* Resource Rating
* Authenticated User (via devise) permission setting

The basic guides that have been merged and adapted are the [Ruby on Rails Tutorial](http://www.railstutorial.org/book), the [basic RailsGirls app](http://guides.railsgirls.com/app/) and the tutorials for [creating thumbnails](http://guides.railsgirls.com/thumbnails), [authenticating users](http://guides.railsgirls.com/devise/), [adding design](http://guides.railsgirls.com/design), [deploying to OpenShift](http://guides.railsgirls.com/openshift/) and [adding comments](http://guides.railsgirls.com/commenting).



### [*0.*Installation](/install)

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


### [*1.*Basic Web Application](/_posts/2014-05-29-touristic-autism_basic-app.markdown)

### [*2.*Version control with Git](/_posts/2014-05-29-touristic-autism_git.markdown)

### [*3.*Resource Modeling](/_posts/2014-05-29-touristic-autism_resource-modeling.markdown)

### [*4.*Continuous Deployment](/_posts/2014-05-29-touristic-autism_continuous-deployment.markdown)

### [*5.*Resource Rating](/_posts/2014-05-29-touristic-autism_resource-rating.markdown)

### [*6.*Design](/_posts/2014-05-29-touristic-autism_design.markdown)

### [*7.*Image upload and Thumbnails](/_posts/2014-05-29-touristic-autism_image-upload.markdown)

Optional - for advanced participants
### [*8.*Static Pages and Testing](/_posts/2014-05-29-touristic-autism_static-pages-tdd.markdown)


To-Do: add tests and deploying reminders at the end of each step.



## What next?

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


# Appendices

## Undoing things

Rails has some facilities to help you recover from mistakes. 

For instance, you may decide to change the name of a controller. Since, when generating a controller, Rails creates many more files than the controller file itself, undoing the generation means removing a whole set of files. In Rails, this can be accomplished with rails destroy. In particular, these two commands cancel each other out:

  $ rails generate controller FooBars baz quux
  $ rails destroy  controller FooBars baz quux

Similarly, after we generate a model as follows:

  $ rails generate model Foo bar:string baz:integer

This can be undone using

  $ rails destroy model Foo


Migrations change the state of the database using

  $ rake db:migrate

We can undo a single migration step using

  $ rake db:rollback

To go all the way back to the beginning, we can use

  $ rake db:migrate VERSION=0

As you might guess, substituting any other number for 0 migrates to that version number, where the version numbers come from listing the migrations sequentially.

To drop a table from the db enter

  $ rails console

Then just type:

  >> ActiveRecord::Migration.drop_table(:<table-name>)

You can browse directly the database (if sqlite3 type ".quit" to exit afterwards) by typing

  $ rails db

