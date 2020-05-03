---
title: Add a custom domain for Heroku app
layout: post
date: '2020-02-24 13:16:10 +0700'
categories: heroku
---

Finally, my custom domain for the Jekyll blog started working. Normally, it is as easy step to adding a custom domain to a Heroku app like this: 
{% highlight shell %}
heroku domains:add todos.phuonglong.com
{% endhighlight %}

Unfortunately, I followed this Heroku's [guide](https://blog.heroku.com/jekyll-on-heroku ). It asked us to "https_only": true in the static.json. It caused the issue with SSL mismatch when redirection.
 
TIP:  To clone a Heroku app, we should use this command:
{% highlight shell %}
heroku git:clone -a myapp
{% endhighlight %}
But sometimes you may accidentially clone the app by a normal git command:
{% highlight shell %}
git clone https://git.heroku.com/myapp.git
{% endhighlight %}
Then you will not able to have the app working as usually. To fix the issue, you should run:
{% highlight shell %}
heroku git:clone -a myapp
{% endhighlight %}