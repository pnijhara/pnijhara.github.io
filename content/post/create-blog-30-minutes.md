---
title: "Create your own blog in 30 minutes using Hugo, a static site generator written in Go"
date: 2019-08-06T17:18:26+05:30
categories:
- blog
- Random dicovery
tags:
- hugo blog
- create blog
- go programming language
keywords:
- tech
autoThumbnailImage : false
thumbnailImagePosition : "left"
thumbnailImage : img/thumbnail/hugo-blog.jpg
coverImage: img/cover/hugo.png
coverMeta: out
metaAlignment: center
---
Do you know you can create your blog without any knowledge of content management system or actual knowledge of creating a website, setting it, styling it or improving it? Well, you can with the world’s fastest framework for building websites

Before going forward it is
## Why Hugo?
* Hugo is the fastest tool of its kind. At <1 ms per page, the average site builds in less than a second.
Hugo supports unlimited content types, taxonomies, menus, dynamic API-driven content, and more, all without plugins.

* Hugo shortcodes allow for both beauty and flexibility.

* Hugo ships with pre-made templates to make quick work of SEO, commenting, analytics and other functions.  One line of code and you're done.

* Hugo provides full i18n support for multi-language sites with the same straightforward development experience Hugo users love in single-language sites.

* Hugo allows you to output your content in multiple formats, including JSON or AMP and makes it easy to create your own.

* Because there is no database, no plugins requiring any permissions, and no underlying platform running on your server, there's no added security concern.

* Version control is easy. Some CMS platforms use their own version control system (VCS) or integrate Git into their interface. With Hugo, all your source files can live natively on the VCS of your choice.

## Install Hugo

##### Mac OS

>`$ brew install hugo`

##### Windows

> `$ choco install hugo -confirm`

##### Linux
> `$ snap install hugo`

There are many other ways of installing from GitHub repository, you can check them [here](https://gohugo.io/getting-started/installing/)

## Create a new site

Create a new site that will become your blog

> `$ hugo new site awesome-blog`

Change into the newly created directory

>``$ cd awesome-blog``