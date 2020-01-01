---
title: "Hugo vs Jekyll: A comparison based on personal usage"
date: 2020-01-01T10:29:28+05:30
categories:
- blog
- Random discovery
tags:
- hugo blog
- jekyll blog
keywords:
- tech
autoThumbnailImage : false
thumbnailImagePosition : "left"
thumbnailImage : img/thumbnail/blog5.jpg
coverImage: img/thumbnail/blog5.jpg
coverMeta: out
metaAlignment: center
---
Well, I am not writing this blog because I have used Hugo for making my website. It is just that I wanted    to compare the powers of Hugo and Jekyll. There is a whole list of static-site generators you can use and some of them are listed [here](https://www.creativebloq.com/features/10-best-static-site-generators). However, I am just comparing these 2 as they are widely used.

>NOTE: I too don't know why I chose Hugo over Jekyll for making this website.

### What is a static-site generator?

First of all, let us know what is a static-site generator. So, static site generators as the name suggest are simply website generators that take content, typically stored in flat files rather than databases, apply it against layouts or templates and generate a structure of purely static HTML files that are ready to be delivered.

To know more about the advantages and disadvantages of static-site generators, read [Davidwalsh's blog](https://davidwalsh.name/introduction-static-site-generators).


### What is Hugo?

Hugo is a static site generator written in Go. It is optimized for speed, easy use and configurability. Hugo takes a directory with content and templates and renders them into a full HTML website. Hugo makes use of markdown files with front matter for metadata.


### What is Jekyll?

Jekyll is a file-based content management system written in ruby. Jekyll takes your content, renders Markdown and Liquid templates, and spits out a complete, static website ready to be served by Apache, Nginx or another web server. Jekyll is the engine behind GitHub Pages, which you can use to host sites right from your GitHub repositories.

### 

#### 

| Hugo| Jekyll | 
| --- | --- |
| Go programming Language | Ruby programming language|
| lightning Fast | Not as fast as Hugo |
| Easy to set up | Easy to set up but not as easy as Hugo |
| Easy to deploy | Easy to deploy |
| No plugins/extensions for free themes | Highly customisable and high support of plugins |
| Open source | Open Source |
| No Github integration | Github integration|
| Supports TOML, YAML and JSON | Supports the only YAML for front matter|
| Fast builds| Slow builds|


So, these were some of the basic comparisons I made while using them in creating my static sites. There is still one more important comparison that is *Asset Pipeline* which I will try to cover in my upcoming blogs.