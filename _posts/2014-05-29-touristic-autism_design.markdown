---
layout: default
title: Touristic Autism-friendly Spots App 
permalink: touristic-autism_design
---

# Design

*Created by Myriam Leggieri, [@iammyr](https://twitter.com/iammyr)*
*for [Rails Girls Galway](https://github.com/RailsGirlsGalway)*
The basic guides that have been merged and adapted are the [Ruby on Rails Tutorial](http://www.railstutorial.org/book), the [basic RailsGirls app](http://guides.railsgirls.com/app/) and the tutorials for [creating thumbnails](http://guides.railsgirls.com/thumbnails), [authenticating users](http://guides.railsgirls.com/devise/), [adding design](http://guides.railsgirls.com/design), [deploying to OpenShift](http://guides.railsgirls.com/openshift/) and [adding comments](http://guides.railsgirls.com/commenting).

**Coach:** Talk about the relationship between HTML and Rails. What part of views is HTML and what is Embedded Ruby (ERB)? What is MVC and how does this relate to it? (Models and controllers are responsible for generating the HTML views.)

The app doesn't look very nice yet. Let's do something about that. We'll use the Twitter Bootstrap project to give us nicer styling really easily.

Open `app/views/layouts/application.html.erb` in your text editor and above the line

{% highlight erb %}
<%= stylesheet_link_tag "application", media: "all", "data-turbolinks-track" => true %>
{% endhighlight %}

add

{% highlight erb %}
<link rel="stylesheet" href="//railsgirls.com/assets/bootstrap.css" />
<link rel="stylesheet" href="//railsgirls.com/assets/bootstrap-theme.css" />
{% endhighlight %}

and replace

{% highlight erb %}
<%= yield %>
{% endhighlight %}

with

{% highlight erb %}
<div class="container">
  <%= yield %>
</div>
{% endhighlight %}

Let's also add a navigation bar and footer to the layout. In the same file, under `<body>` add

{% highlight html %}
<nav class="navbar navbar-default navbar-fixed-top" role="navigation">
  <div class="container">
    <div class="navbar-header">
      <button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".navbar-collapse">
        <span class="sr-only">Toggle navigation</span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
      </button>
      <a class="navbar-brand" href="/">The Idea app</a>
    </div>
    <div class="collapse navbar-collapse">
      <ul class="nav navbar-nav">
        <li class="active"><a href="/ideas">Ideas</a></li>
      </ul>
    </div>
  </div>
</nav>
{% endhighlight %}

and before `</body>` add

{% highlight html %}
<footer>
  <div class="container">
    Rails Girls 2014
  </div>
</footer>
<script src="//railsgirls.com/assets/bootstrap.js"></script>
{% endhighlight %}

Now let's also change the styling of the ideas table. Open `app/assets/stylesheets/application.css` and at the bottom add

{% highlight css %}
body { padding-top: 100px; }
footer { margin-top: 100px; }
table, td, th { vertical-align: middle; border: none; }
th { border-bottom: 1px solid #DDD; }
{% endhighlight %}

Now make sure you saved your files and refresh the browser to see what was changed. You can also change the HTML & CSS further.

In case your Terminal shows you an error message that *sort of* implies there is something wrong with your JavaScript or CoffeeScript, install [nodejs](http://nodejs.org/download/). This issue should not appear when you've used the RailsInstaller (but when you've installed Rails via ```gem install rails```).

**Coach:** Talk a little about CSS and layouts.


1.Design your header

+ put the following code to the bottom of `app/assets/stylesheets/application.css`:

    ```
    .navbar {
        min-height: 38px;
      background-color: #f55e55;
    }
    ```

  Now refresh the page and check the changes. You can try change the
    color or font of the header. You can check the color reference
    from [http://color.uisdc.com/](http://color.uisdc.com/).

    **Coach: ** talk about the property `display`, inline and block element.

+ Then put these lines at the bottom：

    ```
    .navbar a.brand { font-size: 18px; }
    .navbar a.brand:hover {
     color: #fff;
     background-color: transparent;
     text-decoration: none;
    }
    ```

    **Coach: ** explain the 4 states of a link


2.Design your table

 + We simply use the twitter [Bootstrap](http://www.bootcss.com/) to
   polish our table。find this line from
   app/views/ideas/index.html.erb and replace:

   ```
   <table>
   ```

   with

   ```
   <table class="table">
   ```

 + Modify size of the picture using the following lines

     ```
     <%= image_tag(idea.picture_url, :width => 600) if idea.picture.present? %>
     ```

     try to change the width and see what's gonna happen


 + add the following lines to the bottom of file app/assets/stylesheets/ideas.css.scss:

  ```
  .container a:hover {
    color: #f55e55;
    text-decoration: none;
    background-color: rgba(255, 255, 255, 0);
  }
  ```


 + try add some background style with property `background-image`,
   reference to
   [http://subtlepatterns.com/](http://subtlepatterns.com/) for some patterns.


3.add style to footer

+ add the lines to bottom of  app/assets/stylesheets/application.css:

    ```
    footer {
      background-color: #ebebeb;
      padding: 30px 0;
    }
    ```

    try put more things into `footer`, then adjust it's position.

4.add style to button

  + open
    [http://localhost:3000/ideas/new](http://localhost:3000/ideas/new)
    and find the `Create Idea` button.

   add these lines to app/assets/stylesheets/ideas.css.scss

   ```
   .container input[type="submit"] {
      height: 30px;
      font-size: 13px;
      background-color: #f55e55;
      border: none;
      color: #fff;
    }
   ```

   **Coach** explain how to use `border` in css, try modify the style
     of button like round the corner, add shadow or color etc.

