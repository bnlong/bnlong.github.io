---
title: Jekyll Admin
layout: post
date: '2020-02-27 21:30:00 +0700'
categories: jekyll
---

Wow ! I have setup Ruby and Jekyll Admin successfully on my MacBook Pro ! This is the first post created by Jekyll Admin.

Here are commands I ran : 
1. Install Ruby by the : [GoRails](http://gorails.com/setup/osx/10.14-mojave) document:
{% highlight shell %}
brew install rbenv ruby-build rbenv-default-gems rbenv-gemset
echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
source ~/.bash_profile
rbenv install 2.7.0
rbenv global 2.7.0
{% endhighlight %}
{:start="2"}
2. Install Jekyll Admin using its [guide](https://github.com/jekyll/jekyll-admin): 
*     Add the following to your site’s Gemfile:
{% highlight ruby %}
     gem 'jekyll-admin', group: :jekyll_plugins
{% endhighlight %}
*     Run:  `bundle install`
