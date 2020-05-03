---
layout: post
title:  "My first day with Jekyll!"
date:   2020-02-23 13:16:10 +0700
categories: jekyll update
---
1. Installed Ruby and Jekyll on my old HP Probook 4540s laptop which runs Ubuntu 18.04
2. Followed Jekyll document and created my blog. 
3. Edit my first port under `_posts` directory. 
4. Setup Heroku CLI and deploy the Jekyll blog to Heroku
5. Here are all commands I ran:

{% highlight shell %}
    heroku create
    heroku buildpacks:add heroku/ruby
    heroku buildpacks:add https://github.com/heroku/heroku-buildpack-static
    vim ./static.json
    git add static.json
    git commit -m "Add static.json"
    vim ./Rakefile
    vim Gemfile
    bundle
    git add Rakefile Gemfile Gemfile.lock
    git commit -m "Add Rake task to build Jekyll site"
    git push heroku master
    heroku apps:rename blooming-blog
    heroku domains:add blog.phuonglong.com

{% endhighlight %}

