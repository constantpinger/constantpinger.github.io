---
layout: default
title: GH Pages v Wordpress 
nav_order: 1
---


# Creating a Blog on Github Pages v Wordpress

This is the first page written within [Github Pages](https://pages.github.com/) and falls around the 4 hour point in the journey to understanding the technology. Upon hearing about the concept I thought this would be a brilliant way to produce content about code I've written or tech battles I've won/lost. I love Github and really like having a personal treasure chest of all the work I've created in one place.

The reality has been similar to when you spill the ready meal onto your plate having slavoured over the delicious picture on the packaging for the 4 minues of microwaving. Not exactly what I was hoping for and far from what I had read in the how-to docs.

## What is Github Pages
You are reading text on a webpage but unlike most content it wasn't written on a traditional web platform such as wordpress or written in HTML. Github pages provides a neat way to create static web pages directly from user's repositories. By creating a repo named <username>.github.io you automatically have a very simple website.

In my experience having used wordpress, other CRM and (back in the day) creating content from HTML files, I wouldn't recommend GH pages for anyone wanting an easy way to blog or provide content online. The process to learn the tech is one more thing to learn which may well be interesting for the sake of learning it. But if your interest is in writing a type of code for a type of technology then this deviates from your main cause. Also the limits of GH Pages mean that creating a free Wordpress site is the better option for most in my opinion. Compare these two examples which are based on the same text:

https://constantpinger.home.blog/2021/01/06/raritan-px1-command-line/
https://constantpinger.github.io/DC/PDU/

The GH Pages version doesn't look as good but more importantly it would be difficult for me to proivde features like tags, links to similar pages, interaction with readers, auto notification of new posts....  These might be possible, but require coding or a similar level of knowledge where as in Wordpress these are available via the GUI. Clearly GH Pages is geared towards that love coding as the platform itself has that at its core. My point is that for those without infinite time results can be gained quicker from Wordpress.


Things I've learnt that aren't mentioned in the "really really easy guides to get you up and running"
1. It takes upto a minute from commiting a file to the update being available to a web browser. This is becaues there is a backend process to transform the markup text files into static webpages.
2. You have to learn a new coding technology (jekyll)
3. The themes that you can use via the GH pull down menus don't work unless the config file, file structure and page YAML header are perfect. GH Pages defaults to text output if you get it wrong
4. Some/all themes are linked to GH repos which could be removed at the wim of the owner leaving your GH Pages site broken


## Links
**Cayman Theme repo** [https://github.com/pages-themes/cayman/](https://github.com/pages-themes/cayman/)

**Great port of Read the Docs into GH Pages**[https://www.embeddedlog.com/jekyll-theme-rtd/](https://www.embeddedlog.com/jekyll-theme-rtd/)
