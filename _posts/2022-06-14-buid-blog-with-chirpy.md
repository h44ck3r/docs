---
title: Build a blog with Jekyll and Chirpy.
date: 2022-06-14 20:00
categories: [homelab, web site]
tags: [chirpy, jekyll, blog, softwere]     # TAG names should always be lowercase
author: hari
img_path: /assets/img/post/blog
---

## Introduction
---
In this first post I will explain how I did to easily create and publish a blog.

I will use this as a documentation blog, but of course you can use the same technique for any kind of blog.

First we will use [jerkyll](https://jekyllrb.com/) which is an opensource static site generator.  
It allows us to write the posts in markdown and it takes care of converting them into HTML and CSS.

Starting a whole project with jekyll can be a bit challenging for beginners (like me), so you can download themes for jekyll.  
In my case I use the [chirpy](https://github.com/cotes2020/jekyll-theme-chirpy) theme (simple and efficient) but there are themes for every taste, you have some examples [here](https://jekyllrb.com/docs/themes/) but if you don't like anything you can always create your own theme from scratch.

that's about all you need to know to get started.  
let's get started
      


## prerequisites
--- 
In my case my OS is Ubuntu, so this documentation should work for any Debian based OS but if you use another OS you should refer to the specific documentation of your OS

we need some dependencies to get started first :
 * Ruby version 2.5.0 ou Higher

### Ruby
Since jekyll is written with ruby we need to install Ruby.
```bash
sudo apt-get install ruby-full build-essential zlib1g-dev
```
   
Avoid installing RubyGems packages (called gems) as the root user. Instead, set up a gem installation directory for your user account. The following commands will add environment variables to your ```~/.bashrc``` file to configure the gem installation path:
```bash
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```
