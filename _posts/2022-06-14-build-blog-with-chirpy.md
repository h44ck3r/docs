---
title: Build a blog with Jekyll and Chirpy.
date: 2022-06-14 20:00
categories: [homelab, web site]
tags: [chirpy, jekyll, blog, softwere]     # TAG names should always be lowercase
author: hari
img_path: /assets/img/post/build-blog-with-chirpy
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
      


## Dependencies
--- 
In my case my OS is Ubuntu, so this documentation should work for any Debian based OS but if you use another OS you should refer to the specific documentation of your OS

we need some dependencies to get started first :
 * Ruby version 2.5.0 ou Higher
 * jekyll bundler

### **Ruby**
Since jekyll is written with ruby we need to install Ruby.

```bash
sudo apt install ruby-full build-essential zlib1g-dev git
```

Avoid installing RubyGems packages (called gems) as the root user. Instead, set up a gem installation directory for your user account. The following commands will add environment variables to your ```~/.bashrc``` file to configure the gem installation path:

```bash
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

### **Jekyll bundler**
Bundler provides a consistent environment for Ruby projects by tracking and installing the exact gems and versions that are needed.

```bash 
gem install jekyll bundler
```


## use the Chirpy theme
---
By going to the git hub repo of chripy in the [quick start](https://github.com/cotes2020/jekyll-theme-chirpy#quick-start) session there is an option to create a new repo from the original.
We need to copy it so we have our own github repo and we can make the necessary changes and keep a copy of our code on github as a back up.

### **Copy the original repo**
![screenshot of the new repo creation on github](new-repo.png){: .normal}    
*screenshot of the new repo creation on github*

Once we have our repo, we have to clone it on our pc
```bash 
git clone https://github.com/<git username>/<git repo name>.git
```
you can find your link here :  
(my repo is called docx)

![the repo link on git](git-link.png){: .normal}    
_The repo link on git_


Now we have cloned the repo we need to install dependencies for the repo :
```bash
cd path/to/cloned/repo
bundle
```

### **Change the theme**
With jekyll especially Chirpy it is easy to make changes to the blog.
for the general configuration it is enough to go to the file ``_config.yml`` and to make the modifications

it is a good starting point to modify the following fields 

```yaml
lang: <option> 
timezone: <option>
title: <option>
tagline: <option>
description: <option>
```
{: file="/_config.yml"}


It is possible to customize evry single option but that's not really the point here.
There is plenty of documentation online to fine tune the site.


## **Posts**
As seen before the posts are written in markdown and Jekyll does the layout for us.  


### Naming Conventions
To to write an article you just have to create a file in the `_posts` folder, but the file name must respect some rules.
* It is necessary to have the date at the beginning in YYYY-MM-DD format 

> You can schedule the publication date by setting the date and time in the furure.
{: .prompt-tip }


* It is necessary to write in kebab-case 
* It must have an extension in .md

so for this position the file name is this: `2022-06-14-build-blog-with-chirpy.md`     
if you are not familiar with markdown it is [very easy](https://www.markdownguide.org/cheat-sheet/), the markdown code of this article is [here](https://raw.githubusercontent.com/h44ck3r/h44ck3r.github.io/main/_posts/2022-06-14-build-blog-with-chirpy.md).


### Header
before writing your article, be sure to read this header, otherwise the layout may be at best haphazard 
```yml
---
title: <title of the article>
date: AAA-MM-DD HH:MM
categories: [cat 1, cat 2]         #you can only have two categories
tags: [tag 1, tag 2, tag 3, tag 4]     # TAG names should always be lowercase
img_path: /path/to/image/folder
---
```
{: file="AAA-MM-DD-post-x.md"}



### Markdown Examples
If you need some help with markdown, check out the [markdown cheat sheet](https://www.markdownguide.org/cheat-sheet/)

I have lots of examples in my [documentation site repo](https://github.com/h44ck3r/docx/tree/main/_posts). Just click on the Raw button to see the code behind the page.

For more neat syntax for the Chirpy theme check their [demo page](https://chirpy.cotes.page/posts/write-a-new-post/) on making posts



## **Jekyll Commands**
---
for it is possible to have an overview of the changes you have made before putting the site into production.

```bash
cd path/to/cloned/repo
bundle exec jekyll s
```
the output should look something like this:
```bash
Configuration file: /home/hari/Documents/site/dev/docx/_config.yml
 Theme Config file: /var/lib/gems/3.0.0/gems/jekyll-theme-chirpy-5.2.0/_config.yml
            Source: /home/hari/Documents/site/dev/docx
       Destination: /home/hari/Documents/site/dev/docx/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
                    done in 0.317 seconds.
 Auto-regeneration: enabled for '/home/hari/Documents/site/dev/docx'
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
```
Now we can go to http://127.0.0.1:4000/ to have an overview of our blog.   
it is good to note that if you make changes to the `_config.yml` you must restart the process


Now that you are satisfied with the result you can build the site in production mode.

```bash
cd path/to/cloned/repo
JEKYLL_ENV=production bundle exec jekyll b
```

Output 
```bash
Configuration file: /home/hari/Documents/site/dev/docx/_config.yml
 Theme Config file: /var/lib/gems/3.0.0/gems/jekyll-theme-chirpy-5.2.0/_config.yml
            Source: /home/hari/Documents/site/dev/docx
       Destination: /home/hari/Documents/site/dev/docx/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
                    done in 0.407 seconds.
 Auto-regeneration: disabled. Use --watch to enable.

```
Jekyll has now built the site in the `_site` folder.   
Just copy the content of this folder and copy it to the appropriate folder on our web server so that the blog is online.

And Voila, you have your blog.


## **Hosting**
---
The next step is to host the site either on github or [locally](https://article-to-local), personally I will host it locally and on github for free as a backup so if locally the site is down the visitors will be directed on Github.

Since hosting on github is the easiest thing to do we will do it right away.      
The author has already done almost everything for us in the `.github` folder we can see that there is a `pages-deploy.yml` file this configuration file configures an ubuntu, installs the dependencies and 'compiles' our site in puroduction mode and all this in a totally automatic way.    
We just need to make a push on github and the magic happens.    
But before the magic happens we need to do some initial actions. 

### URL
First we have to change the name of the project to something like `<GHusername>.gihub.io` it is possible to give another name to your project but the project will be considered as a folder of the main page. so the url will look like this `<GHusername>.gihub.io/<repo name>` it's a matter of preference.     

For my part I prefer to have a 'folder' so I won't do this step and if you are like me you can go directly to the next step.

If you want to have a direct URL you have to change the name of your repo.    
You have to go to settings > General > Repository name and change the name to look like this: `<GHusername>.gihub.io` remember to click on the 'Rename' button.

![change the name of the repo](Rename-repo.png){: .normal}        
_change the name of the repo_

### Publishing branch 
Secondly we need to choose the source of the site, to choose this we go to settings > pages > Source and in the branches make sure you choose gh-pages you can save and everything is good.

![choose the publication branch](source.png){: .normal}       
_choose the publication branch_

> Here you will also have the Github URL of your blog.
{: .prompt-tip }

that's all we have to do now the secript will do everything for us.
Here you will also have the Github URL of your blog.

### git commands
Now you just have to sync the local changes with github.

> You can do a `JEKYLL_ENV=production bundle exec jekyll b` before doing the push so the production version of our blog will also be backed up on github.
{: .prompt-tip }

```bash
git add .
git commit -m '<a comment that describes this commit>'
git push
```
Once the push command is placed you will see in the action tab, Github-actions bot build your page. once it is finished, you will see the blog online.

Et voilà your blog is online.