---
title: Configure a personal domain name on github.
date: 2022-06-21 17:00
categories: [web site]
tags: [blog, git-hub, domain, custom, DNS, host]     # TAG names should always be lowercase
author: hari
img_path: /assets/img/post/custom-domain-gh
---
Git hub allows us to host a public project online and to have access with a github.io URL.     
It is possible not to use the domain name github.io and instead have a personal domain name.

For this you just need to have a domain name and that's it.

## Domain name
---
To have your own domain name you need to buy one from a hosting company like OVH, Go Daddy or ionos or any other hosting company.
The acquisition of a domain name is not very expensive.      
> You can even find free domain names if you are not too picky on the extension.
{: .prompt-tip }

I have domain names with OVH and Ionos which are two hosting companies that I can recommend but really all hosting companies are the same if it's just for the purchase of a domain name.

## GitHub hebergemet
---
With Git-hub you have two choices of hosting either repo in which case the project URL would look like this `<gh username.github.io/<repo name>`.    
or a single record that would be linked to your username.

In both cases you need a subdomain for each hosted page.

## DNS registration
---

I have the domain name `jeyakrishnan.fr` at OVH so it is with their interface that I show you the process but it should be almost the same for all the hosters just different visual.

You can configure a subdomain to point directly to a URL [Gitgub](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site) but it is strongly advised to configure the subdomain to the url of your project.

There are several types of records in the DNS zone but since we are going to redirect to another URL it is wise to use the `CNAME` field

here I create the subdomain **hari.jeyakrishnan.fr** for my documentation project.       

![Subdomain for the project](cname.png){: .normal}    
_Subdomain for the project_

It is also a good idea to create a subdomain **WWW** otherwise when users search for `www.<sub.domain.ext>` the search may not be successful.    

> I recommend you to point the WWW to **your** subdomain so when you want to change the destination of the subdomain you only have to do the moifiacation once.
{: prompt-tip}

![sub sub domain](cname-sub.png){: . normal}
World Wide Web sub domain for our subdomain._

> Changes in the DNS zone can take up to 48 hours to propagate around the world.
{: .prompt-info }

## github configuration
---
Now that we have our DNS record waiting to propagate everywhere we can finish the configuration on Github.

![URL configuration on github](gh-page.png){: .normal}
_configuration of the URL on github._

once you have configured github, you can go to the domain name you want to configure and it's done.