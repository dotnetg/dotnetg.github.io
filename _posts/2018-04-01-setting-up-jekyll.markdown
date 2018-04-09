---
layout: post
title:  "Setting up Jekyll!"
date:   2018-04-01 18:00:10 -0400
categories: blog update
---
I am starting this blog to primarily log my dotnet musings, tech thoughts, recipes to cook delicious software and other impediments observed along the way.

How this blog started?
I am trying out github pages for my blog and will use Jekyll as a static site generator. I am blogging from Windows 10 and with Kali Linux for WSL (Windows Subsystem for Linux).

Setting up github pages (https://pages.github.com/)
Created an account on github (dotnetg), then a repo for dotnetg.github.io.
Clone Repo: git clone https://github.com/dotnetg/dotnetg.github.io

Note that I was tinkering around, trying to see what works and what doesn't and why. So below steps may not server as the perfect guide.

# Installation
1. Installing via bash on Windows 10
open cmd
type bash
2. Update repo list and packages
sudo apt-get update -y && sudo apt-get upgrade -y
3. Install ruby
sudo apt-get install ruby-full
4. Update gem
sudo gem update
5. Install Jekyll
sudo gem install jekyll bundler

I got errors:
Building native extensions. This could take a while...
ERROR:  Error installing jekyll:
        ERROR: Failed to build gem native extension.

current directory: /var/lib/gems/2.5.0/gems/http_parser.rb-0.6.0/ext/ruby_http_parser
make "DESTDIR=" clean
sh: 1: make: not found

I decided to not pursue Kali at this point and switch to Debian

Go back to Windows App Store and download Debian
sudo apt-get update & upgrade. Then install git
open bash

'make' not found on Debian either

so now do:
sudo apt-get install --reinstall build-essential

### Setting up jekyll
sudo apt-get install build-essential patch ruby-dev zlib1g-dev liblzma-dev
Problem: nokogiri was not installed


Head over to http://www.nokogiri.org/tutorials/installing_nokogiri.html
run:
sudo apt-get install build-essential patch ruby-dev zlib1g-dev liblzma-dev
gem install nokogiri

done!

Create a Gemfile in dotnetg.github.io:
source "https://rubygems.org"

{% highlight ruby %}
gem "json"
gem "jekyll"
gem "jekyll-sitemap"
gem "jekyll-feed"
gem "jekyll-paginate"
gem "jekyll-gist"
gem 'github-pages', group: :jekyll_plugins
{% endhighlight %}

Then run sudo bundle install
This will get all the dependencies resolved.

run: sudo gem install jekyll bundler

Then bundle exec jekyll new dotnetg.github.io
This created a new site inside dotnetg.github.io (which I pushed to github)


